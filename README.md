# Training: deepseek-llm-7b-base-trained-v1
# 🧠 deepseek-llm-7b-base-trained-v1

Fine-tuning and training setup for DeepSeek LLM 7B model using custom source code and RAG.

---

## 📁 Project Directory Structure

The root directory on the local machine is `/mnt/deepseek/`. All project-related directories are organized under this root with a clear separation between models, data sources, training runs, and tools:

```
/mnt/deepseek/
├── deepseek-llm-7b-base-trained-v1/  
│   ├── models/                       
│   │   └── <model_name>/             
│   │       ├── config/               # Model, tokenizer, and training configs
│   │       ├── checkpoints/          # Checkpoints from training
│   │       ├── logs/                 # Logs from training or evaluation
│   │       ├── scripts/              # Training/inference scripts (e.g. train_lora.py)
│   │       └── README.md             # Documentation for the model
│   │
│   ├── projects/                     
│   │   └── <project_name>/           
│   │       ├── src/                  # Source code
│   │       ├── docs/                 # Documentation
│   │       ├── data/                 # Optional input data
│   │       └── README.md
│   │
│   ├── datasets/                     
│   │   └── <dataset_name>/           # Processed datasets for training (JSONL, pickle, etc.)
│   │       ├── config.json           # Snapshot of run config
│   │       ├── raw/                  # Copied source code files
│   │       ├── processed/            # JSONL files for pretrain/instruct formats
│   │       │   ├── pretrain.jsonl    # self-supervised code corpus (planned)
│   │       │   └── pretrain.jsonl    # instruct.jsonl`: instruction-tuned dataset (planned)
│   │       ├── meta.json
│   │       └── README.md
│   │
│   ├── runs/                         
│   │   └── <run_id>/                 
│   │       ├── config.json           # Snapshot of run config
│   │       ├── metrics.json          # Evaluation metrics
│   │       ├── log.txt               # Execution log
│   │       └── output/               # Output from the run
│   │
│   ├── tools/                        
│   │   └── tokenizer_utils.py, preprocess.py, etc.
│   │
│   └── shared/                       
│       └── prompts/, glossary.txt, ...
│
├── projects/my_agent/                # Own agent implementation
├── projects/python-genai/            # Reference Gemini implementation (Google)
```

**Note:** The source files under `/mnt/deepseek/deepseek-llm-7b-base-trained-v1/` are stored in the GitHub repository: [https://github.com/pawsiw/deepseek-llm-7b-base-trained-v1.git](https://github.com/pawsiw/deepseek-llm-7b-base-trained-v1.git)

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
```

