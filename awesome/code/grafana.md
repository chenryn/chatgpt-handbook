# grafana

Grafana是开源社区最流行的数据可视化软件，一定程度上也和 superset 一起被视为 tableau 等商业 BI 的开源替代品，很多IT 团队、科研团队，都会使用 Grafana 来做数据监控、挖掘分析。Grafana社区也有很多贡献者，在 github 上分享自己针对不同场景制作的数据分析仪表盘效果和配置。

作为 grafana 新手，或者作为某个数据分析场景的新手，我们除了按部就班学习行业知识、数据分析知识、grafana 知识以外，也可以直接像 ChatGPT 求援。Grafana支持通过 JSON 字符串的方式，直接定义整个仪表盘的所有细节参数。因此，我们可以尝试让 ChatGPT 直接针对特定场景给出最终的 JSON 配置，直接贴进 grafana 即可。下面我们试试对数据中心基础设施主机层监控做一次咨询，看看 ChatGPT 是否可以同时给出主机层应该监控哪些指标，采用什么统计分析方法，做什么类型的可视化，以及最后生成对应的 JSON 配置：

> I need help creating a datacenter health score monitor dashboard with multiple charts. design the dashboard with grafana, give me the grafana dashboard.json

![](/images/awesome/grafana-chat.png)

结果很有趣，ChatGPT 严正申明自己只是一个语言模型，又不知道我们实际环境情况，大段的免责说完以后，其实还是给出了JSON 配置。内容较长，为了阅读方便，我们直接提供成文本：

```
{
  "title": "Datacenter Health Score Monitor",
  "panels": [
    {
      "title": "Server Uptime",
      "type": "graph",
      "targets": [
        {
          "expr": "avg(server_uptime_seconds) by (server)",
          "refId": "A"
        }
      ],
      "legend": {
        "show": true
      }
    },
    {
      "title": "CPU Utilization",
      "type": "gauge",
      "targets": [
        {
          "expr": "sum(cpu_utilization_percent) by (server)",
          "refId": "B"
        }
      ],
      "maxValue": 100,
      "valueName": "current",
      "thresholds": "70, 90",
      "format": "percent"
    },
    {
      "title": "Network Latency",
      "type": "singlestat",
      "targets": [
        {
          "expr": "avg(network_latency_ms) by (server)",
          "refId": "C"
        }
      ],
      "valueName": "current",
      "format": "ms"
    }
  ],
  "id": null,
  "timezone": "browser",
  "editable": true,
  "hideControls": false,
  "sharedCrosshair": false,
  "rows": [],
  "schemaVersion": 21,
  "version": 0,
  "links": []
}
```

我们可以看到，ChatGPT 给我们推荐了三个监控指标，都遵守 openMetric 规范，以下划线 `_` 而非英文点 `.` 风格命名，分别是主机启动时长、CPU 使用率、平均网络延时。时长以趋势图展示，延时以单值展示，CPU 使用率用车速表展示，并设定 70% 和 90% 两档告警阈值。还不错！现在让我们实际验证一下输出的正确性吧。打开一个 grafana 产品界面，点击 create dashboard，切换到 setting 中的 JSON mode，把 ChatGPT 输出的 JSON 完整的复制粘贴进去。

![](/images/awesome/grafana-json.png)

点击保存后，返回查看这个被 ChatGPT 取名为"Datacenter Health Score Monitor"的仪表盘，可以正确看到结果。接下来，就是实际数据导入，查看分析成果了：

![](/images/awesome/grafana-ret.png)

注意，本书作为 ChatGPT 技术介绍，不展开介绍 grafana 软件的安装部署和使用细节。但本节场景其实对 superset 等其他 BI 产品都成立，大家可以选择自己熟悉的工具任意尝试。

