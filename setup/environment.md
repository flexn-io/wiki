# Installation Guide

Supported OS: `macos`, `windows-WIP`, `linux-WIP`

This guide assumes:

- you have vanilla macos setup
- you will use `~/.zshrc` as the only bash profile file (recomended)
- you're running macOS 11.6 or higher

NOTE: You can still configure system via cherrypicking but the final results may vary.

Tested on:

- Mac, Intel, 11.6
- Mac, M1, 12.2.1

# LEVEL 1 - Generic Developer

Open Terminal

## Update System

```
softwareupdate --all --list
```

if you happy:

```
softwareupdate --all --install
```

## Install Rosetta (M1 Only)

```
softwareupdate --install-rosetta
```

## Bash

https://mac.install.guide/ruby/1.html

```
touch ~/.zshrc
```

## Install Xcode Tools

https://mac.install.guide/ruby/2.html

```
sudo xcode-select --install
```

CHECK

```
xcode-select -p
```

## Install Brew

https://mac.install.guide/ruby/3.html

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

If promted by brew:

```
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc

source ~/.zshrc
```

CHECK

```
brew doctor
```

## Install Java (15.0.2)

```
cd ~/Downloads

curl https://download.java.net/java/GA/jdk15.0.2/0d1cfde4252546c6931946de8db48ee2/7/GPL/openjdk-15.0.2_osx-x64_bin.tar.gz -o openjdk-15.0.2_osx-x64_bin.tar.gz

sudo mv openjdk-15.0.2_osx-x64_bin.tar.gz /Library/Java/JavaVirtualMachines/

cd /Library/Java/JavaVirtualMachines/

sudo tar -xzf openjdk-15.0.2_osx-x64_bin.tar.gz

sudo rm openjdk-15.0.2_osx-x64_bin.tar.gz

/usr/libexec/java_home -v15

echo -n "\nexport JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-15.0.2.jdk/Contents/Home" >> ~/.zshrc

source ~/.zshrc
```

CHECK

```
java -version
```

## Configure Git

https://mac.install.guide/ruby/4.html

```
git config --global user.name "YOUR_NAME"
git config --global user.email "YOUR_EMAIL"
```

CHECK

```
git config -l --global
```

```
ssh-keygen -t ed25519 -C "YOUR_EMAIL"
```

Navigate to:

https://github.com/settings/keys

```
pbcopy < ~/.ssh/id_ed25519.pub
```

CHECK

```
ssh -T git@github.com
```

## ASDF Version Manager (Ruby, Node)

We moved from nvm to asdf due to some issues running react-native in nvm setup

```
brew install asdf

echo -e "\n. $(brew --prefix asdf)/libexec/asdf.sh" >> ~/.zshrc

source ~/.zshrc
```

CHECK

```
asdf --version
```

Add support for legacy setups:

```
echo "legacy_version_file = yes" >> ~/.asdfrc
```

## Install Ruby (3.1.1)

```
asdf plugin add ruby

asdf install ruby 3.1.1

asdf global ruby 3.1.1

source ~/.zshrc
```

CHECK

```
ruby -v
```

Optimise gem sizes:

```
echo "gem: --no-document" >> ~/.gemrc
```

## Install NodeJS (16.14.0)

```
asdf plugin add nodejs

asdf install nodejs 16.14.0

asdf global nodejs 16.14.0

source ~/.zshrc
```

Add additional label pointing to same version:

```
asdf install nodejs lts-gallium

source ~/.zshrc
```

CHECK

```
node -v
```

## Install Cocoapods (1.11.2)

```
gem install cocoapods -v 1.11.2

source ~/.zshrc
```

CHECK

```
pod --version
```

# LEVEL 2 - ReNative Developer

## Install Yarn

Unlocks `-p` : `web`, `chromecast`

```
npm i yarn -g
```

## Install Android Studio

Unlocks `-p` : `android`, `androidtv`, `androidwear`

https://developer.android.com/studio

Open, Install, Setup

## Install Xcode

Unlocks `-p` : `ios`, `tvos`, `macos`

https://apps.apple.com/us/app/xcode/id497799835

Open, Install, Setup

## Install Tizen Studio

Unlocks `-p` : `tizen`, `tizenwatch`, `tizenmobile`

https://developer.tizen.org/development/tizen-studio/download

Download, Open, Install, Setup

## Install WebOS SDK

Unlocks `-p` : `webos`

https://webostv.developer.lge.com/sdk/webos-tv-sdk/introduction/

Download, Open, Install, Setup

## Setup ReNative

```
git clone git@github.com:renative-org/renative.git

yarn bootstrap
```

Run Some apps

```
cd packages/renative-template-hello-world

rnv run -p web

rnv run -p android

rnv run -p ios
```

# LEVEL 3 - Pro Developer

NOTE: Opinionated tools, extensions & customisations (NOT manadatory)

## Bash shortcuts

Update `~/.zshrc`

```
alias f="open ."
alias v="code ."
alias sz="source ~/.zshrc"
alias yb="yarn bootstrap"
alias yw="yarn watch"
alias ybc="yarn bootstrap-clean"
alias s="/Applications/SourceTree.app/Contents/Resources/stree"
```

## Install iTerm

Better terminal

https://iterm2.com/downloads.html

### Install oh-my-zsh

IMPORTANT: Copy contents of your `~/.zshrc`

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

Open `~/.zshrc` => paste contents at the top of the file

Close => Reopen iTerm

## Install Spectacle

Manage your screen real estate via shortcuts

https://www.spectacleapp.com/

## Install VSCode

Better IDE

https://code.visualstudio.com/download

Enable Terminal Integration

```
CMD+Shift+P => shell command
```

### Install VS Extensions:

```
Atom One Dark Theme
VS Code ESLint extension
Minimal Icon Theme
GitLens
```

### Configure Settings

CMD+SHift+P => Open Settins (JSON) =>

```
{
    "editor.formatOnSave": true,
    "workbench.colorTheme": "Atom One Dark",
    "workbench.tree.indent": 16,
    "atomKeymap.promptV3Features": true,
    "editor.multiCursorModifier": "ctrlCmd",
    "editor.formatOnPaste": true,
    "editor.codeActionsOnSave": {
        "source.fixAll": true,
        "source.organizeImports": false,
    },
    "explorer.confirmDragAndDrop": false,
    "workbench.iconTheme": "minimal-icon-theme",
    "editor.scrollBeyondLastLine": false,
    "eslint.format.enable": true,
    "security.workspace.trust.untrustedFiles": "open",
    "explorer.confirmDelete": false
}
```

## Install Docker

https://docs.docker.com/desktop/mac/install/

Open, Configure

CHECK

```
docker -v
```
