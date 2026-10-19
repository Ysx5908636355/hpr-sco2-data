# Data dictionary

Every CSV in `data/` has the same 28 columns and 1 s sampling (except the load-step sequence, which is resampled). Column names are the Modelica variable names written by Dymola; the symbols below are the ones used in the paper.

`data/表头对应.csv` holds the original three-row mapping (Modelica name / Chinese name / symbol).

## Columns

| # | Column | Symbol | Quantity | Unit |
|---|---|---|---|---|
| 1 | `Time` | t | simulation time | s |
| 2 | `T_water_in.fluidState.T` | T<sub>water,in</sub> | cooling-water inlet temperature | K |
| 3 | `T_water_out.fluidState.T` | T<sub>water,out</sub> | cooling-water outlet temperature | K |
| 4 | `Pipe1.state.T` | T1 | compressor inlet temperature | K |
| 5 | `Pipe1.state.p` | p1 | compressor inlet pressure | Pa |
| 6 | `Pipe2.state.T` | T2 | compressor outlet temperature | K |
| 7 | `Pipe2.state.p` | p2 | compressor outlet pressure | Pa |
| 8 | `Pipe3.state.T` | T3 | HPHX inlet temperature (recuperator cold-side outlet) | K |
| 9 | `Pipe3.state.p` | p3 | HPHX inlet pressure | Pa |
| 10 | `Pipe4.state.T` | T4 | HPHX outlet temperature (turbine inlet) | K |
| 11 | `Pipe4.state.p` | p4 | HPHX outlet pressure (turbine inlet) | Pa |
| 12 | `Pipe4.inlet.m_flow` | ṁ | cycle mass flow rate | kg/s |
| 13 | `Pipe5.state.T` | T5 | turbine outlet temperature | K |
| 14 | `Pipe5.state.p` | p5 | turbine outlet pressure | Pa |
| 15 | `Pipe6.state.T` | T6 | cooler inlet temperature (recuperator hot-side outlet) | K |
| 16 | `Pipe6.state.p` | p6 | cooler inlet pressure | Pa |
| 17 | `heatPipeReactor.nr` | n<sub>r</sub> | relative nuclear power | – |
| 18 | `heatPipeReactor.T[1, 1]` | T<sub>f</sub> | fuel average temperature | K |
| 19 | `heatPipeReactor.T[2, 1]` | T<sub>m</sub> | monolith average temperature | K |
| 20 | `heatPipeReactor.T[3, 1]` | T<sub>hp,1</sub> | heat-pipe evaporator average temperature | K |
| 21 | `heatPipeReactor.T[4, 1]` | T<sub>hp,2</sub> | heat-pipe adiabatic-section average temperature | K |
| 22 | `heatPipeReactor.T[5, 1]` | T<sub>hp,3</sub> | heat-pipe condenser average temperature | K |
| 23 | `compressor.eta` | η<sub>c</sub> | compressor isentropic efficiency | – |
| 24 | `compressor.Wc` | P<sub>c</sub> | compressor power (negative: work consumed) | W |
| 25 | `turbine.eta` | η<sub>t</sub> | turbine isentropic efficiency | – |
| 26 | `turbine.Wt` | P<sub>t</sub> | turbine power | W |
| 27 | `shaft_TAC.w` | N | shaft rotational speed | rad/s |
| 28 | `shaft_TAC.Power_out` | P<sub>out</sub> | net shaft output power | W |

## Notes

- Shaft speed is stored in rad/s. To compare with the 28 770.4 r/min design value quoted in the paper, use N × 60 / (2π).
- The load-step sequence file (`无控制_-10%FP然后+10%FP_精简.csv`) spans 0–76 000 s with 484 samples and is resampled rather than 1 s spaced: the interval varies between 10 s and 160 s, and five timestamps repeat (1 000, 16 000, 16 010, 21 000 and 76 000 s), so the 484 rows hold 479 distinct times. The other four files are 1 s spaced.
- Station numbering follows the direction of flow: compressor inlet (1) → compressor outlet (2) → HPHX inlet, after the cold side of the recuperator (3) → HPHX outlet, i.e. turbine inlet (4) → turbine outlet (5) → cooler inlet, after the hot side of the recuperator (6).
