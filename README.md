# Remote Controlled Pi

With this library you can video stream from your `Raspberry Pi` with a `Pi Camera`.
The added feature is a on-screen joystick that works on touch-enabled devices and on regular computers.
The measured movement of the joystick is then relayed back to your `Raspberry Pi`, where you can then do anything with it - for instance, **driving a robot**.

Here's an example project done with a `GoPiGo3` robot.
![Example project done with GoPiGo3](http://i.imgur.com/SLUQGgS.gif)

## How to use it

In order to process the joystick's movement, you have to take a look at `robot_commands` function that resides in `flask_server.py` script.
In this function, you get new updates of the joystick every 250 ms.
In this function, there are a couple of variables that were already assigned queried values. Here's what it means for each of it:

* `state`: It's set to `move` when the joystick is moved away from the center and `stop`, when the joystick is released (and destroyed).
* `angle_degrees`: The orientation of the joystick's small circle relative to the big circle. It's anti-clockwise and it starts at 0 degrees at the right (where the joystick is pulled to the right). It's measured in degrees and the values go from 0 up to 360.
* `angle_dir`: It tells the general orientation of the joystick. It can be `up`/`down`/`left`/`right`.
* `joystick_pull_force`: It tells how much the user is pulling the joystick from its center. The values start at 0 and don't have an upper limit. The upper limit is determined by the screen size.

Since I've added a GIF showcasing the GoPiGo3 I also added code for the GoPiGo3 inside the server, so if you ever want to test the GoPiGo3, just uncomment the imports and the call to `actuate_robot` function and run it. Be aware that you'd have to install the GoPiGo3 project from:
[GoPiGo3 Project](http://github.com/DexterInd/GoPiGo3)


## Setting Up

Install the `Pi Camera` dependencies and `Flask` by running the `install.sh` script:
 ```
 sudo bash install.sh
 ```
If everything goes well, **reboot** your `Raspberry Pi`.
You should now have everything set up.



## Running it

Start the server by typing the following command:
```
python3 flask_server.py
```
It's going to take a couple of seconds for the server to fire up.
A port and address will be shown in there. By default, the port is set to `5000`.
Take your `Raspberry Pi` interface's IP address and port and use it on a mobile device or laptop in order to reach the web page.
The webpage's address will have the following pattern:
```
http://[raspberrypi-ip-address]:[port]
```

Also, please make sure you have your mobile device / laptop on the same network as your `Raspberry Pi`. Otherwise, you won't be able to access it.

## Example Project

This is a project done with this library and with a `GoPiGo3`. Check it out on YouTube.

[![Alt text](https://img.youtube.com/vi/Tu_-Al6Smhg/0.jpg)](https://www.youtube.com/watch?v=Tu_-Al6Smhg)
