# FIT5196 A1 — Group050

小组共享仓库，保存当前 `Group050_A1_submission/` 文件夹的同步副本。
本次同步保留已有内容，不重新清洗数据或改写 notebook 结果。

## 文件说明

| 路径（位于 `Group050_A1_submission/`） | 内容 |
|---|---|
| `Group050_solution.ipynb` | 数据处理、文本函数调用与 validation register |
| `Group050_EDA.ipynb` | EDA 图表、findings 和未来 ML questions |
| `Group050_text_functions.py` | 当前整合的共享文本函数 |
| `Group050_source_to_target_mapping.csv` | Source-to-target mapping |
| `outputs/` | 六张标准化 CSV |
| `Group050_EDA_context_assurance_limitations_conclusion.md` | 报告相关段落 |
| `group_member_solution/` | 组员贡献版本，供对照与协作 |

组员贡献版本不是另一套最终入口。需要更新整合版本时，请先检查差异，避免覆盖其他成员的修改。

## 运行说明

在 `Group050_A1_submission/` 目录中启动 Jupyter，并使用包含 pandas、NumPy、Matplotlib 和 Jupyter 相关组件的 Python 环境。具体环境记录见 notebook。

- `Group050_EDA.ipynb` 读取已有 `outputs/` 中的六张 CSV。
- 从原始数据重跑 `Group050_solution.ipynb`，还需要分配给本组的原始资料包。本次仅同步 submission，因此原始 JSON/XML 和配套字典、模板、公开测试文件未上传。

重跑 solution 时，可在仓库根目录下自行放置分配包，形成以下结构；也可将这些文件放在 solution notebook 旁边：

```text
5196/
├── Group050_A1/
│   ├── raw_input/
│   │   ├── Group050_commerce.json
│   │   └── Group050_operations.xml
│   ├── public_data_dictionary.csv
│   ├── A1_source_to_target_mapping_template.csv
│   └── A1_public_text_test_cases.csv
└── Group050_A1_submission/
    ├── Group050_solution.ipynb
    ├── Group050_EDA.ipynb
    ├── Group050_text_functions.py
    └── outputs/
```

运行顺序为 solution → EDA，各自使用 **Restart and Run All**。不要手动修改生成的六张 CSV 来代替修正处理逻辑。

## 同步范围

包含 submission 内的当前文件及组员贡献版本；不包含 `.DS_Store`、Python 缓存、Jupyter checkpoints、外部备份文件夹或原始资料包。
这是当前文件快照，不代表对最终提交清单或评分要求的重新审定。
