# structure

在应用系统开发和维护中，经常会有配置数据或客户数据需要在不同的序列化结构中相互转换的需求。不同编程语言之前，对数据结构的偏好也不一样，比如 JavaScript 一般使用 JSON、Java 一般使用 XML、Ruby 一般使用 YAML、Golang 一般使用 TOML 等等。

一旦陈年老系统某天开始重构，通常就会有大批的存量数据需要转换。我们以纳斯达克大数据领域上市公司第一股 Splunk 的仪表盘配置数据为例，该软件从 v7 升级到 v8 版本时，重构了自己的仪表盘设计，配置数据结构从 XML 改为了 JSON。我们可以用 ChatGPT 来做第一步的简单转换。下例内容来自官方手册的 basic 示例：

> 将下面这段 XML 数据转换为 JSON 格式：
> <dashboard version="1.1">
>   <!-- A title for the dashboard -->
>   <label>Basic Dashboard</label>
>   
>   <!-- Provide a description -->
>   <description>Illustrate the basic structures of a dashboard</description>
> 
>   <!-- Place panels within rows -->
>   <row>
> 
>     <!-- This basic dashboard has only a single panel -->
>     <panel>
>     
>       <table>
>         <title>Top Sourcetypes (Last 24 hours)</title>
> 
>         <!-- A search powers the panel -->
>         <search>
>           <query>
>           index=_internal | top limit=100 sourcetype | eval percent = round(percent,2)
>           </query>
>           <!-- Specify a time range for the search -->
>           <earliest>-24h@h</earliest>
>           <latest>now</latest>
>         </search>
> 
>         <!-- Use options to further define how to display result data -->
>         <option name="wrap">true</option>
>         <option name="rowNumbers">true</option>
>       </table>
>     </panel>
>   </row>
> 
> </dashboard>

![](/images/awesome/structure.png)

ChatGPT 成功的输出了对应内容的 JSON 格式数据。不过是否真的合法呢？我们打开 JSONLint 工具，把 ChatGPT 输出的内容复制粘贴到 JSONLint 工具的文本输入框内，点击验证，看到工具返回验证成功。ChatGPT 成功完成了数据结构转换任务。

![](/images/awesome/structure-jsonlint.png)

