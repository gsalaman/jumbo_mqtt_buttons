# jumbo_mqtt_buttons
Want to have an external program that emulates the 8x8 button array and sends presses to our jumbotron.

Two sides:  
* webpage that has virtual button array and pushes presses to MQTT broker
* library app that sits under jumbotron like "get_buttons", subscribes to (and consumes) MQTT messages

Can start with just using sniffer to generate presses to see if jumbotron can consume.

Steps:
* define protocol
* tweak "gamepad wrapper" to consume protocol
* test app to for wrapper
* webpage to generate 8x8 buttons

# 1st cut protocol
| Topic | Payload | Notes |
|-------|---------|-------|
| jumbo_press | x,y | x & y are 0-7 |

# Wrapper thoughts
Want to present an interface as close to the button interface as possible.  Maybe "get_mqtt_buttons.read()" rather than "get_buttons.read()"?  Client would  have to change their include and their button statement...

Only one client, so wrapper is simpler than "gamepad wrapper".  Still have input queue, but no "player registration".

Quick proto in ii21?
