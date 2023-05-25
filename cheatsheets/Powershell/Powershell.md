## Linux command equivalents:

- ls -> get-childitem
	- dir, cgi, ls
- cp -> copy-item
	- copy, cpi, cp
- mv -> move-item
	- mi, move, mv
- pwd -> get-location
	- gl, pwd
- cd -> set-location
	- cd, chdir, sl
- cat -> get-content
	- cat, type, gc
- apt install -> install-module
	- ```Install-Module -Name Chocolatey -Force```
	- import-module : import the installed module to the current shell session
	- If error : `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned`
 - apt update -> Get-WindowsUpdate
 - apt upgrade -> Install-WindowsUpdate