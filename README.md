# Ubuntu VNC Setup

## Environment
* Ubuntu 18.04 Desktop

 Requirements
* `sudo apt install tigervnc-standalone-server tigervnc-viewer`
* `sudo apt install xfce4`

## Setup
* Put [xstartup](./xstartup) in `~/.vnc/`
* Run `vncserver -localhost yes :1`
    * Stop it by `vncserver -kill :1`
* Then you can use your favorite VNC Viewer to connect to `localhost:5901` (`:1` refers to port `5901`)

## TODO
- [] There are still some icon missing.

## Troubleshooting
* `gnome-session --session=ubuntu --debug`
* `ps aux | grep gnome`: See how `gdm` invoke `gnome-session`
* `man gnome-session`
* `man gnome-shell`

## References
* <https://help.ubuntu.com/community/VNC/Servers>: I mainly consulted this page
* <https://www.cyberciti.biz/faq/install-and-configure-tigervnc-server-on-ubuntu-18-04/>
* <https://askubuntu.com/questions/648819/couldnt-start-xtightvnc-trying-default-font-path-vncserver>
* <https://bugzilla.redhat.com/show_bug.cgi?id=1149893>: Color profile issue when successfully entering GNOME.
* <https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04>
* <https://www.teknotut.com/en/install-vnc-server-with-gnome-display-on-ubuntu-18-04/>
* <https://askubuntu.com/questions/1031147/running-vnc-server-on-ubuntu-desktop-18-04-by-creating-new-sessions/1035321#1035321>
* <https://askubuntu.com/questions/281177/colours-background-messed-up-in-vnc-viewer>: VNC quality.
* <https://askubuntu.com/questions/905466/dropbox-icon-not-working-unable-to-create-dbus-session-bus>
* <https://askubuntu.com/questions/502837/dbus-folder-in-home-folder-belongs-root>: `~/.dbus/` folder.
* <https://askubuntu.com/questions/281177/colours-background-messed-up-in-vnc-viewer>: Change Picture Quality to High.
* <https://www.linuxquestions.org/questions/linux-general-1/icons-missing-from-desktop-with-vnc-and-gnome-session-36174/>: Icon missing
* <https://unix.stackexchange.com/questions/512679/vnc-server-not-showing-icons-in-ubuntu-18-04>:
    ```
    I suspect the issue is somewhere else that the xstartup. I have tried several different settings there and outcome is always same.
    ```
* <https://www.linuxquestions.org/questions/linux-newbie-8/starting-gnome-session-over-vnc-268828/>
* <https://askubuntu.com/questions/771124/vnc-ubuntu-14-04-destop-dont-show-menus-icon>
* <https://askubuntu.com/questions/1209511/what-is-a-ubuntu-gnome-session-and-why-isnt-it-a-systemd-user-session>: `gnome-session`'s `--session` arg; `/usr/share/gnome-session/sessions/ubuntu.session`
* <https://unix.stackexchange.com/questions/345344/difference-between-xorg-and-gnome-kde-xfce>: The relation between GNOME and X (aka X11, X Window Systems)
* <https://linuxhint.com/how_gnome_starts/>
* <https://askubuntu.com/questions/971388/few-application-icons-not-appearing-in-ubuntu-dock-after-upgrading-to-ubuntu-17>
