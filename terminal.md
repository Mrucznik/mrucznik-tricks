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

To configure properly with snap installed jetbrains ide's and workaround error: `error: Unable to open universal variable file '/snap/goland/135/plugins/terminal/fish/fish_variables': Read-only file system`, go to `File->Settings->Tools->Terminal` and changing `Shell Path` to /usr/bin/jetbrains_fish. After that, run:
```sh
sudo echo '#!/bin/sh\
if [ -n "$OLD_XDG_CONFIG_HOME" ]; then\
  export XDG_CONFIG_HOME="$OLD_XDG_CONFIG_HOME"\
else\
  unset XDG_CONFIG_HOME\
fi\
exec fish' > /usr/bin/jetbrains_fish
sudo chmod +x /usr/bin/jetbrains_fish
```
Credits to Alastair Knowles, https://youtrack.jetbrains.com/issue/IDEA-169111


## Terminal - terminator

I use [terminator](https://github.com/gnome-terminator/terminator)
```sh
# Installation
sudo apt install terminator

# Set as default terminal
sudo update-alternatives --config x-terminal-emulator

# Set 'Open in Terminal' on desktop to open terminator
gsettings set org.gnome.desktop.default-applications.terminal exec terminator

# Set 'Open in Terminal' in Nautilus to open terminator
sudo apt install python3-nautilus python3-yaml
mkdir -p $HOME/.local/share/nautilus-python/extensions
cd $HOME/.local/share/nautilus-python/extensions
wget https://raw.githubusercontent.com/mwahlroos/Nautiterm/master/src/nautiterm/open_terminal.py
sed -i "s/DEFAULT_TERMINAL_EXEC = 'gnome-terminal'/DEFAULT_TERMINAL_EXEC = 'terminator'/g" open_terminal.py
sudo apt remove nautilus-extension-gnome-terminal
nautilus -q
```

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
