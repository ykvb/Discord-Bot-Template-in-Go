# Features
```
Command Handler: Prefix-based command system with easy routing
Event Listeners: Handles messages, guild joins, member joins, and more
Permission Management: Role-based permission checks for moderation commands
Error Handling: Comprehensive error handling throughout the codebase
Modular Architecture: Easy to extend with new commands and features
```

# Commands
## General Commands
```
!help - Display all available commands
!ping - Check bot latency and API response time
!info - Display bot information and statistics
!avatar [@user] - Get a user's avatar in high resolution
```
## Information Commands
```
!serverinfo - Display detailed server information
!userinfo [@user] - Display user information and roles
```
## Moderation Commands (Requires Permissions)
```
!kick @user [reason] - Kick a member from the server
!ban @user [reason] - Ban a member from the server
!clear <amount> - Bulk delete messages (1-100)
```
## Fun Commands
```
!8ball <question> - Ask the magic 8-ball a question
!roll [max] - Roll a dice (default 6, max 1000)
!poll <question> - Create a yes/no poll with reactions
```

# Installation & Setup
## Prerequisites
1. Go 1.21 or higher

2. A Discord Bot Token (from [Discord Developer Portal](https://discord.com/developers/applications))

### Step 1: Clone or Create Project
bash
```
mkdir discord-bot
cd discord-bot
```
### Step 2: Create Project Files
Create the following files in your project directory:
```
main.go - Main bot entry point
commands.go - Command implementations
go.mod - Go module definition
```
### Step 3: Initialize Go Module
bash
```
go mod init discord-bot
go mod tidy
```
This will download the required dependencies: github.com/bwmarrin/discordgo - Discord API library
### Step 4: Configure Bot Token
Create a .env file or set environment variable:
#### Linux/Mac:
```
export DISCORD_BOT_TOKEN="your-bot-token-here"
```
#### Windows (Command Prompt):
```
set DISCORD_BOT_TOKEN=your-bot-token-here
```
#### Windows (PowerShell):
```
$env:DISCORD_BOT_TOKEN="your-bot-token-here"
```
### Step 5: Run the Bot
```
go run main.go commands.go
```
Or build and run:
```
go build -o bot
./bot  # Linux/Mac
bot.exe  # Windows
```

# Discord Bot Setup
#### Go to Discord Developer Portal

#### Click "New Application" and give it a name

#### Go to the "Bot" tab and click "Add Bot"

#### Copy the bot token (keep this secret!)

#### Enable the following Privileged Gateway Intents:
```
✅ Server Members Intent
✅ Message Content Intent
```
# Inviting the Bot
#### Go to the "OAuth2" > "URL Generator" tab
### Select scopes:
##### ✅ bot
### Select bot permissions:
##### ✅ Send Messages
##### ✅ Embed Links
##### ✅ Read Message History
##### ✅ Add Reactions
##### ✅ Kick Members (for moderation)
##### ✅ Ban Members (for moderation)
##### ✅ Manage Messages (for clear command)
#### Copy the generated URL and open it in your browser
#### Select a server and authorize the bot
# Project Structure
```
discord-bot/
├── main.go           Bot initialization and event handlers
├── commands.go       Command implementations
├── go.mod            Go module definition
├── go.sum            Dependency checksums
└── .env              Environment variables (create this)
```
# Configuration
###  Environment Variables
# Customization
### You can customize the bot by modifying constants in main.go:
```
var prefix = "!"  // Change command prefix
```
# Adding New Commands
### To add a new command, follow these steps:
#### 1. Add a case to the switch statement in handleCommand() in main.go:
```
case "mycommand":
    cmdMyCommand(s, m, args)
```
#### 2. Implement the command function in commands.go:
```
func cmdMyCommand(s *discordgo.Session, m *discordgo.MessageCreate, args []string) {
    // Your command logic here
}
```
#### 3. Add command documentation to the help embed in cmdHelp()
## Security Best Practices
```
Never commit your bot token to version control
Add .env to .gitignore
Use environment variables for sensitive data
Implement rate limiting for production use
Validate all user input
Check permissions before executing moderation commands
```
## Dependencies
[Discord GO](https://github.com/bwmarrin/discordgo) - Discord API library for Go
# Error Handling
 The bot includes comprehensive error handling:
```
Failed API calls are logged
User-facing errors are displayed with embedded messages
Permission checks prevent unauthorized command usage
Input validation prevents crashes from malformed commands
```
# Performance Considerations
```
The bot uses Discord Gateway intents to reduce unnecessary events
Bulk operations are used where possible (e.g., bulk message deletion)
Goroutines handle concurrent operations efficiently
Graceful shutdown ensures clean disconnection
```
# Troubleshooting
### Bot doesn't respond to commands
```
Verify the bot token is correct
1. Check that Message Content Intent is enabled
2. Ensure the bot has permission to read and send messages
3. Verify the command prefix matches
```
### Permission errors
```
1. Ensure the bot role is positioned high enough in the role hierarchy
2. Verify required permissions are granted during bot invitation
3. Check that the bot has appropriate channel permissions
```
### Connection issues
```
1. Verify your internet/vps connection
2. Check Discord's status page for API outages
3. Ensure firewall isn't blocking WebSocket connections
```
# Contributing
### To extend this bot:
```
1. Follow the existing code style
2. Add comprehensive error handling
3. Document new commands in the README
4. Test thoroughly before deployment
```
# Support
### For issues related to:
#### DiscordGo library: Visit [DiscordGO Github](https://github.com/bwmarrin/discordgo)
#### Discord API: Check [Discord Developer Documentation](https://discord.com/developers/docs/intro)
#### Go programming: See [Go Documentation](https://go.dev/doc/)
#### FaQ: Join [My Discord Server](https://discord.gg/pkbPg2nahc)
# Future Enhancements
## Potential features to add:
```
1. Database integration for persistent data
2. Custom prefix per server
3. Music playback
4. Scheduled tasks/reminders
5. Economy system
6. Leveling system
7. Custom role reactions
8. Logging system
9. Web dashboard
10. Slash commands support
```
