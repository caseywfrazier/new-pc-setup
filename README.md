# new-pc-setup

## HOW TO SET UP FANCY TERMINAL

### links
---
- [video](https://www.youtube.com/watch?v=VT2L1SXFq9U&t=1345s)

- [blog post](https://www.hanselman.com/blog/my-ultimate-powershell-prompt-with-oh-my-posh-and-the-windows-terminal)

- [oh my posh docs](https://ohmyposh.dev/docs/)


### install/download stuff
---
1. install winget (if you don't already have it)
   - install "App Installer" from windows store OR
   - install from [github releases](https://github.com/microsoft/winget-cli/releases)
1. install vscode
   >`winget install vscode`
1. (optional) install terminal
   >`winget install terminal --source winget`
1. install powershell core: windows store/winget/github/etc
   >`winget install powershell --source winget`

1. dl/install [nerdfont](https://github.com/ryanoasis/nerd-fonts/releases)
   - CascadiaCode.zip
   - CascaydiaCoveNerdFont-Regular
   - Terminal: Settings -> Profiles -> Defaults -> Font face

1. install ohmyposh
   >`Install-Module oh-my-posh -Scope CurrentUser`
   
   OR
   >`winget install JanDeDobbeleer.OhMyPosh`
1. restart PC - to ensure PATH var changes and new fonts are accessible by all programs

### test ohmyposh executable
---
1. configure font settings for Powershell in Terminal to use `CaskaydiaCove NF`
1. to test if the omp exe was successfully added to the $PATH variable, run
    >`oh-my-posh.exe`

### configure psh terminal to use omp with nerdfont
---

1. edit powershell to use omp exe instead of default prompt

   - create profile psh directory
      >`New-Item -ItemType Directory -Force -Path $(Split-Path -Path $profile -Parent)`
   - create profile psh file
      >`New-Item -ItemType File -Force -Path $profile`
   - confirm file exists (`Microsoft.PowerShell_profile.ps1`)
      >`cd $(Split-Path -Path $profile)`
      
      >`dir -File`
   - open in vscode
      >`code -r $profile`
   - add this line and save
      >`oh-my-posh --init --shell pwsh --config "~\AppData\Local\Programs\oh-my-posh\themes\jandedobbeleer.omp.json"  | Invoke-Expression`
   - restart shell to verify it's working
1. edit vscode to use the new font
   - close/open vscode to get new psh terminal settings
   - open file->preferences->settings, search for font
     - set Font family = 
        >`CaskaydiaCove NF`

### extras
---

#### add extra terminal icons
---
1. install the module
    >`Install-Module -Name Terminal-Icons -Repository PSGallery`
1. import the module when the shell loads
    - add this line to your $profile file
        >`Import-Module -Name Terminal-Icons`

#### cd alternative
- this module is an alternative to cd "change-directory" that learns common paths
>`Install-Module z -AllowClobber`

#### other terminal settings
- change transparency
      
   >Cntrl + Shift + Scroll

   OR
   >`"useAcrylic": true,`

   >`"acrylicOpacity": 0.01`

Others:

>`"useAcrylicInTabRow": true,`

>`"theme": "system",`

>`showTabsInTitlebar": true`

#### extra powershell profile settings
---
1. custom ohmyposh settings
   - customize the omp config file
        - can use [this gist](https://gist.github.com/shanselman/1f69b28bfcc4f7716e49eb5bb34d7b2c?WT.mc_id=-blog-scottha) as a reference
1. argument completers, etc
   - copy from this [github gist](https://gist.github.com/shanselman/25f5550ad186189e0e68916c6d7f44c3)
   - how to get psreadline beta (if still needed)
       >`Find-Module PSReadline -AllowPrerelease`

       >`Install-Module -Name PSReadLine -RequiredVersion 2.2.0-beta3 -AllowPrerelease`
