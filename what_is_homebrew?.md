Updating Your Git Using Homebrew
===

An outdated version of Git can leave users vulnerable to security breaches, due to outdated software. That is why it is a good idea to update your Git.

#### Check your version of Git

`$ git --version`

If your terminal displays the following, then you are using Apple's Git.

`git version 1.9.3 (Apple Git-50)`

#### How to Update Git

Install Hombrew by copying and pasting the following into your terminal window:

`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

After the homebrew installed, type the following:

`brew install git`

After, set your path to the local git distro instead of the Apple one:

`export PATH=/usr/local/bin:$PATH`

Check your git version:

`git --version`

Lastly, to update git in the future, all you will need to do is run the followin command:

`brew upgrade git`

Hope this helps