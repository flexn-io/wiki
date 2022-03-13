# Windows

> ReNative currently uses Electron for windows application development, react-native-windows engine is being developed, but it's not yet ready for release.

## Electron 

Electron is fairly powerfull tool, which allows to merge your website code and code you would write for a desktop application into one or create a desktop application in the same way you would create a website. There are many famous aplications that use this technology (for instance Visual Studio Code or Skype), but it's purpose is to serve as a cross platform tool to convert your website into a desktop app.

Docs reference https://www.electronjs.org/

## React Native Windows

React Native Windows is a tool developed, maintained and heavily used by Microsoft for Windows application development. As an example most native apps, that come with Windows installation, such as Calendar, Mail are built using React Native Windows. Unlike Electron this tool brings better performance and lighter applications as the generated code is native to windows platform. React native windows blog also mentioned that designers prefer native applications over cross platform ones, but this advantage is too small and subjective to be counted as one.

Docs reference https://github.com/microsoft/react-native-windows

### Additional setup required for development

React Native Windows requires a Windows machine first and foremost to build and run the applications, however to do so a few more steps need to be taken:

- Go to Developer Settings in the settings menu and turn on 'Developer Mode'

- [Download Visual Studio](https://visualstudio.microsoft.com/vs/community/) and then using Visual Studio Installer install Visual Studio 2019 Community Edition, When installing make sure to also check:
    - 'Universal Windows Platform Development and then on the right hand side also tick the 'C++ (v142) Universal Windows Platform tools.
    - 'Desktop Development with C++'
    - '.NET desktop development'
    - Under 'Individual components' tab (top of the installer window) scroll down to 'Development activities' and tick 'Node.js development tools'

- Enable long path support. This can be done with command in a PowerShell window (as per [Microsoft docs](https://docs.microsoft.com/en-us/windows/win32/fileio/maximum-file-path-limitation?tabs=powershell)):
```
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force
```
To validate your setup you can run the command provided by [React Native Windows documentation](https://microsoft.github.io/react-native-windows/docs/rnw-dependencies) in your PowerShell window:
```
Set-ExecutionPolicy Unrestricted -Scope Process -Force; iex (New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/microsoft/react-native-windows/master/vnext/Scripts/rnw-dependencies.ps1')
```
> The validation command can set and install dependencies, but it's better to do it manually as it failed to execute a few steps and wasn't as easy to debug.

TODO Describe additional modules installation and typical development process
