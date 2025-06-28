# 💻 Agent Training — Runbook: `deepseek-llm-7b-base-trained-v1`

---

## 🌐 Project Language Policy

All content in this project must be written **in English only**.

This applies to:
- All command sections in this file (`commands.md`)
- Code comments and docstrings (`.py`, `.groovy`, etc.)
- README files, changelogs, todos and configs
- Training data files (`.jsonl`, prompt/output examples)
- Variable names and identifiers, where applicable

**Polish or mixed-language content is strictly forbidden.**

---

## 🧱 STEP 1: Project structure and Git initialization

```bash
# Move to shared workspace
cd /mnt/deepseek

# Create project directory for this specific training
mkdir deepseek-llm-7b-base-trained-v1
cd deepseek-llm-7b-base-trained-v1

# Create directory structure
mkdir -p data/source
mkdir -p data/training
mkdir -p data/docs
mkdir -p models/base
mkdir -p models/lora
mkdir -p trainer
mkdir -p logs
mkdir -p configs

# Initialize local Git repository
git init

# Add initial files
echo "# Training: deepseek-llm-7b-base-trained-v1" > README.md
touch commands.md
git add .
git commit -m "Init"

# Add remote Git repository 
git remote add origin git@github.com:pawsiw/deepseek-llm-7b-base-trained-v1.git

# Rename default branch if necessary
git branch -M main

# First push
git push -u origin main
```
---
## 🧱 STEP 2 — Download base model using Git LFS

```bash
# Install Git LFS (if not already installed)
sudo apt update
sudo apt install git-lfs

# Initialize Git LFS
git lfs install

# Move to model storage directory
cd /mnt/deepseek/deepseek-llm-7b-base-trained-v1/models

# Clone the base model repository
git clone https://huggingface.co/deepseek-ai/deepseek-llm-7b-base

# Optional: Verify model structure
ls deepseek-llm-7b-base
```

---
# STEP 3

```bash
mkdir /mnt/deepseek/projects
cd /mnt/deepseek/projects
git clone git@github.com:pawsiw/my_agent.git
cd ..
cd /mnt/deepseek/projects/
git clone https://github.com/googleapis/python-genai.git

