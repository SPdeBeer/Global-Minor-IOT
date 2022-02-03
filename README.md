# Global-Minor-IOT
## Global Minor IOT portfolio

Unfortunately, due to unforseen circumstances I was not able to attend the IOT module but I did try to do as much as I can. Of course we didn't get to do all the same things that were done in Austria in person so this portfolio will aim to showcase what I have tried individually as well as with my Group 1 colleagues.

### Things I was able to do from the tasks list
My name is SP de Beer, I am from The Belgium Campus ITversity in South Africa.
My understanding of IOT is the use of physical hardware devices in conjunction with software systems to complete certain tasks, it can make the life of the user much easier and it can automate many processes that will actually make it safer for humans that have very dangerous tasks.
These devices are also connected to the internet so that they can communicate with each other and system, each year more devices get connected to the internet and this also increases their potential whereas a traditional component will only be doing what it was made for for the rest of its life isolated.

Many times there are sensors involved that will tell the system what it is experiencing so that it can then (based on the code that was written for it) make a decision and perform a certain task. IOT is a fairly young field but it is becoming more popular each year with almost all modern devices coming out with some form of sensor or IOT system, one example of this is the new lane assist technology in cars where the sensor input will tell the system how well the car is positioned withing the lane and if it is not corrected within a certain time span it will be done automatically.

At first when you start working with the breadboard and the LEDs you might want to just plug everything in and start working but unfortunately it is not that easy, you always have to consider the voltage, resistance and amperes of the circuit to make sure you don't destroy the components. To ensure that the voltage always gets divided in a balanced way and that the LED or component never gets overloaded and destroyed, I learnt that you need to use pull up and pull down resistors.

### Things I tried on my own virtually
I experimented on TinkerCad with virtual devices as I did not have access to all the different components and it also gave me the opportunity to try different configurations with different components without harming the devices while learning.

I first started with connecting some LEDs to the breadboard and then making them light up thereafter making them blink. My next idea was to create a circuit that will simulate a traffic light, starting with the LED on red it will then move to yellow after a while and then to green, this cycle will continue until the simulation is stopped.

https://user-images.githubusercontent.com/72278511/152381123-5654446c-fbe1-46ce-841e-7403239b3277.mp4

My second idea was for a temperature sensor combined with an RGB LED, the idea was for the LED to show what temperature range the temperature sensor is experiencing, if the temperature is cold the LED would light up in blue, if the temperature is mild the LED would light up in yellow and if the temperature is hot the LED would light up in RED.
In the TinkerCad virtual environment I can use a slider to control the temperature input that the sensor is experiencing.

https://user-images.githubusercontent.com/72278511/152381738-a4098b25-6e2e-413f-bea8-29a17bdddaf2.mp4

### Things I did in conjunction with Group 1
To get started we had to wire the circuits properly using a breadboard, controller and sensors. The ESP and the sensors both needed power and the sensors’ data connection needed to be wired to the ESP for reading.

![KY-013 sensor](https://user-images.githubusercontent.com/72278511/152390311-4e6bee2e-07fe-4878-bb30-382520ad9c0d.jpeg)

We installed various tool for example Arduino IDE, MQTT, Node-red and Iotempower.

Arduino IDE is used to write C++ code that can be flashed onto the ESP device so that it can perform a certain task which in our case was reading sensor values. I worked with pre-made libraries that assist you in working with certain sensors like a temperature sensor and also learnt how to send the values read through to another service.

MQTT is the tool used to communicate between devices, it transports the messages being sent from the ESP to the Node-red dashboard.

![mqtt](https://user-images.githubusercontent.com/72278511/152389700-c9c8e74d-19bb-4c04-86b8-8fdd798b5d70.JPG)

Node-red is the tool we used to interact with the ESP, display its messages and act as a dashboard for our application.

![node red connected](https://user-images.githubusercontent.com/72278511/152389828-e900e126-7404-4b21-9cc3-9d1d7e0ef37b.jpeg)

We successfully followed the steps in the github page to install iotempower via the command line on linux.

![iotempower](https://user-images.githubusercontent.com/72278511/152397717-008fef7d-4031-40b5-94fb-80caa32193d3.jpeg)

In the learning process we ran into a few issues, the first problem was with the ESP32 module, when it connects to wifi it disables many of the ports so we had to solder the data wires onto the ESP32 module itself on very specific ports. The second issue was with the type of sensor we used, we had to choose between a DHT-11 and a KY-013 sensor, the KY-013 only reads temperature, it bases it off of the voltage reading and there is a specific calculation you have to do to get the temperature, it changes in relation to the voltage.

![analog inputs](https://user-images.githubusercontent.com/72278511/152391049-18513594-80b2-4009-b58d-3b094a7efc2f.JPG)

The DHT-11 sensor reads temperature and humidity which was a bit complicated in the beginning so we left it but later we learnt more about how it works and we incorporated it back into the circuit so that we could then read temperature and humidity.

I learnt how to create nodes that listen for incoming data and nodes that display it, I also learnt how to create a dashboard to visualize the incoming data in real time.

![node red nodes](https://user-images.githubusercontent.com/72278511/152391927-1c631b37-75a5-4bf9-be2d-2b27526a4a5b.JPG)

The dashboard for receiving real time data from the ESP32 and MQTT service.

![dashboard](https://user-images.githubusercontent.com/72278511/152391279-0c5c151a-61e9-46eb-bcbc-f3023f15cf7d.JPG)

Some of the challenges faced with the broadcasting of messages and data were that the IP changes on every Wi-Fi network but we soon figured that out and were able to adjust the code so that it successfully subscribes to the nodes on Node-Red and send the data through.
Another issue faced was that the nodes on the Node-Red dashboard wouldn't connect and the reason for that was that you had to re-deploy the entire dashboard after changing any of the nodes, after re-deploying the system the nodes were able to connect to MQTT.

Using all of this to create something useful, we implemented the temperature and humidity reading circuit to send the data to the dashboard in Node-Red with graphs that show the real time data so that you can monitor it wherever you would put it.

https://user-images.githubusercontent.com/72278511/152396848-1bf5b682-7c87-45d4-9445-19227f665104.mp4
