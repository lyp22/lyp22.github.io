---
published: true
title: (装机)ubuntu必要软件及库安装+美化 from 小灰灰
category: linux
tags: 
  - ubuntu
layout: post
---


#  change source
aliyun service

# apt
```
apt install fish tmux guake git build-essential baobab gparted vim gconf2 cmake aria2 uget bleachbit pinta speedtest-cli puddletag xdot dconf-editor iotop trash-cli fish gnome-todo backintime-qt4
```


# dpkg
```
dpkg -i wps,chrome,electron-ssr,xmind-zero,virtualbox,sogou-pinyin,nautilus_nutstore,teamviewer,vnciewer,netease
```

# install gz...
veractype,foxitreader

# configure ssr


# configure guake

# sign in to google

# install albert
```
wget -nv https://download.opensuse.org/repositories/home:manuelschneid3r/xUbuntu_18.04/Release.key -O Release.key
sudo apt-key add - < Release.key
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/manuelschneid3r/xUbuntu_18.04/ /' > /etc/apt/sources.list.d/home:manuelschneid3r.list"
sudo apt-get update
sudo apt-get install albert
```

# uninstall firefox

# install markdown editor
## typora
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
sudo add-apt-repository 'deb http://typora.io linux/'
sudo apt install typora

# auto mount 
C D E dataset

```
/dev/sda3 /media/C ntfs defaults,uid=1000 0 0
/dev/sda5 /media/D ntfs defaults,uid=1000 0 0
/dev/sdb1 /media/E ntfs defaults,uid=1000 0 0
/dev/sdb4 /media/Dataset ext4 defaults 0 0
/dev/sda4 /media/Ubuntu_Software ext4 defaults 0 0
```

# build soft link

```
ln -s /media/C c
ln -s /media/D d
ln -s /media/Dataset/ dataset
ln -s /media/E e
ln -s d/research/
ln -s research/workspace/
ln -s workspace/Github/ github
ln -s e/backup/
ln -s e/Software/LinuxSoftware/ software
```

# install python

1. install miniconda
2. change pip source
3. install from envirnment

# install program tool

tar pycharm,clion
// tar -xf pycharm-community-2018.2.2.tar.gz -C ~
add desktop shortcut

K71U8DBPNE-eyJsaWNlbnNlSWQiOiJLNzFVOERCUE5FIiwibGljZW5zZWVOYW1lIjoibGFuIHl1IiwiYXNzaWduZWVOYW1lIjoiIiwiYXNzaWduZWVFbWFpbCI6IiIsImxpY2Vuc2VSZXN0cmljdGlvbiI6IkZvciBlZHVjYXRpb25hbCB1c2Ugb25seSIsImNoZWNrQ29uY3VycmVudFVzZSI6ZmFsc2UsInByb2R1Y3RzIjpbeyJjb2RlIjoiSUkiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJSUzAiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJXUyIsInBhaWRVcFRvIjoiMjAxOS0wNS0wNCJ9LHsiY29kZSI6IlJEIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiUkMiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJEQyIsInBhaWRVcFRvIjoiMjAxOS0wNS0wNCJ9LHsiY29kZSI6IkRCIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiUk0iLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJETSIsInBhaWRVcFRvIjoiMjAxOS0wNS0wNCJ9LHsiY29kZSI6IkFDIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiRFBOIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiR08iLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJQUyIsInBhaWRVcFRvIjoiMjAxOS0wNS0wNCJ9LHsiY29kZSI6IkNMIiwicGFpZFVwVG8iOiIyMDE5LTA1LTA0In0seyJjb2RlIjoiUEMiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifSx7ImNvZGUiOiJSU1UiLCJwYWlkVXBUbyI6IjIwMTktMDUtMDQifV0sImhhc2giOiI4OTA4Mjg5LzAiLCJncmFjZVBlcmlvZERheXMiOjAsImF1dG9Qcm9sb25nYXRlZCI6ZmFsc2UsImlzQXV0b1Byb2xvbmdhdGVkIjpmYWxzZX0=-Owt3/+LdCpedvF0eQ8635yYt0+ZLtCfIHOKzSrx5hBtbKGYRPFDrdgQAK6lJjexl2emLBcUq729K1+ukY9Js0nx1NH09l9Rw4c7k9wUksLl6RWx7Hcdcma1AHolfSp79NynSMZzQQLFohNyjD+dXfXM5GYd2OTHya0zYjTNMmAJuuRsapJMP9F1z7UTpMpLMxS/JaCWdyX6qIs+funJdPF7bjzYAQBvtbz+6SANBgN36gG1B2xHhccTn6WE8vagwwSNuM70egpahcTktoHxI7uS1JGN9gKAr6nbp+8DbFz3a2wd+XoF3nSJb/d2f/6zJR8yJF8AOyb30kwg3zf5cWw==-MIIEPjCCAiagAwIBAgIBBTANBgkqhkiG9w0BAQsFADAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBMB4XDTE1MTEwMjA4MjE0OFoXDTE4MTEwMTA4MjE0OFowETEPMA0GA1UEAwwGcHJvZDN5MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxcQkq+zdxlR2mmRYBPzGbUNdMN6OaXiXzxIWtMEkrJMO/5oUfQJbLLuMSMK0QHFmaI37WShyxZcfRCidwXjot4zmNBKnlyHodDij/78TmVqFl8nOeD5+07B8VEaIu7c3E1N+e1doC6wht4I4+IEmtsPAdoaj5WCQVQbrI8KeT8M9VcBIWX7fD0fhexfg3ZRt0xqwMcXGNp3DdJHiO0rCdU+Itv7EmtnSVq9jBG1usMSFvMowR25mju2JcPFp1+I4ZI+FqgR8gyG8oiNDyNEoAbsR3lOpI7grUYSvkB/xVy/VoklPCK2h0f0GJxFjnye8NT1PAywoyl7RmiAVRE/EKwIDAQABo4GZMIGWMAkGA1UdEwQCMAAwHQYDVR0OBBYEFGEpG9oZGcfLMGNBkY7SgHiMGgTcMEgGA1UdIwRBMD+AFKOetkhnQhI2Qb1t4Lm0oFKLl/GzoRykGjAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBggkA0myxg7KDeeEwEwYDVR0lBAwwCgYIKwYBBQUHAwEwCwYDVR0PBAQDAgWgMA0GCSqGSIb3DQEBCwUAA4ICAQC9WZuYgQedSuOc5TOUSrRigMw4/+wuC5EtZBfvdl4HT/8vzMW/oUlIP4YCvA0XKyBaCJ2iX+ZCDKoPfiYXiaSiH+HxAPV6J79vvouxKrWg2XV6ShFtPLP+0gPdGq3x9R3+kJbmAm8w+FOdlWqAfJrLvpzMGNeDU14YGXiZ9bVzmIQbwrBA+c/F4tlK/DV07dsNExihqFoibnqDiVNTGombaU2dDup2gwKdL81ua8EIcGNExHe82kjF4zwfadHk3bQVvbfdAwxcDy4xBjs3L4raPLU3yenSzr/OEur1+jfOxnQSmEcMXKXgrAQ9U55gwjcOFKrgOxEdek/Sk1VfOjvS+nuM4eyEruFMfaZHzoQiuw4IqgGc45ohFH0UUyjYcuFxxDSU9lMCv8qdHKm+wnPRb0l9l5vXsCBDuhAGYD6ss+Ga+aDY6f/qXZuUCEUOH3QUNbbCUlviSz6+GiRnt1kA9N2Qachl+2yBfaqUqr8h7Z2gsx5LcIf5kYNsqJ0GavXTVyWh7PYiKX4bs354ZQLUwwa/cG++2+wNWP+HtBhVxMRNTdVhSm38AknZlD+PTAsWGu9GyLmhti2EnVwGybSD2Dxmhxk3IPCkhKAK+pl0eWYGZWG3tJ9mZ7SowcXLWDFAk0lRJnKGFMTggrWjV8GYpw5bq23VmIqqDLgkNzuoog==

