#9-sensor-log
**This app allows you to output a strobe at different frequencies, plots the values of analog sensor, and logs timestamped information as JSON**

##Setting up the hardware

I used an [arduino mega](https://www.arduino.cc/en/Main/ArduinoBoardMega2560) for this example, but any of the [boards](http://johnny-five.io/platform-support/) supported by johnny-five should work.

Connect a loopback wire from pin 11 to A1

<img src="./assets/board.png" width="500">

##Setting up the code


To run, first clone the repo and npm install the example directory

```
git clone https://github.com/sofroniewn/electron-johnny-five-examples
cd electron-johnny-five-examples/9-sensor-log
npm install
```

Unfortunately the serial port may not work right away and might need to be rebuilt

```
./node_modules/.bin/electron-rebuild
```

At this point if you try to starting the app with

```
npm start
```
You may get an error if the path to <code>serialport.node</code> is wrong

```
Uncaught Error: Cannot find module '/Users/sofroniewn/github/electron-johnny-five-examples/1-led/node_modules/johnny-five/node_modules/serialport/build/Release/node-v47-darwin-x64/serialport.node'
```

This can easily be fixed by

```
mv ./node_modules/johnny-five/node_modules/serialport/build/Release/electron-v0.36-darwin-x64/ ./node_modules/johnny-five/node_modules/serialport/build/Release/node-v47-darwin-x64/
```

You're now ready to run the app!

For more information about that error and using electron with johnny-five and node-serialport in general, check out this super helpful [blog post](http://meow.noopkat.com/using-node-serialport-in-an-electron-app/) by [@noopkat](https://github.com/noopkat)

##Running the app
After setting up the [hardware](https://github.com/sofroniewn/electron-johnny-five-examples/tree/master/9-sensor-log#setting-up-the-hardware) and the [code](https://github.com/sofroniewn/electron-johnny-five-examples/tree/master/9-sensor-log#setting-up-the-code) you are now ready to run the app with 

```
npm start
```

Once the board has been found and the green status light in the top right has turned on, you should be able to click the **start** button in the top left corner. Pin 11 will then start to output a strobe at a frequency defined by the input box. Change the value of this input to change the frequency of the pulses. The sensor values will also be acquired and plotted to the screen using a [lightning](http://lightning-viz.org/) vizualization. As long as Pin 11 is connected to A1 the orange sensor values should follow the red pulses. The values of the sensor, the strobe and high precision timestamps are also logged to JSON file, <code>'./sensor.log'</code>.

<img src="./assets/screenshot.png" width="500">

**Congrats!** You've gone through all the examples - go and build something amazing!