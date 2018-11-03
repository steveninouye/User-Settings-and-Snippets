# Mac OS X Setup

## Applications

-   Google Chrome
-   Visual Studio Code
-   Atom
-   Discord
-   Slack
-   WeChat
-   WhatsApp

---

## Terminal Software

### Xcode

```
xcode-select --install
```

### Homebrew

-   Get Homebrew at [https://brew.sh](https://brew.sh/)
-   After installing Homebrew install wget

```
 brew install wget
```

### Git

```
# install git
brew install git

# makes git terminal output pretty
git config --global color.ui true

# this will mark you as the 'author' of each committed change
git config --global user.name "your name here"

# use the email associated with your GitHub account
git config --global user.email your_email_here
```

#### Generating a new SSH key

![](ssh_key_gen.png)
![](new_ssh_agent.png)
![](add_gh_ssh_key.png)

### Fonts

```
# install fonts
brew tap caskroom/fonts
brew cask install font-fira-code
brew cask install font-inconsolata
```

---

## ~/.bashrc
```
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

## ~/.aliases
```
alias ga="git add"
alias gc="git commit -m"
# alias gac="git add -A && git commit -m "
alias gp="git push"
alias bsp="bundle exec rspec"


# gitauthor "Steven Inouye" "steveninouye@msn.com"

function git_change_authorship {
  git filter-branch -f --env-filter "
    GIT_AUTHOR_NAME=\"$1\"
    GIT_AUTHOR_EMAIL=\"$2\"
    GIT_COMMITTER_NAME=\"$1\"
    GIT_COMMITTER_EMAIL=\"$2\"
  "
}
alias gitauthor=git_change_authorship


function make_and_change_directory {
  case "$1" in
    */..|*/../) cd -- "$1";; # that doesn't make any sense unless the directory already exists
    /*/../*) (cd "${1%/../*}/.." && mkdir -p "./${1##*/../}") && cd -- "$1";;
    /*) mkdir -p "$1" && cd "$1";;
    */../*) (cd "./${1%/../*}/.." && mkdir -p "./${1##*/../}") && cd "./$1";;
    ../*) (cd .. && mkdir -p "${1#.}") && cd "$1";;
    *) mkdir -p "./$1" && cd "./$1";;
  esac
}
alias mkcd=make_and_change_directory
```

## ~/.bash_profile

Create a `.bash_profile` in home directory and insert code inside.

_More Information to Customize Terminal Color at [Marina Mele's Site](http://www.marinamele.com/2014/05/customize-colors-of-your-terminal-in-mac-os-x.html)_

```
export CLICOLOR=1
export LSCOLORS=Gxheahdhfxegedabagacad
parse_git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\u@\h \W\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
PS1="\[\e[45m\]\[\e[37m\]💰 \d \A \h[\[\e[4;37m\]\u\[\e[0;37m\]\[\e[45m\]]: \w\[\e[3;37m\]\[\e[44m\]\$(parse_git_branch)\[\e[45m\] 💰\[\e[0m\]\n💰"
source ~/.bashrc
source ~/.aliases
```

Run `.bash_profile`. In terminal run

```
source ~/.bash_profile
```

---

## Terminal

```
# terminal default colors
BACKGROUND = black
TEXT = flora
BOLD TEXT = black # default
SELECTION = iron

# customize terminal color
## terminal font
Monaco 12 pt

## terminal preferences
Display ANSI colors  # check the box
```
