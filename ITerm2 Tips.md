# iterm2 Tips

## 美化iterm2

### Powerlevel9k 
   [Powerlevel9k is a theme for ZSH which uses Powerline Fonts](https://github.com/bhilburn/powerlevel9k)

   [ShowOffYourConfig](https://github.com/bhilburn/powerlevel9k/wiki/Show-Off-Your-Config)

#### Installation Instructions

* Install the Powerlevel9k Theme

    > $ git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k

You then need to select this theme in your ~/.zshrc:
    
    > ZSH_THEME="powerlevel9k/powerlevel9k"

* Install Powerline Fonts

    >$ brew tap caskroom/fonts
    
    >$ brew cask install font-meslo-nerd-font

    配置defaultshell 选择NerdFont

 * MyConfig

    ```
    POWERLEVEL9K_MODE='nerdfont-complete'
    #POWERLEVEL9K_MODE='awesome-patched'
    POWERLEVEL9K_SHORTEN_DIR_LENGTH=2
    #POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(os_icon dir vcs)
    POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(os_icon context dir dir_writable vcs vi_mode)
    #POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status nvm node_version)
    POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status background_jobs history ram load time)
    DEFAULT_USER="zhanghui"

    POWERLEVEL9K_OS_ICON_BACKGROUND="white"
    POWERLEVEL9K_OS_ICON_FOREGROUND="blue"
    POWERLEVEL9K_DIR_HOME_FOREGROUND="white"
    POWERLEVEL9K_DIR_HOME_SUBFOLDER_FOREGROUND="white"
    ```