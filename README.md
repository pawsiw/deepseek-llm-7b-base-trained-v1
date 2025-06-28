# Training: deepseek-llm-7b-base-trained-v1
# 🧠 deepseek-llm-7b-base-trained-v1

Fine-tuning and training setup for DeepSeek LLM 7B model using custom source code and RAG.

---

## 📁 Project Directory Structure

All project-related directories are organized under `/mnt/deepseek` with a clear separation between models, data sources, training runs, and tools:

/mnt/deepseek/
├── models/             # All trained models and their configurations
│   └── <model_name>/   # e.g. deepseek-llm-7b-base-trained-v1
│       ├── config/         # Model, tokenizer, and training configs
│       ├── checkpoints/    # Checkpoints from training
│       ├── logs/           # Logs from training or evaluation
│       ├── scripts/        # Training/inference scripts (e.g. train_lora.py)
│       └── README.md       # Documentation for the model
│
├── projects/           # Source repositories and RAG inputs
│   └── <project_name>/     # e.g. my-agent, customers-api
│       ├── src/            # Source code
│       ├── docs/           # Documentation
│       ├── data/           # Optional input data
│       └── README.md
│
├── datasets/           # Processed datasets for training (JSONL, pickle, etc.)
│   └── <dataset_name>.jsonl
│
├── runs/               # Individual training/evaluation runs
│   └── <run_id>/           # e.g. deepseek-v1-20250628
│       ├── config.json     # Snapshot of run config
│       ├── metrics.json    # Evaluation metrics
│       ├── log.txt         # Execution log
│       └── output/         # Output from the run
│
├── tools/              # Utilities and helper scripts
│   └── tokenizer_utils.py, preprocess.py, etc.
│
└── shared/             # Optional shared assets (e.g. prompts, glossaries)
    └── prompts/, glossary.txt, ...


---

## 🔧 Training Strategy

This model is trained using a retrieval-augmented generation (RAG) approach, leveraging isolated customer code repositories. The training pipeline includes:

- Data preprocessing from `projects/`
- Dataset generation into `datasets/`
- LoRA fine-tuning via scripts in `models/<name>/scripts/`
- Logging into `runs/`

---

## 📌 Notes

- All documentation, comments, and instructions are written in **English**
- No code is auto-generated unless explicitly requested
- This model acts as a **code-generating assistant**, not a chatbot
- All actions must be logged and reproducible
- Git is used for versioning scripts and configurations

---

## 🧩 Dependencies

- Python 3.10+
- Transformers >= 4.38
- DeepSeek LLM Toolkit
- Optional: `accelerate`, `peft`, `bitsandbytes`, `datasets`

---

## 🧪 Inference

To test inference locally:

```bash
cd models/deepseek-llm-7b-base-trained-v1/scripts/
python infer.py --model_dir ../checkpoints/last/ --prompt "Write a hello world script"

