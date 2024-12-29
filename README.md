# sus-tracker-twitch-bot V4 is current
Sus Tracker

Sus Tracker is a Python application designed to monitor and manage suspicious words in a Twitch chat. The application provides both a graphical user interface (GUI) and a Twitch bot to interact with the chat, allowing users to track, rate, and manage suspicious word usage. It also supports OAuth authentication for secure access to Twitch features.

Features

Twitch Chat Bot

Monitors messages in your Twitch channel for a customizable list of suspicious words.

Counts and tracks how often suspicious words are used.

Calculates a "Sus Level" to provide a percentage-based assessment of suspicious activity in the chat.

Runs as a background thread for seamless integration.

Graphical User Interface (GUI)

Add or remove suspicious words.

Display a list of current suspicious words.

Rate the chat based on word usage.

Reset suspicious word usage statistics.

Customize UI colors and button appearance.

Update the threshold for suspicious activity evaluation.

Persistent Data

Saves suspicious words to a file (suspicious_words.json) for persistence.

Maintains user data (user_data.json) for Twitch OAuth authentication.

Stores application settings (settings.json) for GUI customization and operational parameters.

Flask Web Server for OAuth

Handles Twitch OAuth authentication.

Exchanges authorization codes for access tokens.

Stores access tokens securely for each configured Twitch channel.

How It Works

OAuth Authentication

Login to Twitch:

The application generates an OAuth login URL and opens it in the user's web browser.

Users authorize the application to access their Twitch account.

Token Exchange:

The Flask server receives an authorization code and exchanges it for an OAuth token.

The token is saved and used to authenticate the Twitch bot.

Chat Monitoring

The Twitch bot connects to the user's channel using the OAuth token.

Messages are processed to check for suspicious words.

Usage counts are updated in real-time, and the "Sus Level" is calculated based on the threshold.

GUI Interaction

Managing Suspicious Words:

Users can add or remove words from the list of suspicious words via the GUI.

Changes are saved to suspicious_words.json for persistence.

Threshold Management:

Users can update the threshold for evaluating the "Sus Level".

The threshold affects how the application calculates the percentage-based "Sus Level".

Customizing the UI:

Users can change the background color, text color, and button color of the application.

Customizations are saved in settings.json.

Uploading Settings:

Current settings can be exported for sharing or backup.

Persistent Data Management

Suspicious Words:

Suspicious words and their usage counts are stored and updated in suspicious_words.json.

User Data:

User tokens and channel information are stored in user_data.json.

Settings:

UI and operational preferences are stored in settings.json.

Installation and Setup

Install Dependencies:

Install Python (>=3.7) and required libraries:

pip install asyncio flask requests twitchio

Run the Application:

Start the application by running the script:

python sus_tracker.py

Authenticate with Twitch:

Click "Log in with Twitch" in the GUI.

Follow the instructions to authorize the application.

Configure Suspicious Words:

Add or remove words using the GUI.

Monitor and Manage Chat:

View and manage suspicious word usage statistics in real-time.

File Structure

sus_tracker.py: Main application file.

suspicious_words.json: Stores the list of suspicious words.

user_data.json: Stores user tokens and channel information.

settings.json: Stores UI customization and operational settings.

chat_data/: Directory to save chat data logs (if needed).

Contributing

If you'd like to contribute to this project, feel free to open an issue or submit a pull request. Suggestions and feedback are always welcome!

License

This project is open-source and licensed under the MIT License.

Disclaimer

This application is intended for educational and personal use. Please comply with Twitch's terms of service and privacy policy when using this bot.


Word Usage:
Each suspicious word is tracked individually. Its suspicious level is calculated as:
number of times the word is used ÷ 1,000
For example:
If "word1" is used 10 times: 
10÷1,000=1%
If "word2" is used 250 times: 
250÷1,000=25%
Overall Suspicious Level:

The bot averages the suspicious levels of all tracked words. For example:
Word1 contributes 1%, and Word2 contributes 25%.
Average = (1+25)÷2=13%
Final suspicious level: 13%

Why 1,000?
The 1,000-message threshold ensures that the bot is useful for channels of all sizes:
Smaller channels can still detect suspicious words.
Larger channels don’t inflate the numbers disproportionately.

Edit: I added where it counts the number of words used, and there are no more case-sensitive words. The word message threshold can be  changed from 1,000 to whatever else dynamically now.
