# trad

trad is a simple, and currently unfinished, command line python program to facilitate easy interaction with IKEA Trådfri devices. Currently it can do simple tasks like turn on / turn off or dim lightbulbs. See example commands below.

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
- Example: `trad setup 192.168.0.100 dj2o3njmdcvoj23r`

Now the program should be working, and be able to communicate with your gateway. Try it with `trad devices` and see if it lists the devices on your network.

## Examples

_Note: all device names are case insensitive!_

_Note: if a device name contains spaces (e.g. "Office 2") you must surround it with quotation marks on the command line, e.g. `trad on "office 2"`. Single quotation marks also works._


* `trad on {name}` will turn on lightbulb named {name}. 

* `trad off {name}` will turn off lightbulb named {name}. 
 
* `trad toggle {name}` will turn toggle lightbulb named {name} on or off, depending on its current state.
 
* `trad dim {name} {value}` will set brightness value of lightbulb named {name} to {value}. Value must be between 0-254.

* `trad temp {name} {value}` will change the color temperature of a bulb. Value can be warm/normal/cool, or a number between 0-204.
 
* `trad groups` will list the names of all groups defined in your gateway. Add `-j` to output json with all known details.
 
* `trad devices` will list the names of all devices defined in your gateway. Add `-j` to output json with all known details.

* `trad daemon` will daemonize the program - DO NOT USE - THE DAEMON CURRENTLY DOES NOTHING!!

## TODO (aka Planned Features) (aka Wanted Features)
- Migrate to a client/server model - or a daemon that can monitor the network and all trådfri device, and respond to commands.
- Add interaction with entire groups (e.g. something like `trad off livingroom -g` to turn off all bulbs in the 'livingroom' group.)
- [DONE for on/off state] Add command to get the current state of a lightbulb.
- Add support for tasks/timers, and moods.
- [DONE] Add support for setting color temperature.
- Add support for RGB bulbs.
- Many of these are already supported by pytradfri - those should be relatively easy to implement.
