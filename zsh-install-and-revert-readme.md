# Zsh Installation with Auto-completion, Powerlevel10k Theme, and Reverting to Bash

This guide provides instructions for installing Zsh with enhanced auto-completion features, the Powerlevel10k theme, and reverting back to Bash if needed.

## Install Zsh and Set Up Auto-completion with Powerlevel10k Theme

### Manual Steps

1. Install Zsh and Git:
   ```
   sudo apt install -y zsh git
   ```

2. Install Oh My Zsh:
   ```
   sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   ```

3. Install zsh-autocomplete plugin:
   ```
   git clone https://github.com/marlonrichert/zsh-autocomplete.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autocomplete
   ```

4. Install Powerlevel10k theme:
   ```
   git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
   ```

5. Edit ~/.zshrc to add the plugin, configurations, and set the theme:
   ```
   sed -i 's/plugins=(/plugins=(zsh-autocomplete /' ~/.zshrc
   sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="powerlevel10k\/powerlevel10k"/' ~/.zshrc
   echo 'zstyle ":autocomplete:*" default-context history-incremental-search-backward' >> ~/.zshrc
   echo 'zstyle ":autocomplete:*" min-input 1' >> ~/.zshrc
   echo 'setopt HIST_FIND_NO_DUPS' >> ~/.zshrc
   ```

6. Set Zsh as default shell:
   ```
   chsh -s $(which zsh)
   ```

7. Restart your terminal or run:
   ```
   source ~/.zshrc
   ```

### Automated Script

Save the following as `install_zsh_auto_p10k.sh`:

```bash
#!/bin/bash

# Install Zsh and Git
sudo apt install -y zsh git

# Install Oh My Zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended

# Install zsh-autocomplete plugin
git clone https://github.com/marlonrichert/zsh-autocomplete.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autocomplete

# Install Powerlevel10k theme
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

# Add plugin, configurations, and set theme in .zshrc
sed -i 's/plugins=(/plugins=(zsh-autocomplete /' ~/.zshrc
sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="powerlevel10k\/powerlevel10k"/' ~/.zshrc
echo 'zstyle ":autocomplete:*" default-context history-incremental-search-backward' >> ~/.zshrc
echo 'zstyle ":autocomplete:*" min-input 1' >> ~/.zshrc
echo 'setopt HIST_FIND_NO_DUPS' >> ~/.zshrc

# Set Zsh as default shell
chsh -s $(which zsh)

echo "Zsh installed with auto-completion and Powerlevel10k theme. Please log out and log back in for changes to take effect."
echo "After logging back in, run 'p10k configure' to set up your Powerlevel10k theme."
```

## Revert to Bash

[The revert to Bash section remains unchanged]

## Usage

1. To install Zsh with auto-completion and Powerlevel10k theme:
   ```
   chmod +x install_zsh_auto_p10k.sh
   ./install_zsh_auto_p10k.sh
   ```

2. To revert to Bash:
   ```
   chmod +x revert_to_bash.sh
   ./revert_to_bash.sh
   ```

Note: Always review scripts before running them. These scripts will prompt for your password when necessary.

After installing Zsh with Powerlevel10k, you'll need to configure the theme. The first time you open a new terminal after installation, you'll be prompted to configure Powerlevel10k. If not, you can manually start the configuration wizard by running:

```
p10k configure
```

This will guide you through setting up your preferred Powerlevel10k configuration.
