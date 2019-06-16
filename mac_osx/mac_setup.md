# Mac OS X Setup

## Applications

- Google Chrome
- Visual Studio Code
- Discord
- Slack
- WeChat
- WhatsApp

---

## Terminal Software

### Xcode

```bash
xcode-select --install
```

### Homebrew

- Get Homebrew at [https://brew.sh](https://brew.sh/)
- After installing Homebrew install wget

```bash
 brew install wget
```

### Git

```bash
# install git
brew install git

# makes git terminal output pretty
git config --global color.ui true

# this will mark you as the 'author' of each committed change
git config --global user.name "Steven Inouye"

# use the email associated with your GitHub account
git config --global user.email steveninouye@msn.com
```

#### Generating a new SSH key [here](https://help.github.com/en/articles/connecting-to-github-with-ssh)

#### Generating a new SSH key
Open Terminal.

Paste the text below, substituting in your GitHub email address.

```
$ ssh-keygen -t rsa -b 4096 -C steveninouye@msn.com
```

This creates a new ssh key, using the provided email as a label.

```
> Generating public/private rsa key pair.
```

When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

```
> Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```

At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases".

```
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

#### Adding your SSH key to the ssh-agent
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. When adding your SSH key to the agent, use the default macOS ssh-add command, and not an application installed by macports, homebrew, or some other external source.

Start the ssh-agent in the background.
```
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```

If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.

```
$ ssh-add -K ~/.ssh/id_rsa
```

### Fonts

```bash
# install fonts
brew tap caskroom/fonts
brew cask install font-fira-code
brew cask install font-inconsolata
```

---

## ~/.bashrc

```bash
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

## ~/.aliases

```bash
alias ga="git add"
alias gc="git commit -m"
alias gac="git add -A && git commit -m "
alias gp="git push"
alias be="bundle exec"
alias ber="bundle exec rails"

# gitauthor "Steven Inouye" "steveninouye@msn.com"

# function git_change_authorship {
#   git filter-branch -f --env-filter "
#     GIT_AUTHOR_NAME=\"$1\"
#     GIT_AUTHOR_EMAIL=\"$2\"
#     GIT_COMMITTER_NAME=\"$1\"
#     GIT_COMMITTER_EMAIL=\"$2\"
#   "
# }
# alias gitauthor=git_change_authorship


# function make_and_change_directory {
#   case "$1" in
#     */..|*/../) cd -- "$1";; # that doesn't make any sense unless the directory already exists
#     /*/../*) (cd "${1%/../*}/.." && mkdir -p "./${1##*/../}") && cd -- "$1";;
#     /*) mkdir -p "$1" && cd "$1";;
#     */../*) (cd "./${1%/../*}/.." && mkdir -p "./${1##*/../}") && cd "./$1";;
#     ../*) (cd .. && mkdir -p "${1#.}") && cd "$1";;
#     *) mkdir -p "./$1" && cd "./$1";;
#   esac
# }
# alias mkcd=make_and_change_directory
```

## ~/.bash_profile

Create a `.bash_profile` in home directory and insert code inside.

_More Information to Customize Terminal Color at [Marina Mele's Site](http://www.marinamele.com/2014/05/customize-colors-of-your-terminal-in-mac-os-x.html)_

```bash
export CLICOLOR=1
export LSCOLORS=Gxheahdhfxegedabagacad
parse_git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
export PS1="\u@\h \W\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
PS1="\[\e[0;31m\]\h[\u]:\t \[\e[4;37m\]\$(parse_git_branch)\[\e[0;31m\] \W \[\e[0m\]"
source ~/.bashrc
source ~/.aliases
```

Run `.bash_profile`. In terminal run

```bash
source ~/.bash_profile
```

---

## Terminal

```bash
# terminal default colors
BACKGROUND = black
TEXT = white
BOLD TEXT = white # default
SELECTION = iron

# customize terminal color
## terminal font
PT Mono 12pt

## terminal preferences
Display ANSI colors  # check the box

# Red next to black under ANSI Colors
Change to bright red

# Window Tab
## Window Size
Columns: 95
Rows: 36
```
