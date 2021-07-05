
# The Calm Window Manager (CWM) configuration

This repository showcases screenshots of the Calm Window Manager (CWM)

[CWM](https://github.com/leahneukirchen/cwm)

CWM is a floating window manager, that can also do tiling.

There is also a built-in application launcher.

However, as CWM is extremely minimalistic, other applications are used to obtain extra bling.


## Screenshots of floating windows

![](images/VirtualBox1.png)
![](images/VirtualBox2.png)
![](images/VirtualBox3.png)
![](images/VirtualBox4.png)
![](images/VirtualBox5.png)
![](images/VirtualBox6.png)
![](images/VirtualBox7.png)


## Screenshots of tiled windows

![](images/VirtualBox8.png)
![](images/VirtualBox9.png)


## Screenshots with application launcher

![](images/VirtualBox10.png)
![](images/VirtualBox11.png)


## Installation of CWM

Most Linux distributions have the CWM in their repository.
So installing CWM is extremely easy. For example:
```
# dnf install cwm 
```

FreeBSD also has CWM in their repository, and is installed as follows:
```
# pkg install cwm
```


## Other packages used

Use of other packages can be seen in the screenshots, and they are:
 + fish shell
 + chromium browser
 + urxvt terminal
 + exa - a modern replacement for ls
 + feh wallpaper launcher

```
# dnf install fish chrome rxvt-unicode exa feh
```

Transparency in the terminal is performed by Compton:
```
# dnf install compton
```



## Configuration files


### Bash configuration file

The ~/.bash_profile file is like this:
```
feh --no-fehbg --bg-fill --randomize /usr/share/backgrounds/wallpapers-master&
compton&
```


### Fish configuration file

The ~/.config/fish/config.fish file is like this:
```
export LESS_TERMCAP_mb=(printf '\e[01;31m') # enter blinking mode - red
export LESS_TERMCAP_md=(printf '\e[01;35m') # enter double-bright mode - bold, magenta
export LESS_TERMCAP_me=(printf '\e[0m') # turn off all appearance modes (mb, md, so, us)
export LESS_TERMCAP_se=(printf '\e[0m') # leave standout mode    
export LESS_TERMCAP_so=(printf '\e[01;33m') # enter standout mode - yellow
export LESS_TERMCAP_ue=(printf '\e[0m') # leave underline mode
export LESS_TERMCAP_us=(printf '\e[04;36m') # enter underline mode - cyan
```

Note - same as bash except the $ is removed

### CWM configuration file

The ~/.cwmrc is like this:

```
# these fonts are for the menu
#fontname "sans-serif:pixelsize=16"
#fontname "monospace:pixelsize=15"
#fontname "dejavu sans mono:size=7"
fontname fixed-13

moveamount 10	# granularity of finest movement
vtile 60
htile 60
gap 5 5 5 5
color inactiveborder black

bind-key CM-Return	"urxvt"
bind-key CM-minus	window-vtile
bind-key CMS-minus	window-htile

# applications
command xscreensaver	"xscreensaver"
command xclock		"xclock"
command top		"urxvt +sb -depth 32 -bg rgba:0000/0000/0000/6666 -fg [100]cyan -e top"
command urxvt-bkblack	"urxvt +sb -depth 32 -bg rgba:0000/0000/0000/aaaa -fg [100]grey -fn xft:monospace:pixelsize=12 -geometry 132x50 +ssr"
command urxvt-bkdarkred	"urxvt +sb -depth 32 -bg rgba:3333/0000/0000/aaaa -fg [100]grey -fn xft:monospace:pixelsize=12 -geometry 132x50 +ssr"
command urxvt-bklightred	"urxvt +sb -depth 32 -bg rgba:aaaa/0000/0000/aaaa -fg [100]grey -fn xft:monospace:pixelsize=12 -geometry 132x50 +ssr"
command urxvt-bkdarkgreen	"urxvt +sb -depth 32 -bg rgba:0000/3333/0000/aaaa -fg [100]grey -fn xft:monospace:pixelsize=12 -geometry 132x50 +ssr"
command urxvt-bkdarkblue	"urxvt +sb -depth 32 -bg rgba:0000/0000/3333/aaaa -fg [100]grey -fn xft:monospace:pixelsize=12 -geometry 132x50 +ssr"

```

note 1 - as urxvt is configured without scroll bars, use shift-pageup to scroll up, and shift-pagedown to scroll down. 
note 2 - the +ssr parameter of urxvt turns off secondary screen scroll, so for example text inside the VIM editor will not be shown in the primary window after VIM is exited.


