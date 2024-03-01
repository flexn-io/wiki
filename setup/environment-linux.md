# Installation Guide

Supported OS: `macos`, `windows-WIP`, `linux`

This guide assumes:

- you have vanilla linux setup
- you're running Ubuntu 22.04 or higher

NOTE: You can still configure system via cherrypicking but the final results may vary.

Tested on:

- Ubuntu, 22.04.4

# LEVEL 1 - Generic Developer

Open Terminal as root

## Update System

```
sudo apt update
```

if you happy:

```
sudo apt upgrade -y
```

## Install CURL

```
sudo apt install curl -y
```

### Install Node Version Manager (NVM)

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```

Activate NVM

```
source ~/.bashrc
```

CHECK

```
nvm -v
```

## Install NodeJS (18.19.0)

```
nvm install 18.19.0
```

Make it default node version with NVM

```
nvm alias default 18.19.0
```

CHECK

```
node -v npm -v
```

## Install Git

```
sudo apt-get install git-all
```
To configurate Git follow official guide:

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux

## Install Ruby

```
sudo apt-get install ruby-full
```

CHECK

```
ruby -v
```

## Install Python

```
sudo apt-get install python3
```

CHECK

```
python3 --version
```

# LEVEL 2 - ReNative Developer

## Install Yarn

Unlocks `-p` : `web`, `chromecast`

```
npm i -g yarn
```

## Install Lerna

```
npm i lerna@6.6.2 -g
```

## Install Android Studio

Unlocks `-p` : `android`, `androidtv`, `androidwear`

https://developer.android.com/studio

Open, Install, Setup

## Install Tizen Studio

Unlocks `-p` : `tizen`, `tizenwatch`, `tizenmobile`

https://developer.tizen.org/development/tizen-studio/download

Download, Open, Install, Setup

## Install WebOS SDK

Unlocks `-p` : `webos`

https://webostv.developer.lge.com/develop/tools/sdk-introduction/

Download, Open, Install, Setup

## Setup ReNative

```
git clone git@github.com:renative-org/renative.git

yarn bootstrap
```

Run Some apps

```
cd packages/template-starter

rnv run -p web

rnv run -p android
```
