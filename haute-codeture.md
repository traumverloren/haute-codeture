theme: Poster Custom
footer: @stephaniecodes

# Haute Codeture

## <br/><br/>

### Stephanie Nemeth

#### @stephaniecodes ✨ stephanie.lol

[.hide-footer]

---

## I like to build fun things with LEDs.

![inline](wilburparty.gif)

^ But i didn't know i liked to build fun things with leds until recently.

---

## I'm a hardware newbie.

^ only been working with hardware for the past year.

---

### I got inspired at an art museum.

#<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
![original](stedelijk.jpg)

^I got into hardware cuz I got inspire by a visit to an art museum.

^Stedelijk museum in Amsterdam

^I went to see an exhibition of art by Jean Tinguely.

---

### Jean Tinguely

#<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

![original](tinguely.jpg)

^ Jean Tinguely

^ Swiss, 60s/70s

^ Art NOT about standing in a sterile white space, distantly gazing silent painting

^ Art meant to be playful

^ Created installations meant to be triggered by a viewer

^ The viewers's experience was integrated into the overall effect of the work itself

^ It intentionally blurred the line between artist and viewer

^ The viewer is invited to choose a drawing tool (marker, pen, or pencil) and place it in a holder.

^ When put into motion, it moves it along a piece of paper.

^ The result would be a work of art in itself.

^ No longer just watching a process, the viewer, by choosing the drawing tool, plays a role in the creation of an entirely new work of art.

---

> I wanted something ephemeral that would pass like a falling star...The work had to just transpire, make people dream and talk, and that would be all.
> -- Jean Tinguely

^ At the exhibit, this quote by Tinguely stood out to me.

^ Really liked idea of art as a temporary experience that connects an artist and viewer

^ It's spontaneous and,

^ Only meant to bring joy and inspire for short time

---

# ![](blue-hair-emoji.png) + ![](computer.png) = ![](art.png)

^ I was excited by all these ideas

^ and wanted to use my skillset as a developer

^ and make my own interactive art experience

^ I didn't have a studio space to create an installation like Tinguely.

^ Apply same idea of interactivity to the most accessible form of expression I could think of - my clothing.

---

![loop autoplay](intro-clip.mov)

^ I wanted to make a complete, cohesive look that was completely interactive via an app.

^Really interested in interactions that might occur when people realize it's interactive.

---

# Project Plan:

* Web app for user input

![right loop autoplay](IMG_2280.mov)

^ Create a web app for user input

---

# Project Plan:

* Web app for user input
* LEDs + hardware in clothing

![right](rainbow_leds.jpg)

^ Integrate LEDs & microcontrollers in diff pcs of clothing

---

# Project Plan

* Web app for user input
* LEDs + hardware in clothing
* Send messages from app to clothing: <br/>Socket.IO

^ Communication between the app and clothing is handled through socketio

^ One of my favorite libraries as a dev

^ Event-based messaging library that works in all browsers/devices

^ integrate socketio client libraries into app and clothing

^ create a socketio server to relay the msgs

^ Easy setup: node.js server & client libraries

![right 83%](led-couture-schema-socketio.png)

---

## Easy, right?

^ I had a plan

^ Everything is gonna go really smoothly

---

![right](IMG_1603.JPG)

# Faced lots of challenges

^ Lots of wiring and soldering

^ Most ambitious hardware project so far

---

## Building stuff is all about _*iteration*_

^ I had setbacks that made me unsure of my abilities

^ I felt frustrated and that i was terrible maker and never going to get better at this stuff.

^ but most importantly, I tried to learn from every setback I had

^ And continually improve my project.

---

# Iteration #1

### The starting point

^ So let's start at the beginning

---

![inline](led-couture-schema-socketio-heroku.png)

^ Create a simple web app where users choose a color and program for my clothing

^ Create a socketio server to relay the messages from the app to the hardware

^ Deploy it all on a simple express server on Heroku.

^ I didn't have to think much about the software side of the project

^ Main focus was on hardware

^ Most of my focus was on figuring out the hardware bit.

---

[.build-lists: true]

# Hardware

* Small footprint
* Durability
* Wifi connectivity

^ Needed to figure out what all I was going to use to control the LEDs in my clothing

^Must be as discrete/small as possible in my clothing

^ Durable - taking off/on

^ Needed wifi to receive messages from the app.

---

![left 80%](huzzah.jpg)

# Adafruit Feather Huzzah ESP8266

* Arduino
* Small
* Wifi built-in
* Lots of info/tutorials

^I chose an arduino.

^ Arduino is a great choice for a project like this

^ cuz i just needed it to run the light programs

^ and listen for new messages from the app and change programs.

^ Adafruit Feather Huzzah

