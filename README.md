# sus-tracker-twitch-bot V3 is current
Make sure all dependencies are installed, these are the imported libraries. I used pyinstaller, but some may not have installed through it like requests or twitch

A Python application bot that reads chats and checks for sus words to give a sus level 
Add Suspicious Words:
Type the word you want to monitor into the box and click "Add Word."

Update threshold V3:

You can change the value of how the logic calculates dynamically. The logic is the same as below, but the percent rate value changes with this new threshold you set. 200 is a good base start.

Delete a Word:
Highlight the word in the list, then click "Delete Word" to remove it from monitoring.
Log In to Your Twitch Account:

Click the "Log in with Twitch" button. This will take you to a login screen.
After logging in, enter your Twitch channel name to connect to the bot.
If the login doesn’t work initially, try logging in again for a fresh connection.

You will need to log in each time you turn it on. This is how it resets for new chats.

Firewall Notifications:

The bot might trigger a firewall alert due to its use of networking libraries like Flask, Requests, and Twitch APIs.
If this happens: Click the firewall notification or go to your security settings under Firewall.
Allow the bot through the firewall.

Note: The bot contains no malicious code. It simply reads chat messages, counts occurrences of suspicious words, and updates a JSON file with the counts.

If you’re concerned, the bot’s source code will be made available on GitHub. This will allow you to customize it or verify the code.

How the Bot Works
The bot monitors chat messages for suspicious words that you specify.
Words not listed will not affect the "Suspicious Level."
At the end of the stream, click "Rate Chat" to calculate the overall suspicious activity.
This can be used as fun, or for moderation purposes.

What the Bot Doesn't Do
Moderation: The bot does not moderate chat, issue warnings, kick users, or take any other action against participants. It’s purely for fun and analysis.

Customization Needed for Moderation: If you require moderation tools, you’ll need to add them separately to suit your specific use cases.



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

Edit: I added where it counts the number of words used, and there are no more case-sensitive words.
