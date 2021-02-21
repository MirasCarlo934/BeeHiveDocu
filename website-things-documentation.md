# Controlling Things in BeeHive

At this point, you already know the basics of things and attributes. A thing is a device, and its attributes are its functionalities. Let's go back to the wallswitch analogy:

[show wallswitch analogy image]

Each switch of the wallswitch corresponds to an attribute which can occupy one of two states: *on(1)* or *off(0)*. From the [previous tutorial](), you've learned how to change the state of an attribute by changing its *value* through HTTP request calls. With this in mind, a *smart wallswitch* can send the state of its individual switches to BeeHive, which keeps a record of it accordingly.

*But what if it's the other way around?*

What if you want to *control* the wallswitch *from BeeHive*?

[show virtual thing diagram]

An important aspect of IoT is control—being able to control your things in other ways than merely walking up to and interacting with them. Having a smart wallswitch means also having the means to control it via a phone app, web dashboard, et cetera. So how does this work in BeeHive?

# MQTT

Message Queueing Telemetry Transport (MQTT) is a protocol on top of TCP/IP that is a favorite in IoT applications. It follows a *publish-subscribe* paradigm in which things can publish and subscribe to certain channels (or *topics* in MQTT-speak) in order to transmit and receive data.

[basic MQTT workflow]

MQTT allows for a lightweight and easy-to-use protocol for exchanging data in an IoT universe. It has a small code footprint and is already ported to libraries of major programming languages like C and Java. BeeHive makes use of MQTT to communicate with things.

[BeeHive MQTT architecture]

## MQTT API

Aside from REST, BeeHive also has an API built on top of MQTT. This API focuses on communicating thing states, primarily their attribute states. While the MQTT API is only limited to this function, its advantage over REST is that it is lightweight and allows things to send and receive data without sending bulky and time-consuming HTTP requests.

Before anything else, we recommend that you 

There are really only two things you need to know to use the MQTT API: the *topic* and the *message*.

