# i3run - Run, Raise or hide windows in i3wm 

### usage

```text
i3run --instance|-i INSTANCE [--summon|-s] [--nohide|-g] [--mouse|-m] [--command|-e COMMAND] [--rename|-x OLD_NAME]
i3run --class|-c CLASS [--summon|-s] [--nohide|-g] [--mouse|-m] [--command|-e COMMAND] [--rename|-x OLD_NAME]
i3run --title|-t  TITLE [--summon|-s] [--nohide|-g] [--mouse|-m] [--command|-e COMMAND] [--rename|-x OLD_NAME]
i3run --conid|-n CON_ID [--summon|-s] [--nohide|-g] [--mouse|-m] [--command|-e COMMAND] [--rename|-x OLD_NAME]
i3run --help|-h
i3run --version|-v
```

`i3run` let's you use one command for multiple functions
related to the same window identified by a given criteria. 
`i3run` will take different action depending on the state of
the searched window: 

| **target window state**          | **action**
|:---------------------------------|:------------
| Active and not handled by i3fyra | hide
| Active and handled by i3fyra     | hide container, if not `-g` is set
| Handled by i3fyra and hidden     | show container, activate
| Not handled by i3fyra and hidden | show window, activate
| Not on current workspace         | goto workspace or show if `-s` is set
| Not found                        | execute command (`-e`)



Hidden in this context,  means that window is on the
scratchpad. Show in this context means,  move window to
current workspace. 


`-e` is optional, if no *COMMAND* is passed and no window is found,  nothing happens.  It is important that `-e` *COMMAND* is **the last of the options**.  It is also important that *COMMAND* **will spawn a window matching the criteria**,  otherwise the script will get stuck in a loop waiting for the window to appear. (*it will stop waiting for the window to appear after 10 seconds*)


OPTIONS
-------

`--instance`|`-i` INSTANCE  
Search for windows with the given INSTANCE

`--summon`|`-s`  
Instead of switching workspace, summon window to current
workspace

`--nohide`|`-g`  
Don't hide window/container if it's active.

`--mouse`|`-m`  
The window will be placed on the location of the mouse
cursor when it is created or shown. (*needs `xdotool`*) 

`--command`|`-e` COMMAND  
Command to run if no window is found. Complex commands can
be written inside quotes: 
```
i3run -i sublime_text -e 'subl && notify-send "sublime is started"'

```


`--rename`|`-x`  
If the search criteria is `-i` (instance), the window with
instance: *OLDNAME* will get a n new instance name matching
the criteria when it is created (*needs `xdotool`*).

`--class`|`-c` CLASS  
Search for windows with the given CLASS

`--title`|`-t` TITLE  
Search for windows with the given TITLE

`--conid`|`-n`  
Search for windows with the given CON_ID

`--help`|`-h`  
Show help and exit.

`--version`|`-v`  
Show version and exit.


