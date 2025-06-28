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

