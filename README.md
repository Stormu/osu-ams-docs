# Information for using the bot.
Down below is a bunch of information pertaining to the irc bot used in osu! multiplayer lobbies. If you're not a bot owner or an admin, this information may not matter to you. This is not to be confused with another osu! ams bot used by osu! ranked lobbies.

## How it works
The osu-ams bot sends a query to the osu! API in a similar fashion to you using the search feature for beatmaps on the osu! website. Based on the total amount of beatmapsets matching it's criteria, the bot will then randomly generate a number as to randomly pick any mapset from any page. It'll then verify how many difficulties of a matching beatmapset fit into the criteria of the kind of maps the bot is looking for. If more than one difficulty matches the bot's criteria, the bot will then randomly select one of the difficulties and load it into the multiplayer lobby.

## FAQ
#### Am I able to change the kind of beatmaps the bot searches for (such as star difficulty, bpm, etc)?
Unless the bot owner has made you an admin, none of the commands listed below as **Admin Commands** will work for you. As such, you will be unable to edit anything relatig to the bot. If you are an admin, feel free to use the `!query` command!

#### Selected maps have a star rating outside the set range!
This is a limitation of star ratings not being fully calculated client side. I assure you, however, that beatmaps selected by the bot will always match the star difficulty restrictions if any are placed.

#### Everyone is ready but the bot has not started the match
This is a limitation of how BanchoBot perceives everyone to be ready. If everyone says they are ready except for one last player and said player leaves the lobby, BanchoBot will assume the entire lobby still isn't ready to play. Simply have one player unready then ready again to fix this.

#### The match began before I finished downloading a map and is now stuck
First off, if this happens, please increase the timer amount. To fix this, either use `!abort` to abort the progression of the phantom match or leave and join again and the lobby should reset itself.

## Public Commands
Below is a list of commands able to be used by any player in the lobby.

| Command | Function |
|---------|----------|
| `!abort` | Begins a vote to abort the match. Only works while a match is in progress. |

## Admin Commands
Below is a list of commands able to be used by players marked as admins by the bot owner.

| Command | Function |
|---------|----------|
| `!abort` | Aborts a match. Same as the BanchoBot command `!mp abort`. |
| `!clearhost` | Clears the host from the lobby. Same as the BanchoBot command `!mp clearhost`. |
| `!host` | Makes the user the lobby host. Same as the BanchoBot command `!mp host`. |
| `!info` | Returns a link to this page. Meant to provide information to admins. |
| `!kick [player]` | Kicks the player mentioned. Same as the BanchoBot command `!mp kick [player]`. |
| `!lb [type]` | Change the kind of maps you get. Tells the bot whether to search for beatmaps with or without a leaderboard or to not care. Acceptable types: graveyard, any, *. |
| `!password [password]` | Sets a password for the lobby. Same as the BanchoBot command `!mp password [password]`. |
| `!query [string]` | Sets restrictions on a lobby. Check below for a tutorial on how to use this command. |
| `!ruleset` | Returns the current restrictions of a lobby. |
| `!size [number]` | Sets the size of a lobby. Same as the BanchoBot command `!mp size [number]`. **NOTE**: Setting the size to 0 closes the lobby. |
| `!skip` | Skips the current beatmap selected and has the bot fetch a new beatmap. Stops countdown timer if the timer is enabled. |
| `!start` | Skips the timer and immediately starts the match. Same as the BanchoBot command `!mp start` |
| `!stop` | Stops the automatic countdown timer. The timer will not run again until the match is over. |
| `!timer [seconds]` | Sets the number of seconds the automatic timer counts down. Acceptable range is 30 seconds to 5 minutes (300 seconds). |
| `!tr` | Stands for *toggle random*. Tells the bot whether to automatically fetch a new map after a match or not. |
| `!tt` | Stands for *toggle timer*. Enable/disable the automatic timer that begins upon map change. |

## Formatting a Query
Here is a tutorial of how to use the `!query` command to add restrictions to a multiplayer lobby utilizing the bot.

There are 5 attributes of a beatmap you can tell the bot to filter for. These include: AR (Approach rate), BPM (Beats per minute), CS (Circle Size), Length, and Star (Star rating)

The operators accepted by the bot: `<`, `<=`, `>`, `>=`, `=`, `!=`

In order to format the query, you would put the attribute on the left followed by the operator and then the value. **NOTE: DO NOT PUT SPACES BETWEEN THE ATTRIBUTE, OPERATOR, AND VALUE. THIS WILL CAUSE YOUR QUERY TO NOT WORK.**

An example of a proper query would be: `ar=10` or `star<=7`.
To include multiple restrictions, place spaces between restrictions. The bot will use the spaces as an indication of where one restriction ends and the other begins. Example: `star>=6 star<=7 cs<=5.5`

You can also just type an artist or title of a song and such to filter for those maps. However, this is extremely inaccurate and the bot will most likely choose maps undesired regardless so I don't recommend doing that.
