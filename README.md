# EGOCL

Evidence-Gated Ontology-aware Contrastive Learning (EGOCL) for tsRNA-disease association prediction.

This cleaned repository contains the source code, preprocessing pipeline, reproducible experiment runners, leakage checks, selected plotting scripts, and the dataset files required to reproduce the main experiments. Local runtime folders, external baseline repositories, manuscript drafts, caches, model checkpoints, and generated result files are intentionally excluded.


## Environment

Python 3.10+ 

bash
pip install -r requirements.txt

For GPU training, install the PyTorch build that matches your CUDA version from the official PyTorch instructions.

## Data preprocessing

The cleaned repository already includes processed data. To rebuild from raw files:

```bash
python src/preprocess/parse_result.py
python src/preprocess/parse_doid.py
python src/preprocess/build_graph.py
python src/preprocess/build_doid_paths.py


##  EGOCL 
```bash
python src/train.py --num_folds 5 --epochs 100 --hidden_dim 128 --num_layers 2 --batch_size 512 --lr 0.001 --dropout 0.2 --weight_decay 1e-5 --patience 20 --use_evidence_gate --use_ontology --use_path_attention --use_direction --use_tsrna_attr --use_tsrna_seq --tsrna_kmer 3 --tsrna_attr_fusion gated --use_attr_contrastive --attr_cl_weight 0.05 --output_dir results/egocl_tsrna_attr
```
