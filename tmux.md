# create a seesion
> tmux new-session -s seesion_1
> tmux new -s seesion_1
## -d
don't attach to current window
> tmux new -s seesion_1 -d

# kill seesion
> tmux kill-session -t seesion_1


# comand prefix
> Ctrl+b
## t
press Ctrl+b, then t
a large clock appear on the screen
## d
detach from a seesion
## c
create a window in a current session
## ,
rename a window
## p
go to the previous window
## n
go to the next window
## number e.g 0, 1, ...
go to the target number window
## w
display a visual menu of your windows
## f
find a window that contains a string of text
## &
close a window
or use exit
## %
virtically split 
## "
horizontally split
## o
cycle through the panes
## Up, Down, Left, Right
move around the panes
## space
- even-horizontal
- even-vertical
- main-horizontal
- main-vertical
- tiled
## x
kill a pane, which also closes the window if there's only one window
## :
enter command mode
## ?
get a list of all predefined keybindings and associated commmands these trigger

# .tmux.conf
```bash
# Setting the prefix from C-b to C-q
set -g prefix C-q
# free the original C-b key
unbind C-b
# reload the configuration file
bind r source ~/.tmux.conf \; display "Reloaded!"
# ensure that we can send Ctrl-Q to other apps
bind C-q send-prefix
# splitting panes with | and -
bind | split-window -h
bind - split-window -v
# moving between panes with prefix h,j,k,l
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R
# quick window selection
bind -r C-h select-window -t :-
bind -r C-l select-window -t :+
# rezise pane size, allow repeat
bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5
# mouse
# set -g mouse on
set -g mouse on
# set the default terminal mode to 256color mode
set -g default-terminal "screen-256color"
# set color for the active window
setw -g window-status-current-style bg=red
# set escape time zero
set -s escape-time 0

# scroll screen
setw -g mode-keys vi
# Ctrl-q, [
# up: Ctrl-u
# down: Ctrl-d
```

