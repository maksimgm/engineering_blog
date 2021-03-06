Updating Your Git Using Homebrew
===

An outdated version of Git leaves users vulnerable to security breaches. Therefore, it is a good idea to update your Git using Homebrew. Homebrew is an open source management system that simplifies the installation of software on Mac OS X. [Wikipedia](http://en.wikipedia.org/wiki/Homebrew_(package_management_software) In essence, Homebrew installs the stuff that Apple didn't.

How to install Homebrew:

#### Check your version of Git

	$ git --version

If your terminal displays the following, then you are using Apple's Git:

	git version 1.9.3 (Apple Git-50)

#### How to Update Git

Install Homebrew by copying and pasting the following code into your terminal window:

	ruby -e "$(curl -fsSL https://	raw.githubusercontent.com/Homebrew/install/master/instal`l)"

After Homebrew is installed, type:

	brew install git

After, set your path to the local git distribution instead of the Apple one:

	export PATH=/usr/local/bin:$PATH

Check your git version:

	git --version

Lastly, to update git in the future, all you need to do is run the following command:

	brew upgrade git
	
Note: If Git is up to date then your terminal will inform you that the latest  Git version is installed.

Stay up to date and happy coding