^it's small, has built-in wifi

^very popular microchip so lots of info online

---

# Building Phase

---

![inline fill](leds_strip-wire-solder.gif)![inline fill](IMG_1337.jpg)
![inline fill](IMG_1349.jpg)![inline fill](build_process_2.jpg)

^So, the build process:

^Basically me sitting on the floor in my living room of my tiny amsterdam apartment, and constructing each piece, testing, and fixing soldering mistakes lol

---

![fit](cards.jpg)

---

# First Outing: Lighted Bike Ride Amsterdam

![inline loop](bike-ride.mp4)

^So excited to take it out in public!

^ But as you can see in the video

^ My skirt crashes and reboots to a diff program

^But super FAIL

---

# Fail

![inline autoplay loop](sigh.mp4)

^Embarrassed, disappointed

---

# Iteration #2

### (Or, how to make it crash less)

^An opportunity to troubleshoot and make it work better

---

# Figure out where it was crashing

* Use Serial Monitor in Arduino IDE (Log statements)

![inline](serial-monitor-1.png)

^Lucky for me, the microcontroller i chose supports monitoring when plugged into my computer

^put in log statements at all diff bits of the code

---

# Figure out where it was crashing

* Use Serial Monitor in Arduino IDE (Log statements)

![inline](serial-monitor-2.png)

^ It crashing cuz the arduino was having trouble staying connected to the socketio server

^ It was disconnecting/reconnecting over and over again

---

### Socket.IO is _great_ for the web!

### but is the _best_ fit for my IoT Project?

^Made for web applications communicated over HTTP

^Geared for browsers, but I didn't need that extra overhead

---

### Just because a library is available, doesn't mean it's the best solution

^So i took a step back and thought again about what i was up against coding for hardware.

---

# Coding for Hardware

* Resources are at a premium
* Minimize overhead

^Not communicating between browser and server for my hardware, so that extra overhead for HTTP isn't needed.

^ I needed the most bare minimum (but easy to implement and understand) messaging library possible.

---

# ✨ MQTT ✨

^M2M/IoT connectivity protocol

---

# MQTT

A lightweight messaging protocol<br/>optimized for high-latency or unreliable networks

^ Invented in 1999

^ Need a solution that allowed for minimal battery loss and minimal bandwidth connecting sensors over satellite connection.

^ I could give a whole talk about MQTT but wanna highlight the things that I thought were the most awesome.

---

# Publish/subscribe

![inline](mqtt-pubsub-diagram.png)

^ Publish Subscribe Architecture

^ clients and a broker.

^ Clients connect to the broker, which then mediates communication between the devices.

^ When a device connects it can subscribe to topics.

^ Then, when another client publishes a message on a subscribed topic, the broker forwards the message to any client that has subscribed to it.

^ Publisher and subscriber do not need to know each other

^ Publisher and subscriber do not need to run at the same time.

^ Operations on both components are not halted during publish or receiving

---

# Lightweight

* Transport over TCP/IP
* 2 byte overhead

^ MQTT control packet headers are kept as small as possible.

^ Every bit in the packet is carefully crafted to reduce the data transmitted over the network.

^ It means that in comparison with many other protocols (HTTP) it almost does not load the network with the transfer of information, which is necessary only for the functioning of the protocol.

^ Having a small header overhead makes this protocol appropriate for IoT by lowering the amount of data transmitted over constrained networks.

---

![inline](mqtt-table.jpg)

^ MQTT has short and readable specification.

^ Simple verbs used to describe actions:

^ Basically 5 verbs in MQTT: CONNECT, DISCONNECT, PUBLISH, SUBSCRIBE, PING

---

# Setup MQTT Clients + Broker

![inline](mqtt-pubsub-diagram.png)

^ Needed to rework my app, hardware, and server setup and change it to use to use MQTT instead of socketio.

---

# Setup Web App Client

![inline](mqtt-pubsub-diagram-arrow-app.png)

---

![inline 30%](MQTTjs.png)

^yay can use MQTT in the browser!

^MQTT.js is a client library for the MQTT protocol, written in JavaScript for node.js and the browser.

---

# MQTT.js Client

```javascript
var mqtt = require("mqtt");
// Create a client that connects to the broker
var client = mqtt.connect(MQTT_BROKER_URL);

function sendEvent(program) {
  // Publish topic: "lights", payload: "rainbow"
  client.publish("lights", program);
}

var rainbowButton = document.getElementById("rainbowButton");
rainbowButton.addEventListener("click", () => sendEvent("rainbow"));
```

^Easy to follow

^Only a couple lines of code to implement.

^Include the library, Create a client that connects to the url wherever the mqtt broker is located on the web

^Create a function so that whenever the rainbowButton is clicked,

