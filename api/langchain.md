# langchain

LangChain 是一个基于大型语言模型（LLMs）的框架，它可以帮助你快速地开发和部署各种基于文本的应用。比如，你可以用它来制作一个聊天机器人，或者一个能够自动生成问题和答案的系统，或者一个能够对文章进行摘要的工具等等。

LangChain 的核心思想是，你可以把不同的组件“链接”起来，形成一个链。每个组件都有自己的功能，比如调用一个LLM、处理文本、存储数据等。通过链接不同的组件，你可以实现更复杂和更灵活的功能。在目前的 LLM 社区，langchain 已经是最流行的开发框架，多数应用都使用它作为开发基础。


接下来我们利用 LangChain 实现一个简单的问答机器人，这个机器人可以根据我准备的语料回答相关问题。

不过动手之前，我们要先了解一下语料训练用到的一个核心技术--Embeddings。这种技术可以将原始数据表示为向量空间中的点，这样相似的数据点就可以在向量空间中靠近，而不相似的点则远离，从而更容易进行计算和比较，因此 Embeddings 向量通常具有许多有用的性质，例如可以使用它们进行词汇语义相似性计算、词性分类、情感分析等。我们要实现的问答机器人，就会用到向量相关性计算，是Embeddings 技术的一种经典应用场景。

接下来我们正式开始，首先我们先找两篇文章作为语料，一篇是介绍最新评选的2022年北京十大旅游景点的文章，一篇是介绍GPT-4发布的文章，我们将这两篇文章文字内容保存成txt文件。

    北京市十大旅游景点.txt
    GPT-4发布.txt

首先安装需要使用的库文件。除了 langchain，我们还需要一个中文分词工具，一个向量数据库，这里我们选择jieba作为中文分词工具，chromadb 作为我们的向量数据库。

```
pip install langchain
pip install chromadb
pip install jieba
pip install unstructured
pip install tiktoken
pip install openai
```

然后我们创建chat.py文件，在文件开头导入要用到的库和方法：

``` python
# -*- coding: utf-8 -*-

import os
import sys
import jieba
from langchain.llms import OpenAI
from langchain.vectorstores import Chroma
from langchain.chains import ChatVectorDBChain
from langchain.text_splitter import TokenTextSplitter
from langchain.document_loaders import DirectoryLoader
from langchain.embeddings.openai import OpenAIEmbeddings

```

在自然语言处理中，分词是一项重要的预处理任务，将文本数据切分成语义单元，便于进行进一步处理。因此我们先将之前保存的两个txt文件内容进行中文分词，并将进行过切词操作的内容保存到新文件中。假设我们的两篇语料保存在 corpus 文件夹下，切词后的文件保存在 segments 文件夹下。

``` python
def generate_segments():
    """将语料切词并将结果保存在文件中"""
    corpus_files=["北京市十大旅游景点.txt","GPT-4发布.txt"]
    
    for file_name in corpus_files:
        # 读取作为语料的文件
        one_file = os.path.join("./corpus", file_name)
        with open(one_file, "r", encoding='utf-8') as f:  
            origin_data = f.read()
        
        # 分词，用空格将单词连接起来
        segments_data = " ".join([word for word in list(jieba.cut(origin_data))])
        
        # 创建保存分词后文件的目录
        segments_dir = "./segments"
        os.makedirs(segments_dir, exist_ok=True)

        # 保存分词内容到文件中
        segments_file = os.path.join(segments_dir, file_name)
        with open(segments_file, "w") as f:   
            f.write(segments_data)
```

在进行分词后，我们需要对数据进行切块处理，将文本数据按照一定的大小进行切割，以便于后续处理。所以接下来我们加载分词后的文件，并进行切块处理。

``` python

def load_documents():
    """加载分词后文档"""
    loader = DirectoryLoader("./segments", glob="**/*.txt")
    return loader.load()

def split_documents(segments):
    """将文档切块"""
    splitter = TokenTextSplitter(chunk_size=1000, chunk_overlap=0)
    return splitter.split_documents(segments)
```

向量化处理是我们实现问答机器人的核心，我们把切块处理以后的数据使用 Openai 的 Embeddings 方法进行向量化处理。

``` python
def embed_documents(splitted_segments):
    """调用 OpenAI 的 Embeddings 方法进行向量化，注意这里需要设置OPENAI_API_KEY的环境变量，因为Chroma也要用到"""
    os.environ["OPENAI_API_KEY"] = "替换为OpenAI API Key"
    embeddings = OpenAIEmbeddings(openai_api_key=os.environ["OPENAI_API_KEY"])
    vectordb = Chroma.from_documents(
        splitted_segments, embeddings, persist_directory="./segments"
    )
    vectordb.persist()
    return vectordb
```

有了向量数据，我们就可以创建问答Chain了，这个 Chain 是一个由多个模型和处理步骤组成的自然语言处理管道，它可以将用户输入的问题进行解析和分析，然后生成相应的答案。在创建问答Chain时，我们可以根据具体的需求选择合适的语言训练模型。OpenAI的GPT-3.5-turbo模型是一种基于Transformer结构的大型预训练语言模型，具有非常强的自然语言生成和理解能力，可以用于各种自然语言处理任务，如文本生成、翻译、对话系统等。通过加载这个模型，我们可以使问答系统更加智能和灵活，为用户提供更加准确和全面的答案。

``` python
def generate_chain(vectordb):
    """创建问答Chain了"""
    chain = ChatVectorDBChain.from_llm(OpenAI(temperature=0, 
    model_name="gpt-3.5-turbo"), vectordb, return_source_documents=True)
    return chain

```

万事俱备，接下来就可以向机器人提问了。这里需要注意，如果我们把每次聊天的答案记录下来，在提问的时候传回 chain 方法中，那机器人就会结合上下文进行推断，如果我们每次传空，则机器人只会根据当前问题进行回答。

``` python
if __name__ == "__main__":
    generate_segments()
    segments = load_documents()
    splitted_segments = split_documents(segments)
    vectordb = embed_documents(splitted_segments)
    chain = generate_chain(vectordb)

    # 获取问题
    question = sys.argv[0]
    answer_object = chain({"question": question, "chat_history": []});
    print("问题的答案是：",answer_object["answer"]) 

```

我们运行上面的代码，传入想问的问题，就能看到整个处理语料、生成向量的过程的一些提示信息以及最终答案了：

``` bash
~/repos/Langchain Langchain ❯ python chat.py "北京猿人遗址的地址"

Building prefix dict from the default dictionary ...
Loading model from cache /var/folders/tv/qzxmbrgs45v2htt9srd4pl3c0000gn/T/jieba.cache
Loading model cost 0.275 seconds.
Prefix dict has been built successfully.
Running Chroma using direct local API.
loaded in 75 embeddings
loaded in 1 collections
Persisting DB to disk, putting it in the save folder ./segments
问题的答案是： 北京城西南房山区周口店龙骨山脚下。
PersistentDuckDB del, about to run persist
Persisting DB to disk, putting it in the save folder ./segments

```

这样，我们通过 Lang Chain，利用Embeddings技术以及OpenAI的GPT-3.5-turbo模型制作完成了一个简单的问答机器人。我们也可以通过引入更加先进的自然语言处理技术来进一步提高问答机器人的性能和效率，如使用预训练模型进行语义匹配、采用知识图谱进行答案生成等。通过不断地优化和改进，我们可以开发出更加智能和高效的问答机器人，为用户提供更加便捷和高效的服务。

