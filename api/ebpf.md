= ebpf

eBPF 是 Linux 内核在近几年最大的突破性创新技术，在网络数据处理、内核态和用户态函数调试、性能监控等领域发挥了重要作用。但作为一个新技术，eBPF 的学习成本较高，即使是方便普通用户上手的 bpftrace 命令，在有着和 awk 命令相似的外观同时，也依然有各种新数据结构、新语法和新限制要学习。

[GPTtrace](https://github.com/eunomia-bpf/GPTtrace)项目，就利用了 ChatGPT 的能力，来辅助用户上手 bpftrace 工具的使用。

和其他基于 GPT3 接口的项目不同，该项目完整利用了 ChatGPT 的交互形式，因此， GPTtrace 的训练过程，其实就是 prompt 对话内容，详见 `train/` 目录中的若干文档。因此，即使完全不懂编程的人(这可能是句废话，都用上 `bpftrace` 这种高级调试技巧的人怎么可能不懂编程)，也可以直接从 train 目录里复制出来对话语句，贴进 ChatGPT 界面上，复原整个过程。

