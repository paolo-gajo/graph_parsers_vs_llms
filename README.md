# LLMs Underperform Graph-Based Parsers on Supervised Relation Extraction for Complex Graphs

This repository contains the code and data-loading setup for the ACL 2026 paper **"LLMs Underperform Graph-Based Parsers on Supervised Relation Extraction for Complex Graphs"** by Paolo Gajo, Domenic Rosati, Hassan Sajjad, and Alberto Barrón-Cedeño.

The paper compares supervised LLM-based relation extraction against graph-based dependency parsing on relation extraction and dependency parsing datasets with varying graph complexity. The main finding is that graph-based parsers increasingly outperform much larger LLMs as the number of relations in the input graph grows, making the lighter parser architecture a strong choice for complex linguistic graphs.

## Structure

- `./biaffine_attention_parsing` contains the EfficientSDP/biaffine graph parser code.
- `./llm_parsing` contains the LLM text-to-graph fine-tuning and evaluation code.
- `./data` contains the shared datasets. This directory is intentionally ignored by git; download it separately from [this drive folder](https://drive.google.com/drive/folders/1vVKJIUzK4hIipfdEGmS0CCoFmUmZwOQV) and place it at the repository root.
- `./results` contains experiment outputs produced by the training/evaluation scripts.

## Data

After downloading the data, the repository should look like this:

```bash
graph_parsers_vs_llms/
├── biaffine_attention_parsing/
├── llm_parsing/
├── README.md
└── data/
    ├── ade/
    │   ├── bio/
    │   │   ├── train.json
    │   │   ├── val.json
    │   │   └── test.json
    │   └── rdf/
    │       ├── train.json
    │       ├── val.json
    │       ├── test.json
    │       ├── relations.json
    │       ├── relations_list.json
    │       ├── ent_classes.json
    │       └── ent_classes_list.json
    ├── conll04/
    │   ├── bio/
    │   └── rdf/
    ├── scierc/
    │   ├── bio/
    │   └── rdf/
    ├── scidtb/
    │   ├── bio/
    │   └── rdf/
    └── ...
```

The two parsers use different representations from the same root-level `data/` directory:

- `biaffine_attention_parsing/src` loads graph parser splits from `data/<dataset>/bio/train.json`, `val.json`, and `test.json`.
- `llm_parsing/src` loads LLM parsing data and schemas from `data/<dataset>/rdf/`.

You can check your local data layout with:

```bash
tree -L 3 data
```

## Citation

If you use this repository, please cite:

```bibtex
@inproceedings{gajo_2026_graphbasedparsersvsllms,
  title = {{LLMs Underperform Graph-Based Parsers on Supervised Relation Extraction for Complex Graphs}},
  author = {Gajo, Paolo and Rosati, Domenic and Sajjad, Hassan and Barr{\'o}n-Cede{\~n}o, Alberto},
  booktitle = {Proceedings of the 64th Annual Meeting of the Association for Computational Linguistics},
  year = {2026}
}
```
