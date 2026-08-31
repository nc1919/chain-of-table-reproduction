# Chain-of-Table

This repository is a personal fork/snapshot of the Google Research project [Chain-of-Table: Evolving Tables in the Reasoning Chain for Table Understanding](https://arxiv.org/abs/2401.04398). The algorithm and the majority of the code are the work of the upstream authors; see [google-research/chain-of-table](https://github.com/google-research/chain-of-table) for the canonical archived repository.

It should be presented as reproduced or adapted upstream work, not as an original portfolio project.

## Environment

```bash
conda create --name cotable python=3.10 -y
conda activate cotable
python -m pip install -r requirements.txt
```

## Data

The included `data.zip` follows the upstream snapshot and contains the cleaned TabFact support files described by the original authors.

```bash
unzip data.zip
```

Review the upstream acknowledgements and dataset terms before redistributing or using the data.

## API credentials

Never put an API key in source, notebooks, command-line arguments, or committed output. Supply it through the environment:

```bash
read -rsp "OpenAI API key: " OPENAI_API_KEY
export OPENAI_API_KEY
```

The current runner reads `OPENAI_API_KEY` when `--openai_api_key` is omitted.

## Run

First ten TabFact cases:

```bash
python run_tabfact.py \
  --result_dir results/tabfact_first10 \
  --first_n 10 \
  --n_proc 10 \
  --chunk_size 1
```

Full dataset:

```bash
python run_tabfact.py \
  --result_dir results/tabfact \
  --n_proc 20 \
  --chunk_size 10
```

The pinned client targets the legacy OpenAI Python API used by the archived upstream code. Model availability and API behaviour may have changed; treat this as a reproducibility snapshot.

## Citation

If you use the upstream work, cite:

```bibtex
@article{wang2024chain,
  title={Chain-of-Table: Evolving Tables in the Reasoning Chain for Table Understanding},
  author={Wang, Zilong and Zhang, Hao and Li, Chun-Liang and Eisenschlos, Julian Martin and Perot, Vincent and Wang, Zifeng and Miculicich, Lesly and Fujii, Yasuhisa and Shang, Jingbo and Lee, Chen-Yu and Pfister, Tomas},
  journal={ICLR},
  year={2024}
}
```

## Licence and third-party material

The upstream code is distributed under Apache-2.0; see [LICENSE](LICENSE). The row/column prompt source under `third_party/` carries its own MIT licence. Dataset and model/API terms are separate from the code licence.
