# ADModule
Microsoft signed DLL for the ActiveDirectory PowerShell module

 ```powershell
PS C:\> Import-Module C:\ADModule\Microsoft.ActiveDirectory.Management.dll -Verbose
```
Or
```powershell
PS C:\> iex (new-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/samratashok/ADModule/master/Import-ActiveDirectory.ps1');Import-ActiveDirectory
```
