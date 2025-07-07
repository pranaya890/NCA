Terminal multiplexer or tmux is a tool to manage multiple terminal session from single window. similar as tabs of terminal
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
```
Ctrl+b then d #Detach from session
tmux attach -t <sessionname>

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
```
#### To rename a window
``` 
Ctrl + ,
```