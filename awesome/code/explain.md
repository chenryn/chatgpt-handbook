= explain
TODO

== 给读者解释代码

explain this python code:
from deepsparse import Pipeline
qa_pipeline = Pipeline.create(task="question-answering")
inference = qa_pipeline(question="What's my name?", context="My name is Snorlax")
>> {'score': 0.9947717785835266, 'start': 11, 'end': 18, 'answer': 'Snorlax'}

== 生成接口说明文档

write a docstring description for this function:
import requests
def make_get_request(url):
    response = requests.get(url)
    return response.status_code, response.text
make_get_request('https://www.example.com')

