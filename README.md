# Dataset Description

1. ETD: Here we use the **Electricity Transformer Temperature Dataset**, which contains multivariate time-series measurements collected from a power transformer.
2. DGA: Dissolved Gas Analysis

---

## Fields for ETD Dataset

| Field | Description |
|------|------------|
| `date` | Timestamp of the recorded measurement |
| `HUFL` | High Useful Load |
| `HULL` | High Useless Load |
| `MUFL` | Middle Useful Load |
| `MULL` | Middle Useless Load |
| `LUFL` | Low Useful Load |
| `LULL` | Low Useless Load |
| `OT` | Oil Temperature (target variable) |

---

## Useful vs Useless Load (Physical Meaning)

- **Useful load (active power)**:  
  Current is largely **in phase with voltage**, meaning current peaks when voltage
  peaks. Electrical energy is transferred to the load and converted into real work.

- **Useless load (reactive power)**:  
  Current is **out of phase with voltage** due to inductive or capacitive elements.
  Energy oscillates between the source and the magnetic/electric fields instead of
  performing net work.

Although reactive power does not produce useful output, it still increases the
**current magnitude** flowing through the transformer.

---

## Relation to Oil Temperature

Transformer heating depends on current, not on whether power is useful:
\[
\text{Copper loss} \propto I^2 R
\]

Out-of-phase (reactive) current still flows through resistive windings and produces
heat, raising the oil temperature. Higher-level loads (HUFL, HULL) have the strongest
impact, while lower-level loads contribute to baseline heating.

---

## Data Source

The dataset is provided by the authors of the **Informer** model and is publicly available at: https://github.com/zhouhaoyi/ETDataset

---

## Understanding DGA

There is no direct and infallible method using DGA to obtain an exact evaluation of a transformer’s condition. There are several reasons why the DGA status can be very different from the transformer’s true
condition, some of which are as follows:

a) There are several possible causes of the presence of gas in a transformer. Some of those are related
to fault conditions (e.g., arcing, overheating, PD), others are related to more benign conditions
(e.g., stray gassing, contamination, previous fault now inactive, and mild core overheating.

b) Some pre-failure conditions simply do not generate gas. (e.g., mechanical or insulating system
weakness).

c) Some normal conditions do generate gases. (e.g., normal aging, and insulating liquid oxidation).

d) The DGA data used to develop this procedure and norms came from in-service transformers for
which their condition information (faulty or not) at the time of the DGA was unavailable.
Therefore, there was no possibility to directly correlate one with the other, only to evaluate the
DGA results distribution assuming most of the data came from healthy transformers.

- It is generally recognized by the industry experts that increasing gas levels are more of a concern than the levels themselves. Therefore, it is important to have some guidelines on acceptable gas generation rates.

- It is also recognized that all faults are not of the same concern, so the type of fault should also be considered, not just the gas levels or the gas evolution.

---

## Citation

If you use this dataset, please cite the following work:

```bibtex
@inproceedings{haoyietal-informer-2021,
  author    = {Haoyi Zhou and
               Shanghang Zhang and
               Jieqi Peng and
               Shuai Zhang and
               Jianxin Li and
               Hui Xiong and
               Wancai Zhang},
  title     = {Informer: Beyond Efficient Transformer for Long Sequence Time-Series Forecasting},
  booktitle = {The Thirty-Fifth {AAAI} Conference on Artificial Intelligence, {AAAI} 2021, Virtual Conference},
  volume    = {35},
  number    = {12},
  pages     = {11106--11115},
  publisher = {{AAAI} Press},
  year      = {2021},
}
