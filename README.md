# Ollama Tools

A collection of shell scripts to make working with Ollama models easier.

## 🚀 Features

- **model-select**: Interactive local model selector
  - Automatically filters out cloud models
  - Shows only locally downloaded models
  - Dynamically updates as you add/remove models
  - Simple numbered selection interface

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

You'll see a list of your local Ollama models:
```
Available LOCAL Ollama models:

 1) mistral:7b
 2) deepseek-coder:latest
 3) deepseek-r1:1.5b

Select model number (1-3):
```

## 🔧 Requirements

- [Ollama](https://ollama.ai) installed and running
- Bash shell

## 📝 License

MIT License - Feel free to use and modify!

## 🤝 Contributing

Suggestions and improvements welcome!
