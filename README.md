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
- [x] There are still some icon missing.
    - I finally fixed it by tweaking the theme. See <https://askubuntu.com/questions/1311713/can-anyone-help-me-with-my-tigervnc-xstartup-script-for-ubuntu-18-04s-gnome-doc>

## Troubleshooting
* `gnome-session --session=ubuntu --debug`
* `ps aux | grep gnome`: See how `gdm` invoke `gnome-session`
* `man gnome-session`
* `man gnome-shell`
* `man gdm3`: It mentions `/usr/share/xsessions`
* `apt list --installed | grep gnome`
    * `gnome-shell-extension-ubuntu-dock`
* `dbus-daemon`
* `man vnc.conf`
* `/etc/vnc.conf`
* `man vncserver`
* `man Xsession`
* `/usr/lib/gdm3/gdm-x-session`
* `cat /etc/X11/default-display-manager`
* `vim /etc/X11/Xvnc-session`
* `vim /etc/X11/Xsession`
* `/etc/gdm3`
* `/etc/X11/Xsession.d/20x11-common_process-args`
* `/etc/X11/Xsession.d/50x11-common_determine-startup`
    * In my Ubuntu 18.04, `x-session-manager` is an alias to `/etc/alternatives/x-session-manager` (where it eventually point `usr/bin/gnome-session`)
* `env |grep XDG_DATA_DIRS`: This enviornment variable will control how the `.desktop` file are loaded.
* `/etc/profile.d/xdg_dirs_desktop_session.sh`: This file explains why `/usr/share/ubuntu` is added in `XDG_DATA_DIRS`

## References
* <https://help.ubuntu.com/community/VNC/Servers>: I mainly consulted this page
* <https://www.cyberciti.biz/faq/install-and-configure-tigervnc-server-on-ubuntu-18-04/>
* <https://askubuntu.com/questions/648819/couldnt-start-xtightvnc-trying-default-font-path-vncserver>
* <https://bugzilla.redhat.com/show_bug.cgi?id=1149893>: Color profile issue when successfully entering GNOME.
* <https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04>
* <https://www.teknotut.com/en/install-vnc-server-with-gnome-display-on-ubuntu-18-04/>
* <https://askubuntu.com/questions/1031147/running-vnc-server-on-ubuntu-desktop-18-04-by-creating-new-sessions/1035321#1035321>
    * The Gnome session doesn't seem to work on VNC X servers, but an Xvfb will work. The idea is to create an Xvfb for the session and use x11vnc for VNC

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
* <https://askubuntu.com/questions/1209511/what-is-a-ubuntu-gnome-session-and-why-isnt-it-a-systemd-user-session>: See `/usr/share/xsessions/ubuntu.desktop`
* <https://unix.stackexchange.com/questions/263922/what-is-the-tryexec-field-in-desktop-files>: `TryExec` in `.desktop` file.
* <http://manpages.ubuntu.com/manpages/bionic/man1/dbus-launch.1.html>: `dbus-launch --exit-with-session gnome-session`
* <https://github.com/TigerVNC/tigervnc/issues/1131>: Almost the same error messages as me!
* <https://stackoverflow.com/questions/17251293/what-is-the-relationship-between-x11-and-gnome>: The relationship between `GNOME` and `X`
* <https://askubuntu.com/questions/1033004/18-04-how-to-get-wayland-back-after-upgrade-to-18-04>: `/etc/gdm3/custom.conf` `/etc/gdm3/Xsession`
* <https://specifications.freedesktop.org/desktop-entry-spec/latest/>: `.desktop` specification
* <https://wiki.archlinux.org/index.php/desktop_entries>
* <https://specifications.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html>
    * See `Icon Lookup`
    * See `/usr/share/icons/hicolor/index.theme`
* <https://wiki.archlinux.org/index.php/TigerVNC>: Arch Linux doc never fails me.
* <https://wiki.archlinux.org/index.php/GNOME#GNOME_Shell_themes>
* <https://gitlab.gnome.org/GNOME/gdm/blob/master/daemon/gdm-x-session.c>: `gdm-x-session`
* <https://c-nergy.be/blog/?p=12073>
* <https://unix.stackexchange.com/questions/417906/authentication-is-required-to-create-a-color-profile>: Color profile issue
* <https://askubuntu.com/questions/64283/custom-application-icons-not-displaying>: Icon cache: `gtk-update-icon-cache`
* <https://itsfoss.com/gnome-tweak-tool/>: `apt install gnome-tweaks`
* <https://askubuntu.com/questions/779645/ubuntu-software-icon>: `/usr/share/ubuntu/applications/org.gnome.Software.desktop` and `/usr/share/applications/org.gnome.Software.desktop`: I totally not understand why there are two `desktop` file....
* <https://askubuntu.com/questions/1312020/can-someone-explain-why-there-exist-two-org-gnome-software-desktop-files-which>: The question I ask. I found this related to `XDG_DATA_DIRS`.
* <https://unix.stackexchange.com/questions/471327/whats-the-right-way-to-add-directories-to-xdg-data-dirs>: `XDG_DATA_DIRS`
* <https://gitlab.gnome.org/GNOME/gdm/-/blob/97ca4b1268e78a21041d9fda9512b892ce344d92/daemon/gdm-session.c#L2631-2641>: `DESKTOP_SESSION`  is set in this line. However, my ad-hoc `xstartup` was not invoked by `gdm-*` related processes. For more information, please see `gdm_session_start_session` function in that link. (There is a `set_up_session_environment` function).
