# Instalation

## First step => Download and install Hack NF

Download and install Hack NF font from [nerd-fonts](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/Hack/Regular/complete/Hack%20Regular%20Nerd%20Font%20Complete%20Mono%20Windows%20Compatible.ttf)

## Second step

```powershell
Set-ExecutionPolicy Unrestricted
Install-Module PSReadLine -Force -SkipPublisherCheck -AllowPrerelease
Install-Module posh-git -Force -SkipPublisherCheck -AllowPrerelease
Install-Module oh-my-posh -Force -SkipPublisherCheck -AllowPrerelease
Install-Module -Name Terminal-Icons -Repository PSGallery

Import-Module posh-git
Import-Module oh-my-posh
Import-Module -Name Terminal-Icons
Set-PoshPrompt slim

Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete
Set-PSReadLineOption -PredictionSource History

# this will override your current profile, so if you have something custom, do not execute it.
$sb = New-Object -TypeName System.Text.StringBuilder
$sb.AppendLine("Import-Module posh-git");
$sb.AppendLine("Import-Module oh-my-posh");
$sb.AppendLine("Import-Module -Name Terminal-Icons");
$sb.AppendLine("Set-PoshPrompt slim");
$sb.AppendLine("");
$sb.AppendLine("Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete");
$sb.AppendLine("Set-PSReadLineOption -PredictionSource History");

$sb.ToString() | Out-File -FilePath $profile
```

Then restart your powershell terminal

## Third step

Enable dotnet-suggestion

Follow the tutorial: https://github.com/dotnet/command-line-api/blob/main/docs/dotnet-suggest.md
