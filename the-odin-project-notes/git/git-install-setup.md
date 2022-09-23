**Setting Up Git** **(Linux)**

Linux Installation shell commands

1) Update the system
```bash
sudo apt update
sudo apt upgrade
```
2) Install git
```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

3) Configure global variables (do this before using Git)

```bash
git config --global init.defaultBranch main 
git --version # version should be 2.28 or newer
git config --global color.ui auto # make it look nicer

# Set your user name and email
git config --global user.name "Your Name"
git config --global user.email "yourname@example.com"

# Verify user info if desired
git config --get user.name
git config --get user.email
```
4) Create an SSH Key

 ```bash
# Run this command first - if you get "No Such File" run the next one
ls ~/.ssh/id_ed25519.pub

ssh-keygen -t ed25519 -C <youremail> # press enter when it prompts to save and skip the passphrase
```

5) Log into Github or create a Github account if necessary. 
	1) Click on profile picture (should get a dropdown) 
	2) Click on Settings in the menu
	3) On the left-hand side, click `SSH and GPG keys`
	4) Click the green button in the top right corner that says `New SSH Key`
	5) In the command line, enter the following command:
	```bash
		cat ~/.ssh/id_ed25519.pub
	```
	6) Add a descriptive title to remember the source of the key
	7) Paste the output of the command into the field and click `Add SSH Key`
	8) Test your SSH Connection
		1) Open Terminal.
		2) Enter the following:
	```shell
	$ ssh -T git@github.com
	# Attempts to ssh to GitHub
	```
		
		
	You may see a warning here - you just want to verify that the fingerprint in the message matches [GitHub's public key fingerprint](https://docs.github.com/en/github/authenticating-to-github/githubs-ssh-key-fingerprints)


	9) If the key matches, press enter and you should be fully authenticated.
		If you get a warning message here "agent admitted failure to sign...", check here:
		[Error: Agent admitted failure to sign"](https://docs.github.com/en/articles/error-agent-admitted-failure-to-sign).
		
		If you see this message, you are good to go:
		**Hi username! You’ve successfully authenticated, but GitHub does not provide shell access**