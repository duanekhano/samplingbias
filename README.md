# samplingbias

**评估线上采样是否扭曲了整体指标。**

`samplingbias` —— 比较采样规则与真实流量分布，算出各分段的指标偏移

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`samplingbias.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install duanekhano-samplingbias
```

装完直接用命令名调用：

```bash
samplingbias --help
```

也可以不用安装，直接把 `samplingbias.py` 拷走用——它只依赖标准库。

## 为什么需要它

被采到和没被采到的样本差别有多大，工具给量化结果

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 观测采样偏差 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python samplingbias.py --file input.txt
python samplingbias.py --text "示例内容"
python samplingbias.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 比例的分母取自你给的口径，不替你选口径。
- 不判断比例高低是否合理。

## 跑测试

```bash
python test_samplingbias.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/duanekhano/samplingbias>

---

## 关于作者

duanekhano 做观测采样偏差相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://duanekhano.github.io>
- 仓库：<https://github.com/duanekhano/samplingbias>

## 许可

MIT，见 [LICENSE](LICENSE)。
