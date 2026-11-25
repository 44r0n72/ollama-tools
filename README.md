# Ollama Tools

A collection of shell scripts to make working with Ollama models easier.

## 🚀 Features

- **model-select**: Interactive selector for local and cloud models
  - Groups cloud models by SIZE `-` and keeps local models separate
  - Numbers choices across both groups and runs the selected model
  - Dynamically updates as you add/remove models

## 📦 Installation

1. Clone this repository:
```bash
git clone https://github.com/YOUR_USERNAME/ollama-tools.git
cd ollama-tools
```

2. Make the script executable:
```bash
chmod +x model-select
```

3. Add to your `.bashrc` or `.zshrc`:
```bash
echo "alias model='~/ollama-tools/model-select'" >> ~/.bashrc
source ~/.bashrc
```

## 💡 Usage

Simply type:
```bash
model
```

You'll see local and cloud Ollama models in separate groups, with choices numbered together:
```
Available Ollama models:

LOCAL MODELS:
 1) llama3.2:latest
 2) qwen3:8b

CLOUD MODELS:
 3) deepseek-v3.1:671b-cloud

Select model number (1-3): 3
Selected: deepseek-v3.1:671b-cloud
```

## 🔧 Requirements

- [Ollama](https://ollama.ai) installed and running
- Bash shell

## 📝 License

MIT License - Feel free to use and modify!

## 🤝 Contributing

Suggestions and improvements welcome!
