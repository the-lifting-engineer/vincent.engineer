+++
title = "About"
description = "Home Security System"
date = "2021-10-30"
aliases = ["about-us", "about-hugo", "contact"]
author = "Vincent The-Lifting-Engineer"
+++
Why build when you can buy:  
  
I take my privacy very serious, so why should I trust a major firm like Amazon or an obsecure firm like Yi to monitor my house when I know I can build my own system. (I would say and do it better but we all know that is a lie)  
Additionally it should provide a fun challenge and open myself up more to IOT and different protocols such as UDP/TCP and SMTP. It should be noted a big part of the reason why I find it neccesary to build this system isn't because I'm afraid of break ins but more so that when I'm in my bedroom I can't usually hear the doorbell, so having an LED light up will notify me that: yes indeed there is someone at the front door.

What I have so far:  
  
So far the story is pretty short and sweet, using two ESP8266 modules communicating with eachother using UDP I have managed to build a basic detection system.  
One ESP-8266 sits by my front door with an HRC505 PIR attached to it to monitor for movement, if it detects movement it will start the process of connecting with the other ESP-8266 module that is in my bedroom. This module will eventually light up an LED strip notifiying me that someone is at the front door.  
But wait there is more, while sure I spend a fair amount of time in my bedroom, I also spend a lot of time in my yard or garage both places where I can't hear the doorbell to great. Rather than spending more money on more modules and LED strips I figured I could incorporate an emailing service. The benefit being I can always tell if someone is at my front door wether I am home or not.  
A lot of the code is frankensteined together from various sources and made to work, the goal moving forward would be to clean up a lot of the code while gaining a stronger understanding of the current UDP and SMTP that is being used to make everything work.

Future plans:  
  
Swapping out the front door ESP-8266 module with an ESP-32 Camera so I can record an image of the person/item at the front door. Great for letting me know when my amazon package arrives. Plus adding an USB storage device such as an SD car to the setup so I can record videos and save them on local media for later review if weird stuff happened. Kind of like a Tesla. 
Also adding a power supply, seems to be a running trend here, so I can have it run off the wall outlet but incase of an outage it can still continue to operate. 

-The-Lifting-Engineer
