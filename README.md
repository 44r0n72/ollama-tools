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

## 📱 Connecting Android to Local Ollama Models

You can access your local Ollama models from your Android device using the **Chatbox** app. Here's how:

### Prerequisites
- Ollama running on your local machine
- Android device on the same network as your computer
- [Chatbox app](https://chatboxai.app/) installed on your Android device

### Step 1: Configure Ollama to Accept Network Connections

By default, Ollama only accepts connections from localhost. You need to configure it to listen on your network:

#### On Linux:
1. Edit the systemd service file:
```bash
sudo systemctl edit ollama.service
```

2. Add the following configuration:
```ini
[Service]
Environment="OLLAMA_HOST=0.0.0.0:11434"
```

3. Restart the Ollama service:
```bash
sudo systemctl daemon-reload
sudo systemctl restart ollama
```

#### On macOS:
1. Set the environment variable using launchctl:
```bash
launchctl setenv OLLAMA_HOST "0.0.0.0:11434"
```

2. Restart Ollama application

#### On Windows:
1. Open System Environment Variables
2. Add a new system variable:
   - Name: `OLLAMA_HOST`
   - Value: `0.0.0.0:11434`
3. Restart Ollama application

### Step 2: Find Your Computer's IP Address

#### On Linux/macOS:
```bash
ip addr show | grep "inet " | grep -v 127.0.0.1
# or
ifconfig | grep "inet " | grep -v 127.0.0.1
```

#### On Windows:
```cmd
ipconfig
```

Look for your local IP address (usually starts with `192.168.` or `10.`)

### Step 3: Configure Chatbox on Android

1. Open **Chatbox** app on your Android device
2. Go to **Settings**
3. Select **AI Provider** or **Model Provider**
4. Choose **Ollama** from the list
5. Enter your Ollama server URL:
   ```
   http://YOUR_COMPUTER_IP:11434
   ```
   For example: `http://192.168.1.100:11434`
6. Save the settings
7. Select your desired model from the available local models

### Step 4: Test the Connection

1. In Chatbox, start a new conversation
2. Send a test message
3. You should receive a response from your local Ollama model

### 🔒 Security Considerations

⚠️ **Important**: Exposing Ollama to your network has security implications:

- Only expose Ollama on **trusted networks** (like your home network)
- **Never** expose Ollama to the public internet without proper security measures
- Consider using a firewall to restrict access to specific devices
- On public or untrusted networks, use a VPN or SSH tunnel instead

### Alternative: SSH Tunnel (More Secure)

For better security, especially on untrusted networks, use an SSH tunnel:

1. Install **Termux** on your Android device
2. Set up SSH access to your computer
3. Create an SSH tunnel:
```bash
ssh -L 11434:localhost:11434 user@your-computer-ip
```
4. In Chatbox, use `http://localhost:11434` as the server URL

### 🐛 Troubleshooting

**Can't connect from Android:**
- Ensure both devices are on the same network
- Check if firewall is blocking port 11434
- Verify Ollama is running: `curl http://localhost:11434/api/tags`
- Test from your computer first: `curl http://YOUR_IP:11434/api/tags`

**Connection timeout:**
- Check firewall settings on your computer
- Ensure Ollama is configured with `OLLAMA_HOST=0.0.0.0:11434`
- Try restarting Ollama service

**Models not showing in Chatbox:**
- Verify models are installed: `ollama list`
- Check Chatbox can reach the server (test with a simple HTTP request)
- Ensure you're using the correct API endpoint format

## 📝 License

MIT License - Feel free to use and modify!

## 🤝 Contributing

Suggestions and improvements welcome!
