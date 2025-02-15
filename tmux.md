tmux is a terminal multiplexer: it enables a number of terminals to be created, accessed,  and controlled from a single screen. tmux may be detached from a screen and continue running in the background, then later reattached.
# For installing tmux
```shell
sudo pacman -S tmux
```
# For creating new tmux session
```shell
tmux
```
**NOTE**: The default prefix key is `Ctrl+B`.
# Keybinds
| Keybinding                        | Used                                                                 |
| --------------------------------- | -------------------------------------------------------------------- |
| `Ctrl+b d`                        | To detach from tmux session                                          |
| `Ctrl+b c`                        | To create a new terminal window                                      |
| `Ctrl+b %`                        | To create a split pane vertically                                    |
| `Ctrl+b "`                        | To create a split pane horizontally                                  |
| `Ctrl+b (Arrow Keys)`             | To move between pane                                                 |
| `Ctrl+b q (Index Number)`         | To jump to indexed pane                                              |
| `Ctrl+b [Hold Ctrl] (Arrow Keys)` | To resize the size of pane                                           |
| `Ctrl+b [Hold Alt] (1-5)`         | To use predefined layouts                                            |
| `Ctrl+b n`                        | To change window from left to right                                  |
| `Ctrl+b ,`                        | To change the name of the window                                     |
| `Ctrl+b (Window Number)`          | To jump to window                                                    |
| `Ctrl+b w`                        | To list windows to jump to                                           |
| `Ctrl+b x`                        | To kill pane                                                         |
| `Ctrl+b &`                        | To kill window                                                       |
| `Ctrl+b [`                        | To enter vi copy mode. NOTE: Use `Enter` key to confirm copying text |
| `Ctrl+b z`                        | To zoom-in in a single pane                                          |
| `Ctrl+b !`                        | To change pane to a seperate window                                  |
# For listing tmux session
```shell
tmux ls
```
# For attaching to most recent tmux session
```shell
tmux attach
```
OR,
```shell
tmux a
```
# For attaching to any tmux session
```shell
tmux ls
```
- Note the session name you want to attach
```shell
tmux attach -t <session name>
```
OR,
```shell
tmux a -t <session name>
```
# For detaching to tmux session
```shell
tmux detach
```
# For killing any tmux session
```shell
tmux kill-session -t <session name>
```
NOTE: `tmux kill-session` command only kills the most recent session.
# For killing all tmux session (not tested)
```shell
tmux kill-server
```
# For naming a new tmux session
```shell
tmux new -s <name>
```
NOTE: Change `<name>` to whatever you like.
# Bash scripting notes
- Use `tmux has-session -t <session name> 2>/dev/null` to check if the session exists.
- Use `tmux attach-session -t <session name>` to re-attach to existing session.
- Use `tmux new-session -d -s <session name> -n "<window name>"` to create a new session.
# Plugin
tmux source ~/.config/tmux/tmux.conf
https://github.com/tmux-plugins/tpm
### Key bindings
- `prefix + Ctrl-s` - save
- `prefix + Ctrl-r` - restore