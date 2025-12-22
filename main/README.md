# Dataset Description

This project uses the **ETDataset (Electricity Transformer Dataset)**, which contains multivariate time-series measurements collected from a power transformer.

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

## Data Source

The dataset is provided by the authors of the **Informer** model and is publicly available at:  
https://github.com/zhouhaoyi/ETDataset

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
