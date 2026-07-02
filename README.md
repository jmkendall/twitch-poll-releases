# Twitch Poll

A comprehensive Twitch polling system built with Streamer.bot integration, featuring real-time voting, admin control panel, and OBS overlay visualization.

## Download

Download the latest `Twitch-Poll.exe` from the [Releases](https://github.com/jmkendall/twitch-poll-releases/releases) section.

## Installation

1. Download `Twitch-Poll.exe` from the latest release
2. Create a folder for the application (e.g., `C:\Twitch Poll`)
3. Place `Twitch-Poll.exe` in that folder
4. Create a `.env` file in the same directory
5. Configure your environment variables (see below)
6. Run `Twitch-Poll.exe`

## Configuration

Create a `.env` file in the same directory as the executable with the following variables:

```env
PORT=3000
STREAMERBOT_PASSWORD=your_password_here
USE_BOT=false
SEND_RANDOM_VOTE_MESSAGES=false
```

### Environment Variables

- **PORT**: Server port (default: 3000)
- **STREAMERBOT_PASSWORD**: Streamer.bot WebSocket password (required if SEND_RANDOM_VOTE_MESSAGES is true) - leave blank if not sending messages to chat
- **USE_BOT**: (true/false) Use your bot account configured in Streamer.bot for notifications. If false, uses your streamer account
- **SEND_RANDOM_VOTE_MESSAGES**: (true/false) Send random vote results to chat

## Streamer.bot Setup

1. Open Streamer.bot and go to **Servers/Clients → WebSocket Server**
2. Set a password for authentication 
3. Click "Start Server"
4. Update the `.env` file with your Streamer.bot password

## Access Points

After running the executable, access the application at:

- **Admin Panel**: http://localhost:3000/admin
- **OBS Overlay**: http://localhost:3000/
- **Health Check**: http://localhost:3000/health

## Features

- **Real-time Voting**: Viewers vote with numbers 1–N in chat or type `!random`
- **Idempotent Voting**: Each user can vote only once per poll
- **Dynamic Configuration**: Start/stop polls and update options via the admin panel
- **Live Visualization**: Animated progress bars in the OBS overlay, winner badge on close
- **Random Voting**: Viewers can type `!random` to cast a random vote
- **Optional Icons**: Setting on admin panel to show images to the left of poll options


### Poll Image Handling

- Currently images are set up to download and display steam game banners automatically when provided either a matching game name or steam store page URL
- When a poll entry is a game that's not on steam there are three options
    1. Show no image for games that either don't exist on steam or can't be found
    2. Use a default image as a placeholder.  This can be done by saving an image in the images folder that is created in the same directory as the poll application after you start it.  Just name the image you want to use 'default'
    3. If you have an image you want to use for a game that's from Itch.io or any source other than Steam.  Name the image file the same name you use for the poll option when you save it to the images folder.  This will link the two together and display it for that option

## OBS Setup

1. Add a Browser Source in OBS
2. Set the URL to `http://localhost:3000/`
3. Configure the size (recommended: 400x300 pixels)

## Troubleshooting

### Votes Not Counting
- Verify the poll is active (check admin panel)
- Ensure Streamer.bot is connected if using chat integration
- Check that the `.env` file is in the same directory as the executable

### Overlay Not Updating
- Open browser console and check for WebSocket errors
- Confirm the server is running (check http://localhost:3000/health)
- Verify the OBS browser source URL is correct

## System Requirements

- Windows 10 or later
- Streamer.bot - you kind of need it to get votes from chat 
- OBS Studio (optional, for overlay display)

## License

MIT License
