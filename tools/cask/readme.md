custodian-cask
===================

custodian-cask is a Go wrapper over the `cloudcustodian/c7n:latest`
Docker image.  It allows you to use the docker image with the same CLI you
would use for a local Custodian installation. 

This can be useful in situations where you would like to ensure a working
CLI without requiring Python or package dependencies.

Install
-------

Linux

```shell
sudo sh -c 'wget -q https://cloudcustodian.io/downloads/custodian-cask/linux-latest/custodian-cask -P /usr/local/bin && chmod +x /usr/local/bin/custodian-cask'
```

Darwin

```shell
sudo sh -c 'wget -q https://cloudcustodian.io/downloads/custodian-cask/darwin-latest/custodian-cask -P /usr/local/bin && chmod +x /usr/local/bin/custodian-cask'
```

Windows (cmd.exe)

```cmd
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/cloud-custodian/cloud-custodian/master/tools/cask/scripts/install.ps1'))" && SET "PATH=%PATH%;%LOCALAPPDATA%\custodian\"
```

Windows (powershell.exe)

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/cloud-custodian/cloud-custodian/master/tools/cask/scripts/install.ps1'))
```


Run
---
```
custodian-cask run -s . policy.yml
```

You may override the default docker image with the environment variable `CUSTODIAN_IMAGE`

Cask will only attempt to pull any specific image once per hour.  
You can delete $(tmp)\custodian-cask* if you'd like to force an update.


Build
-----

```
cd cloud-custodian\tools\custodian-cask
go build -o custodian-cask
```
