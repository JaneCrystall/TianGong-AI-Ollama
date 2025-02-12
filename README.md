# TianGong Ollama

## Installation
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

## GPUs Allocation

### Disable Nvidia GPUs
Bash scripts to stop nvidia services and unload nvidia kernel modules

```bash
sudo systemctl stop ollama

sudo lsof /dev/nvidia*

sudo systemctl edit ollama

# add the following lines:
[Service]
Environment="CUDA_VISIBLE_DEVICES=-1"
# Environment="OLLAMA_HOST=0.0.0.0:11434"

sudo systemctl start ollama
```

## Model Selection
```bash
# 4G
ollama run deepseek-r1:1.5b-qwen-distill-fp16
ollama run qwen2.5:1.5b-instruct-fp16

# 12G
ollama run deepseek-r1:14b-qwen-distill-q4_K_M
ollama run qwen2.5:14b-instruct

# 16G
ollama run deepseek-r1:7b-qwen-distill-fp16
ollama run qwen2.5:14b-instruct-q6_K

# 32G
ollama run deepseek-r1:14b-qwen-distill-fp16
ollama run qwen2.5:32b-instruct-q6_K

# 80G
ollama run deepseek-r1:70b-llama-distill-q8_0
ollama run qwen2.5:72b-instruct-q8_0

# 800G (CPU)
ollama run deepseek-r1:671b-q8_0
ollama run deepseek-v3:671b-q8_0
```

## UI (optional)

Setup `venv`:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
```

Install requirements:

```bash
pip install --upgrade pip
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install -r requirements.txt --upgrade

# pip freeze > requirements_freeze.txt

open-webui serve
```
