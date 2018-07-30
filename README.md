# Smart Mirror

Steps to create a smart mirror which displays time, temperature, daily forecast, and news headlines.

Note, I will not be covering the actual building of the frame, only the programming of the Raspberry Pi. Supplies used in building the frame include 1" x 4" boards, wood stain, two-way mirrored sheet of acrylic, Raspberry Pi 3 (+ micro SD card, charging cable, usb cord, housing, heatsinks, etc.. It comes in a bundle.), 90 degree angle brackets, and a 23" LED monitor.

You should have some experience with using the terminal and git.  The code is written in Python, but you don't necessarily have to know it.

### Installing

First, install Raspbian onto your Raspberry Pi.  This video walks you through setting up your Pi  https://www.youtube.com/watch?v=y4GOG4P-4tY

Connect to wifi

Clone this repository

```
git clone git@github.com:JPMendenhall/smartmirror.git
```

Navigate to the smart mirror folder

```
cd smartmirror
```

Install your dependencies

```
sudo pip install -r requirements.txt
```
```
sudo apt-get install python-imaging-tk
```

I've seen people recommend vim as a text editor for this, but honestly double clicking the smartmirror.py file and editing in Raspbian's built in editor worked just fine.

Register for an API token to retrieve weather updates from forecast.io

Assign the

```
weather_api_token
```
variable with your unique token

Within the smartmirror.py file, change the latitude and longitude variable values to your home city.  It is currently set to Indianapolis.  Replace these with your city's coordinates (Google city name + lat long, ie "San Francisco latitude longitude")

```
latitude= '39.7684'
longitude = '-86.1581'
```
(Important to replace these, unless you live in Indianapolis.)


Save and close.

To change the screen orientation, in your terminal type

```
sudo nano /boot/config.txt
```

Now that you are editing the config file, add this line to the bottom

```
display_rotate=1
```

Press CTRL-X to quit and press Y to save changes.

Restart the Raspberry Pi


## After Restart

Minimize the task bar.  Right-click on the taskbar and select "Panel Settings". Click on the "Advanced" tab, and check "Minimize panel when not in use".

Navigate to your smart mirror folder

```
cd smartmirror
```

Launch the app
```
python smartmirror.py
```

Install unclutter to hide the mouse
```
sudo apt-get install unclutter
```

Hide the cursor
```
unclutter -idle 0.1 -root
```

Maximize the smart mirror app.  Your taskbar should automatically minimize when the mouse is not hovering over it.  To hide the top pane of the window, simply right click and select "Unroll"

You should now have a very similar display to the images shown.  You may need to change the text size variables if the text is either too small, or flowing off the screen.


### Future Iterations

If the mirror loses power, you do have to plug in your keyboard/mouse into the Raspberry Pi and relaunch the app.  I would like it to launch automatically on boot, but I'm having issues with figuring out how to to automatically launch NAD maximize the app, while hiding boarders and window panes with zero user input.  

### Questions or comments?

James@JPMendenhall.com

### Acknowledgments

* Hat tip to the smart mirror community
