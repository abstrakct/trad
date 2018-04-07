# trad

## What?
trad is a simple, and currently unfinished, python program to facilitate easy interaction with IKEA Trådfri devices.

## Requirements
- pytradfri library (tested on version 5.4.2) - install it via pip or wherever you install your python packages from. Source code and more information at https://github.com/ggravlingen/pytradfri
- python 3
- An IKEA Trådfri gateway, connected to at least one bulb.
- I have personally only tested/used it on linux, but it should work on any platform as long as the above requirements are met.

## Why?
I bought some IKEA Trådfri bulbs and a gateway, and wanted an easy way to interact with them via scripts and keyboard shortcuts.

One use case I really like: I have a Raspberry Pi running Kodi media center, and I have set it up to use this program to turn off all lights when it starts playing a video, and turn lights back on when playback stops! I love it.

## How?
- Install pytradfri, and then clone this repository.
- Copy the `trad` file to a directory in your PATH (if you want access to it from anywhere).
- On Linux/unix: create a directory named `trad` under `$HOME/.config`
- On Windows: create a directory named `trad` in your user directory, probably `C:\Users\{your username}` 
- Run `trad setup {ip} {key}` replacing {ip} with the ip address to your IKEA Trådfri gateway, and {key} with the security code found on your gateway. This security code will be encrypted and stored in a .json file in the directory you created above.

Now the program should be working and able to communicate with your gateway. Try it with `trad devices` and see if it lists the devices on your network.

## Examples / how to actually use the program

Note: all device names are case insensitive! 

Note: if a device name contains spaces (e.g. "Office 2") you must surround it with quotation marks on the command line, e.g. `trad on "office 2"`.

`trad on {name}` will turn on lightbulb named {name}. 

`trad off {name}` will turn off lightbulb named {name}. 

`trad toggle {name}` will turn toggle lightbulb named {name} on or off, depending on its current state.

`trad dim {name} {value}` will set brightness value of lightbulb named {name} to {value}. Value must be between 0-254.

`trad groups` will list the names of all groups defined in your gateway. Add `-j` to output json with all known details.

`trad devices` will list the names of all devices defined in your gateway. Add `-j` to output json with all known details.

## TODO aka Planned Features aka Wanted Features
- Add interaction with entire groups (e.g. something like `trad off livingroom -g` to turn off all bulbs in the 'livingroom' group.)
- Add command to get the current state of a lightbulb.
- Add support for tasks/timers and moods.
- Add support for setting color temperature.
- Add support for RGB bulbs.