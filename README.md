# Discord Bot Template

This is a modular and extensible template for building Discord bots using `discord.py`. It includes utilities for configuration management, database connections, GitHub integration, and logging, making it easy to get started with your bot development.

---

## Features

- **Modular Design**: Easily add new functionality using the `functions` folder with cogs.
- **Database Integration**: Supports MySQL database connections.
- **GitHub Integration**: Automatically pulls and loads functions from a GitHub repository.
- **Logging**: Centralized logging for bot events and errors.
- **Memory Tracking**: Tracks memory usage with `tracemalloc`.

---

## Project Structure

```
Disocrd-Bot-Template/
│
├── bot.py                  # Main bot entry point
├── datastores/
│   └── config.json         # Configuration file
├── functions/
│   └── CogTemplate.py      # Example cog template
├── utils/
│   ├── config_utils.py     # Configuration loader
│   ├── database_utils.py   # Database connection setup
│   ├── github_utils.py     # GitHub repository integration
│   └── logger_utils.py     # Logging utilities
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation
```

---

## Getting Started

### Prerequisites

- Python 3.8 or higher
- A Discord bot token
- MySQL database (optional)
- GitHub repository URL (optional)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/Disocrd-Bot-Template.git
   cd Disocrd-Bot-Template
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Configure the bot:
   - Create a `datastores/config.json` file based on the following template:
     ```json
     {
       "token": "YOUR_DISCORD_BOT_TOKEN",
       "application_id": "YOUR_APPLICATION_ID",
       "use_DB": true,
       "database": {
         "host": "localhost",
         "user": "root",
         "password": "password",
         "database": "bot_database"
       },
       "use_Git": true,
       "repo_url": "https://github.com/your-repo",
       "repo_temp": "main"
     }
     ```

4. Run the bot:
   ```bash
   python bot.py
   ```

---

## Example: Adding a New Cog

To add a new cog, create a Python file in the `functions` folder. Below is an example of a cog that responds with "Hello, world!" when the `!hello` command is used.

### Example: `functions/MyNewCog.py`

```python
import discord
from discord.ext import commands

class MyNewCog(commands.Cog):
    def __init__(self, bot):
        self.bot = bot

    @commands.command()
    async def hello(self, ctx):
        await ctx.send("Hello, world!")

async def setup(bot):
    await bot.add_cog(MyNewCog(bot))
```

---

## Utilities

### Configuration Loader (`utils/config_utils.py`)
Handles loading the bot's configuration from a JSON file.

### Database Connection (`utils/database_utils.py`)
Sets up a connection to a MySQL database.

### GitHub Integration (`utils/github_utils.py`)
Downloads and extracts a GitHub repository to load additional bot functions.

### Logging (`utils/logger_utils.py`)
Provides centralized logging for bot events and errors.

---

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests to improve this template.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

