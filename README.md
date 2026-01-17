# Dataset Description

This project uses the **Electricity Transformer Temperature Dataset**, which contains multivariate time-series measurements collected from a power transformer.

---

## Fields

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
