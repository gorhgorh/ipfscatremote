# ipfscatremote 🐈🤖

Client and server code for cat remote robot arm over ipfs.

## Hardware
- 1 catbot
- an additional arduino + joystick

### Wire catbot
uses pin 10 x and 11 y
laser: direct to 5v
#### Wire Joystick
uses a0 for x and a1 for X

## Software
you need to setup a few things before starting the server / client

### dry run (no bots)
you can test the peer to peer connection by editing the file constants.js and set HASBOT to ```false``` this will disable the j5 code allowing you to use the keyboard arrow to test if the connection works

### 2 computers
if you have the catbot and the controller on two separate computer edit constant.js as follow

```js
...
exports.HASBOT = true
exports.JOYPORT = false
exports.CATPORT = false
```

### 1 computer
board autodetection does not guarantee what part of the system get which board on load, to fix this we need to provide the path to the serial port interface
to find them, unplug both board and type ```ls /dev/tty.*```
now plug one of them and re run ```ls /dev/tty.*``` the new path on the list will be your board one, note it, and now plug the second board to get it's path,
then edit constant.js

```js
...
exports.HASBOT = true
exports.JOYPORT = '/dev/tty.yourjoyport'
exports.CATPORT = '/dev/tty.yourcatbotport'
```

## Run it

- start the server ```node server```
- copy the server adress that is logged
- start the client ```node client```
- paste the server adress
- enjoy some interplanetary cat remote controll!
