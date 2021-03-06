# NodeMCU based temperature and humidity sensor using MQTT

This was built using an ESP8266 and a DHT22.

Because this sensor is compatiable with MQTT, it is also compatible
with the open source home automation platform [Home Assistant](https://www.home-assistant.io/).

In order to use this software, you will need to install the following libraries:

1. MQTT by Joel Gaehwiler
2. DHT by Mark Ruys

These libraries are included as dependencies in the platformio.ini file.

It should also be noted that this was developed using Visual Studio Code with the [PlatformIO](https://platformio.org/) addon.
I reccomend you use platformio since this project was written using its dev style, but it should
work fine if you would like to use the Arduino IDE. You will need to modify some file names and such to fit what
the Arduino IDE requires.

## Usage

This solution is pretty much plug and play. You will need to create a settings.h file containing the following:

```c++
#ifndef Arduino_h
    #include <Arduino.h>
#endif

#ifndef WiFi_h
    #include <ESP8266WiFi.h>
#endif
// #define debug

// General Settings
const int dht_pin = 4;
const int wait = 300e6;                  // this 5 minutes
const int resistence_divisor = 1023.0;   // this will most likely be slightly different for each device due to hardware imperfections
const float max_bat_voltage = 4.2;      // max battery voltage

const float temp_threshold = 0.5;        // temperature retransmit trigger threshold
const float hum_threshold = 0.5;         // humidity retransmit trigger threshold

// WiFi Settings
const char ssid[] = "";
const char pass[] = "";
IPAddress ip(192, 168, 0, 1);  // sets a static IP, more power effecient
IPAddress gateway(192, 168, 1, 1);
IPAddress subnet(255, 255, 255, 0);

// MQTT Settings
const char client_id[] = "";  // unique id for client
const char broker[] = "";     // IP of broker
const char mqtt_user[] = "";
const char mqtt_pass[] = "";
const char will_topic[] = "";
const char publish_topic_temperature[] = "";
const char publish_topic_humidity[] = "";
const char publish_topic_battery[] = "";

```