# 隐藏开机选择界面

* sudo gedit /etc/default/grub

```
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true //隐藏开机选择界面
GRUB_TIMEOUT=0 // 设置开机选择界面等待时间，0 不显示
GRUB_DISABLE_OS_PROBER=true
```

* sudo update-grub // update grub

# theme beauty

```
sudo apt install gnome gnome-shell
```


```
sudo apt install gnome-tweak-tool chrome-gnome-shell gnome-shell-extensions
```


## papirus图标

```
sudo add-apt-repository ppa:papirus/papirus
sudo apt update 
sudo apt-get install papirus-icon-theme
```



## Arc主题

```
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/ /' >> /etc/apt/sources.list.d/arc-theme.list"
sudo apt-get update
sudo apt-get install arc-theme
```

## install extensions

the website is [here](https://extensions.gnome.org/local/).

should install:

1. Hide Top Bar
2. Dash to Dock
3. TopIcons Plus

# install NVIDIA-driver

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
```

more detail [here](https://www.jianshu.com/p/4366ed27add9)

# install vlc

sudo snap install vlc

# install wine app

1. qq
2. wechat
3. thurder

more detail [here](https://blog.csdn.net/qq_25987491/article/details/81364461) and [here(github)](https://github.com/wszqkzqk/deepin-wine-ubuntu) and [here(resouce)](http://mirrors.aliyun.com/deepin/pool/non-free/d/)

# install [fusuma](https://github.com/iberianpig/fusuma)

a touchpad tool.

```
sudo gpasswd -a $USER input
sudo apt install libinput-tools
sudo apt install ruby
sudo gem install fusuma
sudo apt install xdotool
# Touchpad not working in GNOME
gsettings set org.gnome.desktop.peripherals.touchpad send-events enabled
```

# setting shortcut

## Customize Gesture Mapping

```
mkdir -p ~/.config/w        # create config directory
nano ~/.config/fusuma/config.yml # edit config file.
```

Example

```
swipe:
  3: 
    left: 
      command: 'xdotool key ctrl+Prior'
    right: 
      command: 'xdotool key ctrl+Next'
    up: 
      command: 'xdotool key super+w'
#      threshold: 1.5
    down: 
      command: 'xdotool key super+s'
#      threshold: 1.5
  4:
    left: 
      command: 'xdotool key alt+Left'
    right: 
      command: 'xdotool key alt+Right'
    up: 
      command: 'xdotool key super+e'
    down: 
      command: 'xdotool key super+a'
pinch:
  2:
    in:
      command: 'xdotool key ctrl+plus'
      threshold: 0.1
    out:
      command: 'xdotool key ctrl+minus'
      threshold: 0.1

threshold:
  swipe: 1
  pinch: 1

interval:
  swipe: 1
  pinch: 1
```

# nvidia转换问题

NVIDIA转换为intel可以在NVIDIA setting中设置
intel转换为NVIDIA，先命令行sudo prime-select nvidia，然后重启就好
