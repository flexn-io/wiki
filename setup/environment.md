# Installation Guide

This guide assumes you have vanilla macos setup

# LEVEL 1 - GENERIC DEVELOPER

## Install Rosetta

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

## Update System

CHECK

```
xcode-select -p
```

## Install Brew

https://mac.install.guide/ruby/3.html

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

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
ssh-keygen -t ed25519 -C "beherithrone@gmail.com"
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

## Version Manager (Ruby, Node)

```
brew install asdf

echo -e "\n. $(brew --prefix asdf)/libexec/asdf.sh" >> ~/.zshrc

source ~/.zshrc
```

CHECK

```
asdf --version
```

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

```
echo "gem: --no-document" >> ~/.gemrc
```

## Install NodeJS (16.14.0)

```
asdf plugin add nodejs

asdf install nodejs 16.14.0

asdf global nodejs 16.14.0

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
```

CHECK

```
pod --version
```

# LEVEL 2 - RENATIVE DEVELOPER

## Install Yarn

```
npm config set scripts-prepend-node-path true

npm i yarn -g
```

## Install Android Studio

https://developer.android.com/studio

Open, Install, Setup

## Install Xcode

https://apps.apple.com/us/app/xcode/id497799835

Open, Install, Setup

## Setup Renative

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

# LEVEL 3 - PRO DEVELOPER

NOTE: Opinionated extensions (NOT manadatory)

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

https://iterm2.com/downloads.html

### Install oh-my-zsh

IMPORTANT: Copy contents of your `~/.zshrc`

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

Open `~/.zshrc` => paste contents at the top of the file

Close => Reopen iTerm

## Install Spectacle

https://www.spectacleapp.com/

## Install VSCode

https://code.visualstudio.com/download

Enable Terminal

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
