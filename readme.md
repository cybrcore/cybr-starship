<img src="https://raw.githubusercontent.com/cybrcore/cybrcore/refs/heads/main/assets/repo-banners/cybr-starship-banner-top.png"/>

# Showcase
<img src="https://raw.githubusercontent.com/cybrcore/cybrcore/refs/heads/main/assets/showcase/cybr-starship.png"/>
<p align="center">
  <em>starship ↗ (left to right: terminal, terminal, directory, git)</em>
</p>

# Steps
## 0. Before you start
- Make sure [Geist Mono Nerd Font](https://www.nerdfonts.com/font-downloads) is installed, you can do that from terminal with:
```bash
curl -L https://github.com/ryanoasis/nerd-fonts/releases/latest/download/GeistMono.zip -o GeistMono.zip
mkdir -p ~/.local/share/fonts
unzip GeistMono.zip -d ~/.local/share/fonts/GeistMono
fc-cache -fv
```
- Make sure fish is installed: `sudo pacman -S fish` with [cybrcore theme](https://github.com/cybrcore/cybr-fish) and config applied
- See [Installation Guide](https://github.com/cybrcore/cybrdots/blob/main/INSTALL.md) if you're coming from [cybrdots](https://github.com/cybrcore/cybrdots) and haven't set up prerequisites yet
- [starship Github](https://github.com/starship/starship)

## 1. Create config file

```sh
micro ~/.config/starship.toml
```
## 2. Insert [cybrcore theme](../starship/cybrcore.toml) inside starship.toml

## 3. Enable transcience in fish
### Open config.fish
```sh
micro ~/.config/fish/config.fish
```
### Insert at the end:
```json
enable_transience
function starship_transient_prompt_func
  starship module character
end
function starship_transient_rprompt_func
  starship module custom.transient_time
end
starship init fish | source
```
### Restart 
```sh
exec fish
```

## 4. Test

```bash
which starship
starship explain
starship print-config | head -n 5

# Should explain and display starship.toml config

#### If not

echo $STARSHIP_CONFIG

# Should point to ~/.config/starship.toml

#### Then run:

set -gx STARSHIP_CONFIG ~/.config/starship.toml
starship init fish | source
```