^sends a message to the broker with topic "lights" with the payload being the string "rainbow"

---

# Setup Arduino Clients

![inline](mqtt-pubsub-diagram-arrow-arduino.png)

---

# Arduino-MQTT Client

```c
#include <MQTTClient.h>

void setup() {
  WiFi.begin(SSID, PW);
  // Connect to broker, subscribe to topic "lights"
  MQTTClient.begin(MQTT_BROKER_URL, WiFiClient);
  MQTTClient.connect("necklace", KEY, TOKEN);
  MQTTClient.subscribe("lights");
  // Called when message received
  MQTTClient.onMessage(messageReceived);
}
void loop() {
  // Sends/receives messages
  MQTTClient.loop();
}
```

^Easy to follow even if you aren't familiar with coding for arduino!

^ Almost identical to web client

^Connect client to mqtt broker thru the url

^Subscribes to topic "lights"

^Whenever message is received, onMessage method is called.

---

# Setup MQTT Broker

![inline](mqtt-own-broker-plan-heroku-arrow.png)

^Everything going really smoothly, setting up the broker should be easy too right?

---

# Setup MQTT Broker

![inline](mqtt-own-broker-plan-heroku.png)

---

# Setup MQTT Broker

![inline](mqtt-own-broker-plan-heroku-no.png)

---

# MQTT Broker

* Couldn't create my own on Heroku (ports not accessible)
* But... also not ready to leave Heroku

^ Minor hiccup... but looked for a Broker as a service instead

---

# Setup MQTT Broker

![inline](mqtt-own-broker-plan-heroku-ext.png)

---

# shiftr.io

IoT prototyping platform

* Free
* Easy setup

^Sign up and get a key/token and ready to roll

^Also doesn't seem to be a limitation on # of messages per min

---

![inline autoplay loop](hoorayquestionmark.mp4)

^I was happy but I wasn't ecstatic.

^ Relying on a small external broker service not optimal.

---

# Iteration #3

### Build my own MQTT broker!

^ Built my own mqtt broker

^ Move services from heroku to Digital Ocean

---

# MQTT Broker: AEDES

![inline](aedes-github.png)

[https://github.com/mcollina/aedes](https://github.com/mcollina/aedes)

^To implement the MQTT broker, used this library

^broker is embeddable in my current express server, minimal configuration change

---

IMPLEMENT THE MQTT BROKER

```javascript
const express = require("express");
const app = express();
const path = require("path");
const aedes = require("aedes")();
// Create MQTT server for MQTT connections
const mqttServer = require("net").createServer(aedes.handle);
// Create HTTP server for website requests
const httpServer = require("http").createServer(app);
const ws = require("websocket-stream");
const mqttPort = 1883;
const appPort = 8080;

mqttServer.listen(mqttPort, function() {});
httpServer.listen(appPort, function() {});
// Augment the HTTP server with MQTT-over-websocket capabilities
ws.createServer({ server: httpServer }, aedes.handle);
```

^Only a couple lines of code to implement.

^Include the library

^Create MQTT server & HTTP server

^ Specify ports

^Listen on those ports

^Then addon so the HTTP server has MQTT over websocket capabilities so that it can handle MQTT connections from clients in the browser (our web app)

---

![](ballmer.gif)

^Awesome!

^I conquered my devops fears and it worked!

^I was done right?

---

# Iteration #4

#### (aka last thing I changed)

### Upgrade Microcontroller

^Nope, upgrade the hardware

---

[.build-lists: true]

![left 110%](feather-m0.jpg)

## Adafruit Feather M0 WiFi

* Low power management
* Separate Wifi module
* High speed, reliable Wifi 🤩
* 2X cost of Feather Huzzah

^ Low power management

^ Separate Wifi module

^ Don't have to yield all the time to the WiFi core, since its a separate chip. You get full reign of the processor and timing

^ 2X cost of Feather Huzzah

---

![loop autoplay](haute-codeture-end.mov)

^Demo time!

---

## It's a _really_ weird experiment to do as an introvert.

#<br/>

#### (Flashylights.nl)

^ attracting attention and actively seeking out people to interact with me is way outside my comfort zone.

^ it was also an experiment that pushed me to deal with my own reactions to those interactions.

^ but I really wanted to see if i could bring a momentary and joyful to strangers by giving them free reign over my appearance.

^ An application like this is a side of tech a lot of folks haven't experienced.

^ breaking stereotypes with strangers

^ what you can build and who is capable of building those things.

---

# Thank you!

![right autoplay loop](IMG_3976.mov)

###🦄✌☮️️✨

[stephanie.lol](https://stephanie.lol)

[@stephaniecodes](https://twitter.com/stephaniecodes)
