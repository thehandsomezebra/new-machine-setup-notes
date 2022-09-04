# First Time Setup of ubuntu

> Notes taken on Sept 4, 2022 22.04 LTS (Jammy). 

- upon minimal install of ubuntu... 
    - time zone has already been selected
    - internet connection has been established

    - SKIP online accounts
    - SKIP live patch
    - SKIP help improve ubuntu
    - SKIP welcome to ubuntu (privacy)


# things to figure out later:

- What does it take to run remnux VM? 
  - Oh, that will not run on arm or mac.. so just x86.





# commands to run:

```

###########
sudo apt update
###########

###########
# The following block of code is from 
# https://brave.com/linux/
# We can parse this down later.

sudo apt install apt-transport-https curl
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list

sudo apt update
sudo apt install brave-browser
###########




###########
# The following is from 
# https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-sublime-text-on-ubuntu-22-04.html
# to install sublime text

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/sublimetext-keyring.gpg] https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt update
sudo apt install -y sublime-text


# later, I can have it do -- if installed already, then update it using this:
# sudo apt update
# sudo apt --only-upgrade sublime-text
###########



###########

# install git
# oh, by the way... -q is quiet. -qq is quiet with assume -y yes

sudo apt-get -qq install git
git config --global user.email "YourEmail@gmail.com"
git config --global user.name  "YOUR NAME"

###########




###########

#this will always get the latest stable release

dl_url=$( curl -s https://api.github.com/repos/obsidianmd/obsidian-releases/releases/latest  \
    | grep "browser_download_url.*snap" | tail -n 1 | cut -d '"' -f 4 )

curl --location --output Obsidian.snap "$dl_url"
sudo snap install --dangerous Obsidian.snap

## We need the --dangerous, because it flags things
# as dangerous for anything from the internet

###########



###########


#make a key for github

ssh-keygen -t ed25519 -C `git config --get user.email` -f /home/`whoami`/.ssh/github

#now output the public

cat  /home/`whoami`/.ssh/github.pub

#open this link
# https://github.com/settings/keys
# and paste in that public


###########


```