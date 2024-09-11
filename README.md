# 爬取谷歌学术论文信息的简单工具-分为保留原html和保留链接两种

# todo
```
遗憾的是，学校做了DNS投毒，即使我挂了代理，也会出现谷歌学术无法访问的情况，所以实例数据不够完美
```

# 环境-ubuntu
```
python 3.10.12
```
```
chromedriver --version
ChromeDriver 128.0.6613.119 (6e439cfca4deda5954b0c74cde9b521c03cb31ad-refs/branch-heads/6613@{#1464})
```
```
Chrome version is same with ChromeDriver
```

# 用法
```
python3 xxx.py -q "输入要搜索的主题"
```

# 原理
```
通过selenium配合chrome driver完成对谷歌搜索的模拟，反制反爬机制
```
```
通过分解url分离出搜索条件和页码，每个页10个数据
```
```
通过CSS选取到特定的元素，包括论文列表、论文连接、论文简介、论文标题
```
```
跳转到url里读取需要的内容，这里需要自行修改，代码只直接获取整个html
```
```
将数据喂给大模型，让大模型总结摘要
```

# example data
|  Page   | Result  |  Title   | Link  | Abstract  |
|  ----  | ----  | ----  | ----  | ----  |
| 1  | 1 | Toward efficient and privacy-preserving computing in big data era  | https://ieeexplore.ieee.org/abstract/document/6863131/ | "… privacy-preserving techniques to check whether or not they are suitable for privacy-preserving … also present an efficient and privacy-preserving cosine similarity computing protocol as an …" |
| 1  | 2 | Exploring design and governance challenges in the development of privacy-preserving computation  | https://dl.acm.org/doi/abs/10.1145/3411764.3445677 | "… multi-party computation, and differential privacy are part of an emerging class of Privacy Enhancing … , and responsible governance of these privacy-preserving computation techniques. …" |
