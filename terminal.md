# My ubuntu terminal & shell

## Shell - fish

I use [fish](https://fishshell.com) - **f**riendly **i**nteractive **sh**ell.

```sh
# Install fish
sudo apt install fish 

# Change fish to default shell
chsh -s `which fish`

# Turn off welcome message
fish
set -U fish_greeting ""

# Configure fish
fish_config
```

I use Lava color schema and Screen Savvy prompt.


## Terminal - terminator

I use [terminator](https://github.com/gnome-terminator/terminator)

My config in `~/.config/terminator/config`
```
[global_config]
  always_split_with_profile = True
[keybindings]
[profiles]
  [[default]]
    cursor_color = "#aaaaaa"
  [[mrucznik]]
    background_color = "#300a24"
    background_darkness = 0.8
    background_type = transparent
    cursor_color = "#aaaaaa"
    foreground_color = "#ffffff"
[layouts]
  [[default]]
    [[[window0]]]
      type = Window
      parent = ""
      profile = mrucznik
    [[[child1]]]
      type = Terminal
      parent = window0
      profile = mrucznik
[plugins]
```

### Shortcuts
List of most usefull terminator shortcuts:
| Shortcut | Action |
| -------- | ------ |
| `Alt + arrows` | Move focus |
| `(Shift) + Ctrl + Tab` | Cycle to terminal |
| `Ctrl + Page Up/Down` | Switch tab |

TODO: write some more from https://terminator-gtk3.readthedocs.io/en/latest/gettingstarted.html and https://pl.euro-linux.com/blog/terminator-efektywny-i-prosty-emulator-terminala/
