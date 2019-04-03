# App Academy Ruby 2.3.1 Installation

```
# install rbenv
brew install rbenv

# add to the PATH (rbenv commands are now available from terminal)
# .bashrc is the file that contains all of our terminal settings
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc

# initialize rbenv everytime you open a new console window
echo 'eval "$(rbenv init -)"' >> ~/.bashrc

# update current console window with new settings
source ~/.bashrc

# source .bashrc from .bash_profile (necessary on some machines)
echo 'source ~/.bashrc' >> ~/.bash_profile

# install Ruby version 2.4.6
rbenv install 2.4.6

# set version 2.4.6 to be our global default
rbenv global 2.4.6

# the 'rehash' command updates the environment to your configuration
rbenv rehash

# and let's verify everything is correct
# check the version
ruby -v        # => 2.4.6

# check that we are using rbenv's version of ruby
which ruby     # => /Users/your-username/.rbenv/shims/ruby
```

## Install Gems

```
gem install bundler pry byebug
```

## ~/.rspec

Create a `.rspec` file in the home directory and insert the following

```
--format documentation --color
--format documentation
--order=default
```
