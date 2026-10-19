# HPR–sCO₂ Transient Simulation Dataset

*[中文版](README.zh-CN.md)*

Open-loop transient simulation data for the study

> **Dynamic Modeling and Transient Response Mechanisms of a Heat Pipe Reactor Coupled with a Supercritical CO₂ Brayton Cycle**
> *Energy Sources, Part A: Recovery, Utilization, and Environmental Effects*

The dataset covers three disturbance types applied to a heat-pipe-reactor-driven supercritical CO₂ Brayton cycle: electrical load, core reactivity, and cooling-water flow. All cases are open loop (no automatic control acting), so the recorded transients are the inherent response of the plant.

## Contents

| Path | Description |
|---|---|
| `data/` | Five CSV time series, one per case, plus the column dictionary |
| `docs/data_dictionary.md` | Column-by-column description, symbols and units |

## Data files

| File | Disturbance | Duration | Samples |
|---|---|---|---|
| `无控制_-10%FP然后+10%FP_精简.csv` | Load −10 % FP, then +10 % FP | 0–76 000 s | 484 (resampled) |
| `无控制_+10pcm_精简.csv` | Reactivity step, +10 pcm | 0–16 000 s | 16 003 |
| `无控制_-10pcm_精简.csv` | Reactivity step, −10 pcm | 0–16 000 s | 16 003 |
| `无控制_+10%冷却水流量_精简.csv` | Cooling-water flow step, +10 % | 0–21 000 s | 21 005 |
| `无控制_-10%冷却水流量_精简.csv` | Cooling-water flow step, −10 % | 0–21 000 s | 21 005 |
| `表头对应.csv` | Column dictionary (Modelica name, Chinese name, symbol) | — | 3 |

File names are kept in the original Chinese, as exported from the simulation environment:

- `无控制` = no control
- `FP` = full power
- `pcm` = per cent mille (reactivity)
- `冷却水流量` = cooling-water flow
- `精简` = reduced output set (the 28 channels used in the paper)
- `然后` = followed by

## Variables

Twenty-eight channels per file: working-fluid temperatures and pressures at six stations around the loop, mass flow, relative nuclear power, five core and heat-pipe temperatures, compressor and turbine efficiency and power, shaft speed and net output power. Units and symbols are listed in [`docs/data_dictionary.md`](docs/data_dictionary.md).

Two conventions worth noting:

- pressures are absolute, in Pa; temperatures in K;
- `compressor.Wc` is negative (work consumed), `turbine.Wt` and `shaft_TAC.Power_out` are positive.

## What is not included

Post-processing and plotting scripts are not part of this repository. The CSVs are the reduced output set, 28 channels per case, as used for the figures of the paper; any column can be read with standard tools (pandas, MATLAB, Excel).

The plant model was built in Modelica/Dymola on top of the ThermoPower library, with fluid properties from CoolProp. The model files are not redistributed here: they depend on third-party libraries and are available from the corresponding author on reasonable request.

## License

The data and documentation in this repository are released under the Creative Commons Attribution 4.0 International licence (CC BY 4.0). See `LICENSE`.

## Citation

If you use these data, please cite the paper above and this repository:

```bibtex
@dataset{yin2026hprsco2,
  title  = {Transient simulation dataset for a heat pipe reactor coupled with a supercritical CO2 Brayton cycle},
  author = {Yin, Shaoxuan and Yu, Ren and Ma, Jie and Mao, Wei and Sheng, Dongjie},
  year   = {2026},
  note   = {GitHub repository}
}
```

## Contact

Naval University of Engineering, Wuhan 430000, China

- Shaoxuan Yin (first author) — M21182702@nue.edu.cn
- Jie Ma (corresponding author) — 1508051046@nue.edu.cn
