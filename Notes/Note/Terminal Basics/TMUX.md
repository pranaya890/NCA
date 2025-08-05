Terminal multiplexer or  tmux is a tool to manage multiple terminal session from single window. similar as tabs of terminal
Why is tmux used?
Re- attaching and detaching terminal. session management, split screen,  persistent session i.e long running commands wont die.
#### Starting new session  using tmux

```
tmux
tmux new -s <session_name>
```
#### List the session
```
tmux ls
```

#### Reattach and Detach
exiting a tmux session is detaching a pane.
detaching will keep the server  alive until the system is rebooted
we can reattach the session from where we left at any time.
```
Ctrl+b then d #Detach from session
tmux attach -t <sessionname> #

```
#### To kill a session
```
tmux kill-session -t <session-name>
```

#### Split Windows
```
Ctrl b + " #Horizontal split
ctrl b + % # Vertical Split
```
#### Switch Between Panes
```
Ctrl b + arrowkeys
```
### To create new window
```
Ctrl B+ c #new window
Ctrl B +n #for next
Ctrl B+p #for previous
ctrl b+ [num] #for directly jumping to the window
```
#### To rename a window
``` 
Ctrl +B then ,
tmux rename-session -t <previous-name> <new-name>

```
### to zoom out and zoom in
``` Shell
Ctrl +b then z #to zoom in
#again for zoomout
```


## Screen
we can use screen command to create virtual environment inside the terminal
 its like opening multiple tabs inside the browser
 ```Shell
 screen # starting the screen
```

#### detaching a screen
we can use `Ctrl + a` then `d` to detach the screen but keep the process running in background
we can only use `Ctrl +d` to detach or `exit` to exit the screen

### reattaching  a screen
we can use  `-r` argument of screen to reattach the screen
``` Shell
screen -r
```
### screen activation
we can use `Ctrl + a ` top activate the screen functionality then we combine with other key to use its functionality same as detaching a screen

### screen finding 
we can find screen by listing it using `-ls` command then we can reattach using `screen -r identifier` 
![[Pasted image 20250729211720.png]]

### switching screens
we can create multiple windows inside a single session like multi tab in a browser``` Shell
`Ctrl +A  c`   for creating new window
`Ctrl +A  n` for next window
`Ctrl +A  p` for previous window 
`Ctrl +A  0`  for jumping to 0 window
`Ctrl +A  9` for jumping to 9 t window 
`Ctrl +A  " `  selection window for all window
