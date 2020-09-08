# Instalation

## First step => Download and install Hack NF

Download and install Hack NF font from [nerd-fonts](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/Hack/Regular/complete/Hack%20Regular%20Nerd%20Font%20Complete%20Mono%20Windows%20Compatible.ttf)

## Second step

```powershell
Set-ExecutionPolicy Unrestricted
Install-Module PSReadLine -Force -SkipPublisherCheck -AllowPrerelease
Install-Module posh-git -Force -SkipPublisherCheck -AllowPrerelease
Install-Module oh-my-posh -Force -SkipPublisherCheck -AllowPrerelease
Import-Module posh-git
Import-Module oh-my-posh
New-Item $ThemeSettings.MyThemesLocation -ItemType Directory
Invoke-WebRequest https://gist.githubusercontent.com/AlbertoMonteiro/4183020aa6c5d7d0fd8c6af8d0952b9a/raw/e7b1c7eb104442400ecd59069fe03d4bc895a21a/alberto-theme.psm1 -OutFile "$($ThemeSettings.MyThemesLocation)\alberto-theme.psm1"

Set-Prompt alberto-theme

# this will override your current profile, so if you have something custom, do not execute it.
$sb = New-Object -TypeName System.Text.StringBuilder
$sb.AppendLine("Import-Module posh-git");
$sb.AppendLine("Import-Module oh-my-posh");
$sb.AppendLine("Set-Theme alberto-theme");
$sb.AppendLine("Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete");
$sb.AppendLine("Set-PSReadLineOption -PredictionSource History");

$sb.ToString() | Out-File -FilePath $profile
```

Then restart your powershell terminal
