The Telescope Pi is a RaspberryPi on the back of the telescope. It runs the filter wheel, which uses a Phidgets stepper driver to rotate filters while an Arduino monitors the hall effect sensor.

## Homing the Filter Wheel
The home command calibrates the filter wheel's position. At the beginning of the night press the Home button in Evora. The filter wheel will spin around twice so that it can calibrate filter offsets. It must succeed for the filter wheel to operate properly. At the moment it does NOT home properly 100% of the time, but subsequent homes have always worked.

## Changing Filters
In Evora, choose the filter from the drop-down menu and click Rotate.

## Troubleshooting
TelescopeServer runs in a [screen](https://linuxize.com/post/how-to-use-linux-screen/) session as a system service on the Telescope Pi. Control the server with

$ ssh pi@telescopepi.mro.cwu.edu

$ sudo systemctl [enable/start/stop] TelescopeServer

“enable” (already set) means the service will start with each reboot, other options are start and stop.

You can inspect the server’s output,

ssh pi@telescopepi.mro.cwu.edu

$ screen -r

When you’re done, hit Ctrl-a d *before* closing the session.

## Telnet Commands
Any of the following commands can just be typed into a telnet: telnet telescopepi 5503

- **home** find the absolute position of the filter wheel

- **move [pos]** move to a filter position. Position can be any integer, although 0-5 make the most sense since there are 6 filter wheel positions.

- **getfilter** returns filter wheel position as an integer 0-5