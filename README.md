# 教学算力账单的尾部风险与可加分摊

本项目保存高校公共算力与教学研究的虚构汇总资料和Python读取工具。现有工具仅解析输入并显示类型与记录数，不执行统计计算、优化、拟合或训练。样本不代表真实高校、个人或教学成效。

## 资料口径

每个联合情景含概率、课程金额向量和提议概率；返还金额可以为负，总费用始终由同情景贡献求和。p和q用显式分子分母，避免二进制误差。

fixtures为只读资料目录，src/risk_reader.py为现有读取器，material-index.json记录文件内容摘要。研究结果可以放入独立.workspace-output目录，不要覆盖原始数据。

## 运行与开发

Python 3.11及以上版本；现有读取器只用标准库，无安装步骤。进入项目根目录：

    python -m src.risk_reader fixtures/scenarios.json

编译检查：

    python -m compileall -q src tests

输入契约测试：

    python -m unittest discover -s tests -v

## 容器环境

    docker build -t compute-tail-risk:local .
    docker run --rm compute-tail-risk:local

镜像按完整摘要固定，默认执行读取测试。容器不需要访问外部教学平台。
