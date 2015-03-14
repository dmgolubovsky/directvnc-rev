# Display Features #

## Screen Resolution ##

Original directvnc had only support for 16bpp screen color depth. Support for 24bpp (4 bytes per pixel, no alpha-channel) has been added. At the moment, it is still necessary to use the _-bpp_ command line option to set color depth. When negotiating with the remote Xvnc server side, color depth supplied by the server will be used. It is therefore necessary to take care (at least in the present) that screen color depth (default, or set in the [DirectFB configuration file](http://www.directfb.org/docs/directfbrc.5.html)), color depth supplied at the command line, and remote Xvnc server color depth all match.

# Input Features #

## Quitting Directvnc ##

The `Ctrl-Alt-Del` chord is now used (hardcoded) as the quit key. Since DirectFB places the console keyboard into a special mode where special combinations of keys are not passed to the Linux kernel by the console driver, pressing `Ctrl-Alt-Del` does not cause reboot. Since upon restart, directvnc redisplays the remote Xvnc server screen, this feature may be used by a wrapper script to intiate screen lockup, or for other purposes.

## Keyboard Layout Switching ##

Original directvnc has a hardcoded table which translates keyboard input deceived from DirectFB into ISO8859-1 (latin-1) character codes (keysyms) to be sent to the remote Xvnc server, thus providing no ability to dynamically switch keyboard layout. A new feature has been added, providing for setting of alternative keyboard layout, with ability to support non-latin characters such as Cyrillic. A plain text file, containing a subset of [xmodmap(1x)](http://www.linuxmanpages.com/man1/xmodmap.1x.php) syntax (only _keycode_ expressions are recognized with up to four _KEYSYMNAMEs_) can be converted into the format that directvnc understands, and can be loaded upon directvnc starup using the _-m_ command line option. See the KeyboardMapping page for greater details.