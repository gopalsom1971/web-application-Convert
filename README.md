# 🚀 Telegram Bot with Custom Peer Type Handling

This project is a Telegram bot built using Pyrogram. It includes a custom solution to handle "Peer ID invalid" errors by overriding the default peer type determination logic in Pyrogram.

## 📋 Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)

## 🌟 Introduction

Telegram bots are powerful tools that can automate tasks, manage groups, and much more. This bot leverages the Pyrogram library, providing a robust foundation for interacting with Telegram's API. One of the common issues developers face when working with Telegram bots is the "Peer ID invalid" error. This project includes a custom solution to address this issue by overriding the peer type determination function.

## ⚙️ Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/your-repo.git
   cd your-repo
   ```

2. **Install Dependencies**:
   Ensure you have Python installed. Then, install the required packages using pip:
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure API Credentials**:
   Replace the placeholder values in the script with your actual Telegram API credentials:
   ```python
   API_ID = "your_api_id"
   API_HASH = "your_api_hash"
   BOT_TOKEN = "your_bot_token"
   ```

## 🚀 Usage

Once you’ve set up the environment and configured your credentials, you can run the bot with the following command:

```bash
python tg.py
```

The bot will start and execute the tasks defined in your script.

## ✨ Customization

### Handling Peer ID Invalid Errors

One of the key features of this project is a custom function that accurately identifies the type of a peer (user, chat, or channel) based on its ID. This is particularly useful for avoiding "Peer ID invalid" errors.

```python
#-------------------------------------------------------------(THIS PART FOR REMOVE PEER-ID INVALID)----------------------
import pyrogram.utils as utils  # Importing Pyrogram utils

# Custom get_peer_type function
def get_peer_type(peer_id: int) -> str:
    print('get_peer_type call')
    peer_id_str = str(peer_id)
    if not peer_id_str.startswith("-"):
        return "user"
    elif peer_id_str.startswith("-100"):
        return "channel"
    else:
        return "chat"

# Overriding the Pyrogram's get_peer_type with your custom function
utils.get_peer_type = get_peer_type
#--------------------------------------------------------------------------------------------------------------------------
```

### Continuing with Your Main Script

After integrating the custom peer type handling, the rest of your bot script continues as usual:

```python
# Original bot.py/main.py code continues....

# Your existing script continues from here...
```

## 🤝 Contributing

We welcome contributions! If you have suggestions or improvements, feel free to open an issue or submit a pull request.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
