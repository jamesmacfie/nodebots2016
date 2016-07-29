# nodebots2016

## Welcome ##

Hello. Thanks for dropping by.

Getting everything setup to start building robots is a reasonably straight forward endeavour but if you have any issues with getting things running then just hit up one of the help. It's what we're here for.

If you get everything here sussed then you'll be well on your way to building something epic. I'm looking forward to seeing what you create.

## Setting up your environment ##

Provided the Arduino's have been flashed correctly, you should only need to install node and some drivers. If the Arduino hasn't been flashed with the correct firmware (i.e - things don't work and Johnny-five complains) then you'll need to download the Arduino software and follow the instructions listed at http://johnny-five.io/platform-support/

### Windows ###


* NodeJS: [Windows Installer here](http://nodejs.org/download/)
* Serial driver software: [windows driver](/drivers/CH340 windows.zip)
* Arduino: [Windows install guide](https://www.arduino.cc/en/guide/windows)

```
    npm install johnny-five
```

### OS X ###

* NodeJS - [Follow the directions here](http://nodejs.org)
* Serial driver software: [mac driver](/drivers/ch340-mac-driver.zip)
* Arduino - [Mac Install guide](http://arduino.cc/en/Guide/MacOSX)

### Linux ###

* NodeJS: [Source install instructions here](http://howtonode.org/how-to-install-nodejs).
* Arduino [Available here to install manually](http://playground.arduino.cc/Learning/Linux) or a simple 'apt-get install arduino' should do it for a relatively recent version.

## How to get going ##

Ok, let's build something simple as a starter.

Let's create a new folder somewhere and call it `nodeBots`. Inside that folder let's create an `index.js` file. This file is where we'll write the script to turn a small LED on/off.

Before we can start telling our board what to do, we first need to install Johnny-Five into the project. To do this you'll need to jump into the command line (after Node is installed) in your new `nodeBots` directory and type `npm install johnny-five`. This shouldn't take long to install.

Open that `index.js` file you created in a text editor. Marvel over the blank canvas and dream of the possibilities suggeseted by the void.

Put the code below into the file and save it:

``` javascript
var five = require("johnny-five");
var board = new five.Board();

board.on("ready", function() {

  // Create a standard `led` component instance
  var led = new five.Led(13);

  // "blink" the led in 500ms
  // on-off phase periods
  led.blink(500);
});
```

A quick explaination about what that is doing. The first line is pulling in the Johnny-Five library that we just installed. Next, it's creating a reference to the board that you'll be plugging in shortly. Once the board is ready to start accepting directions we run a function (known as a callback) and then create a reference to the LED we'll be putting on pin 13. Finally, we'll blink the light every 500ms.

Now that we have our code, let's setup the board. I'm making the assumption here that you are using an Arduino or an Arduino compatible board. Grab the board and an LED and set it up like the image below:

![](http://johnny-five.io/img/breadboard/led-13.png)

It's a pretty simple wee circuit. Notice that the short LED leg goes to ground and the long leg goes to pin 13. Why pin 13? Look back at the code you just entered into the `index.js` file. When we create the `led` variable we call it with the value 13 - this is the pin that Johnny-five is expecting the LED to be on.

Now that our board is setup and code is written we can try it out. First plug the arduino into your computer and head back to the command line. Once you're on the command line inside the project folder you'll be able to run `node index.js` which will run the script we just created.

Provided everything is hunky-dory you should start to see the LED flash every half a second. YAY! OMG!

## What next ##

Anything you like ;) There's a heap of really good examples up at http://johnny-five.io/examples/ so I'd recommend giving those a read.

