
wrapper for the ghost window function in *i3wm*  

`i3-msg` has an undocumented function (open) that creates empty containers, or as I call them: ghosts. Since these empty containers doesn't contain any windows
there is no instance/class/title to identify them, making it difficult to control them. They do however have a `con_id` and I found the easiest way to keep track of the ghosts is to mark them. That is what this script does, it creates a ghost get its con_id and mark it.

usage
-----
`i3gw MARK`  

example
-------
`i3gw casper`

this will create a ghost marked casper, you can perform any action
you can perform on a regular container.  

    i3-msg [con_mark=casper] move to workspace 2 
    i3-msg [con_mark=casper] split v  
    i3-msg [con_mark=casper] layout tabbed  
    i3-msg [con_mark=casper] kill  

the last example (*kill*), destroys the container.

-------

In the screenshot below, the windows to the right are tiled, and a ghostwindow is tiled on the right half of the screen. The other windows are floating.

[![i3gw in action](/img/awd/ss-i3gw1.png)]((/img/org/ss-i3gw1.png))
