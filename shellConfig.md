


**Dowload Starship:** https://starship.rs/guide/

**Dowload Nerd Fonts:** https://www.nerdfonts.com/

Depois de baixar a fonte abra o powershell e copie esse código para a fonte ser 
adicionada ao computador
```
$key = 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Console\TrueTypeFont'
Set-ItemProperty -Path $key -Name '000' -Value 'LiberationMono NF'
```
Reinicie o powershell, abra de novo, vá em configurações
![App Screenshot](https://github.com/juan-20/juan-20/blob/main/assets/config.png?raw=true)
Clique em windows powershell:
![App Screenshot](https://github.com/juan-20/juan-20/blob/main/assets/powershell.png?raw=true)
Troque a fonte para LiterationMono NF
![App Screenshot](https://github.com/juan-20/juan-20/blob/main/assets/fontChanged.png?raw=true)

Abra seu windows explorer e encontre sua pasta powershell. 
A minha esta em Documentos/Powershell. Se quiser basta digitar $PROFILE no poweshell. Crie o arquivo:
```
Microsoft.PowerShell_profile.ps1
```
e cola isso:

```shell
Invoke-Expression (&starship init powershell)
Import-Module Terminal-Icons

$MaximumHistoryCount = 20000

# Autocomplete
Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete

# Historico
$HistoryFilePath = Join-Path ([Environment]::GetFolderPath('UserProfile')) .ps_history
Register-EngineEvent PowerShell.Exiting -Action { Get-History | Export-Clixml $HistoryFilePath } | out-null
if (Test-path $HistoryFilePath) { Import-Clixml $HistoryFilePath | Add-History }

Set-PSReadLineOption -HistorySearchCursorMovesToEnd
Set-PSReadlineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadlineKeyHandler -Key DownArrow -Function HistorySearchForward

# Essas funções eu personalizei para acessar pastas que sempre acesso
function dowload() { Set-Location "C:\Downloads" }
function programas() { Set-Location "C:\Programas" }
```
Por ultimo abra o VSCode, nas suas configurações e escreva o abaixo para a fonte funcionar
![App Screenshot](https://github.com/juan-20/juan-20/blob/main/assets/fontInVSCode.png?raw=true)
