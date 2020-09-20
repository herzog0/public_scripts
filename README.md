# cipher

Simple program to encrypt and descrypt text with the use of a password.

## Dependencies

```
python3.*
```

### Usage:

```shell
$ cipher # This will prompt you to insert text to be encrypted.

$ cipher decode # This will prompt you to insert the encrypted text (to be decrypted).
```







# agile_commit

This script is intended to speed up the process of commiting changes to a project you're 
working a lot.  
I've realized that many times I don't commit stuff just because it takes too long to open 
a terminal, go to the folder, add and commit things.  
Set a keybinding to this script and you're good to go.  

## Dependencies

```
yad (installable by apt)
```

### Usage:

This script recursively searches for git repositories within a certain folder.  
This certain folder has to be specified in the `PARENT_PATH` variable at the top of the script.  
The other variable that you have to set is `SETTINGS_PATH` (pointing to a settings.json file).  

`PARENT_PATH` will provide the starting place for finding git repositories (if you set this as your home folder 
you'll probably loose a long time searching for repos).  

`SETTINGS_PATH` will record your chosen repository and prompt the changes of that repo right away, until you reconfigure the repo with the obvious button.  







# progbar

It prints a nice progress bar until your process pid exists!  

## Dependencies

None :)

### Usage:

```shell
$ progbar <your command>

# Output

# [▓▓▓▓▓▓
# (When it's done, it print's a last ']')

```








# send_to_telegram

Sends anything to a Telegram bot of your own!  
This can be used to treat a Telegram bot as your personal quick backup system.  
Send quick messages to remember info later, send pictures, audio, entire folders, videos, files etc.  

Note: Telegram limits file size in 50MB to send programatically to a bot, so there's that.  

## Dependencies

```
python3.*

telepot (installable by pip)
```

Also, you'll have to create a bot and retrieve your chat id!  
Do the first task by initating a conversation with @BotFather. It'll do the rest.  

To find your chat id, you can call @chatid_echo_bot. It will echo your chat id, then you can set the require environment variables in the script. 

### Usage:

```shell
$ send_to_telegram <anything>
```

Note: if you get a message "Nothing to do :(", that's because the file mimetype is not registered in in the "mimetypes" dictionary.  
In that case, just open the script with your editor and put the printed mimetype within the desired function array (you'll find the place, believe me).








# telegram_logger

This is a subset of the script `send_to_telegram`. This will works the same, but is intended to just send text to your telegram bot.  It's actually a very useful script.  
(See the dependency section of `send_to_telegram` because there's two more simple steps to configure).

## Dependencies

```
python3.*

telepot (installable by pip)
```

### Usage:

```shell
$ telegram_logger "something"
$ <long running command>; telegram_logger "Done! Stop your coffee and come back."
$ <command on your remote server>; telegram_logger "Work done in your server $(hostname)"
```







# toggle_pid_network

This script moves a provided PID to a `cgroup` with a blocked network.  
Sometimes you just want the remove internet access from a process. Well, with this, your life get's easier.  

## Dependencies

```
fzf (nice fuzzy search interface)
```

### Usage:

```shell
$ toggle_pid_network <name of the program/script to search pids with pgrep>

$ toggle_pid_network -r # Gives back internet access to all blocked pids
```







# uap

This script's intent is to provide a simple way to update multiple packages that depend on each other and that lives inside the same directory.

Also, you have simple ways to print all project names and version within a certain folder.  

My problem was:
I had this folder
Projects/
├── pck1/
├── pck2/
├── ....
└── pckn/
And pckx is a dependency to pcka, pckb, pckc...
Whenever I had to make an important change in pckx I had to go in each dependant project, update pckx's version,
update the dependant package version, npm install, npm build, pack publish etc...
This script does all this, but it will help you by:
1) Recursively find all packages that depend on pckx and are out of date ( you must provide the new pckx's version ).
2) Loop through each package folder asking to update pckx's version and the package version ( it does an increment
of its rightmost digit ).
3) If you accept the update, the script checks if current git index is equal to HEAD, if not, it does not let you
update the package.
4) If passes '3)', runs 'npm install', 'npm run build', 'npm pack' and 'npm publish'.
5) If you want, the script automatically commits the new changes and tags the commit.
A good note is that you don't have to worry about the script trying to search in standard non-user folders, like
node_modules. This happens because we use 'ack' as opposed to 'find' command to find all package.json files in that
folder.

Just use `uap -h` and see what else it can do!  


## Dependencies

```
ack (installable by apt)
python
```

## Usage: 

Usage: uap [options] [package's name] [package's new version]

Options:

	-h      This help message.
	-p      Only prints all packages names and versions in that folder (and subfolders)
	    -P      Same as above but with full path
	-u      (-v required also) If no options are provided, this is the one supposed. It searches and updates
	        a package version in all package.json files it can find in that folder, taking
	        care of re-publishing the updated package and committing the change.
	    -s      Perform a simple update on the righmost digit of the package.json file in your current dir
	-v      The package's version being updated.



