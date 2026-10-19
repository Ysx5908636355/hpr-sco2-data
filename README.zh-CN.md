# 热管反应堆耦合超临界 CO₂ 布雷顿循环瞬态仿真数据集

*[English](README.md)*

本仓库是下列论文的开放数据：

> **Dynamic Modeling and Transient Response Mechanisms of a Heat Pipe Reactor Coupled with a Supercritical CO₂ Brayton Cycle**  
> （热管反应堆耦合超临界 CO₂ 布雷顿循环的动态建模与瞬态响应机理）  
> *Energy Sources, Part A: Recovery, Utilization, and Environmental Effects*

数据覆盖热管反应堆驱动超临界 CO₂ 布雷顿循环的三类扰动：电负荷、堆芯反应性、冷却水流量。全部工况均为开环（无自动控制投入），记录到的是机组自身的瞬态响应。

## 目录结构

| 路径                        | 内容                         |
| ------------------------- | -------------------------- |
| `data/`                   | 5 个 CSV 时序文件，每个工况一个，另附列名字典 |
| `docs/data_dictionary.md` | 逐列说明，含符号与单位                |

## 数据文件

| 文件                          | 扰动                        | 时长         | 样本数      |
| --------------------------- | ------------------------- | ---------- | -------- |
| `无控制_-10%FP然后+10%FP_精简.csv` | 负荷先降 10% FP 再升 10% FP     | 0–76 000 s | 484（重采样） |
| `无控制_+10pcm_精简.csv`         | 反应性阶跃 +10 pcm             | 0–16 000 s | 16 003   |
| `无控制_-10pcm_精简.csv`         | 反应性阶跃 −10 pcm             | 0–16 000 s | 16 003   |
| `无控制_+10%冷却水流量_精简.csv`      | 冷却水流量阶跃 +10%              | 0–21 000 s | 21 005   |
| `无控制_-10%冷却水流量_精简.csv`      | 冷却水流量阶跃 −10%              | 0–21 000 s | 21 005   |
| `表头对应.csv`                  | 列名字典（Modelica 变量名、中文名、符号） | —          | 3        |

文件名沿用仿真环境导出的中文原名，各字段含义如下：

- `无控制`：闭环控制未投入
- `FP`：满功率（full power）
- `pcm`：十万分之一，反应性单位
- `冷却水流量`：冷却水体积流量
- `精简`：精简输出集，仅保留论文用到的 28 个通道
- `然后`：前后两段先后施加

## 变量说明

每个文件 28 列：回路六个站位的工质温度与压力、循环流量、相对核功率、五个堆芯与热管温度、压气机与透平的等熵效率和功率、转速、净输出功率。符号与单位见 [`docs/data_dictionary.md`](docs/data_dictionary.md)。

以下两点约定需要注意：

- 压力为绝对压力，单位 Pa；温度单位 K；
- `compressor.Wc` 为负值（表示耗功），`turbine.Wt` 与 `shaft_TAC.Power_out` 为正值。

## 未包含的内容

后处理与绘图脚本不在本仓库内。各 CSV 是精简后的输出集，每个工况 28 个通道，与论文图件所用数据一致；任意一列都可用通用工具读取（pandas、MATLAB、Excel）。

机理模型在 Modelica/Dymola 环境下基于 ThermoPower 库搭建，流体物性取自 CoolProp。模型文件未随本仓库分发：一方面依赖第三方库，另一方面可向通讯作者索取。

## 许可

本仓库的数据与文档采用知识共享署名 4.0 国际许可协议（CC BY 4.0），全文见 `LICENSE`。

## 引用

使用本数据时，请引用上述论文与本仓库：

```bibtex
@dataset{yin2026hprsco2,
  title  = {Transient simulation dataset for a heat pipe reactor coupled with a supercritical CO2 Brayton cycle},
  author = {Yin, Shaoxuan and Yu, Ren and Ma, Jie and Mao, Wei and Sheng, Dongjie},
  year   = {2026},
  note   = {GitHub repository}
}
```

## 联系方式

海军工程大学，武汉 430000

- 第一作者：殷少轩（Shaoxuan Yin），M21182702@nue.edu.cn
- 通讯作者：马杰（Jie Ma），1508051046@nue.edu.cn
