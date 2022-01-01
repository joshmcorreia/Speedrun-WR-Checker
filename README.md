# Speedrun World Record Checker - Written by Josh Correia (joshmcorreia)
A world-record checker written in Python3 that uses the speedrun.com API. The goal of this program is to neatly organize all of the speedruns you wish to follow in one place. Main features include following multiple (unlimited) games at once, showing how far behind the world record each run is, showing when a run was completed, as well as many other customizable options for the user.<br />
<br />
![alt text](https://i.imgur.com/ErxixIu.png)

# Why use this tool instead of using speedrun.com's "Follow" feature?
The most important reason is speedrun.com's lack of customization for the follow function. I wrote this because I didn't want to be notified every single time there's an individual level WR, even though I only care about any%. This tool completely bypasses that issue by allowing the user to specify the categories of their choosing. Not only can you specify categories, but you can receive notifications for positions other than the world record. What I mean by this is that it will show you when someone gets a new record even if they aren't first place (for example if you have it show 10 places, then someone who gets a personal best for slot #4 will show up). This allows for easier tracking of people climbing the leaderboards and provides a better indication of how close people are to surpassing the current world record. <br />

# Prerequisites:
**Linux:** <br />
```sudo apt install python3``` <br />
```sudo apt install python3-pip```  <br />
```pip3 install srcomapi```  <br />

**MacOS:** <br />
```ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"``` <br />
```brew install python3``` <br />
```pip install srcomapi``` <br />

**Windows:** <br />
[Install the Linux Bash shell](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) <br />
```sudo apt install python3``` <br />
```sudo apt install python3-pip```  <br />
```pip3 install srcomapi```  <br />

# Getting started:
1) Install the prerequisites <br />
2) Clone this repository to your computer <br />
3) Edit the config.ini file and change the urls to whatever games you wish to follow
4) In your terminal type "python3 wr-checker.py"


# Using variables and choices:

**If a game has variables/choices and you don't specify them then the results will be inaccurate** <br />
Example: If you are tracking "https://www.speedrun.com/sm64#70_Star" and don't specify the value/choice, the runs that will show up in the tracker are for the default category which happens to be N64. If you wish to track the VC runs you MUST specify the value and choice. <br />

Variables and categories are a bit complicated so you have to manually find the name of the variables and categories that you wish to filter for. This can be done by going to {https://www.speedrun.com/api/v1/games/[game]/variables}, for example: {https://www.speedrun.com/api/v1/games/sm64/variables}. <br />


*Getting the variable:
From the variables page on the first line the very first id you see should correspond to the variable. <br />
Example: <br />
```{"data":[{"id":"e8m7em86","name":"Platform","category":null``` <br />
"Platform" is the value that we are trying to follow, so we want its corresponding id which is e8m7em86. <br />

*Getting the choice: <br />
From the variables page press Ctrl-F and find the choice that you wish to track. <br />
Example: Ctrl-F the term "N64" on the sm64 variables page which will bring up  <br />{"9qj7z0oq":"N64","jq6540ol":"VC","5lmoxk01":"EMU"}. We want the corresponding id for "N64", so the choice id we are looking for is "9qj7z0oq". <br />

Now that you have the variable and the choice you can add them to the URL of the game you wish to track preceded by a #. It should be in the following format: <br />
https://www.speedrun.com/[game_name]#[category]#[variable]#[choice] <br />
Example: https://www.speedrun.com/sm64#120_Star#e8m7em86#9qj7z0oq. <br />
This is interpreted as follows: <br />
Game: Super Mario 64 <br />
Category: 120 Star <br />
Variable: Platform <br />
Choice: N64 <br />



# Editing the config file:
```
number_of_players_to_track = 10 # This is how many players will be shown on the leaderboard when it is printed out <br />

show_time_behind_wr = True # This shows how far behind world record a run is <br />

show_date = True # This shows the date that the run was accomplished <br />

show_days_ago = True # This shows how many days ago the run was accomplished <br />

date_format = MM/DD/YY # This sets the format of the date that is printed on screen. Options: MM/DD/YY, YY/MM/DD, DD/MM/YY <br />

date_last_ran = 2019-03-20 # This is the date that the program was last run by the user. This is automatically updated when a world record check finishes running <br />

urls =  # This is where the player can specify what runs they follow. Proceed each entry with a [TAB] and follow it with a comma [,]. See the default config.ini file for a basic idea of how it works <br />
```


# Help:

Find an issue in the code? [Submit a bug](https://github.com/joshmcorreia/Speedrun-WR-Checker/issues)

Have a feature request? [Submit a feature request](https://github.com/joshmcorreia/Speedrun-WR-Checker/pulls)
