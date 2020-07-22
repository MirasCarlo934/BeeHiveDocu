# Services

Currently, BeeHive exists as a proof-of-concept and offers 6 basic services:

- Thing Management Platform
- Product Management Platform
- Automation Engine
- Data Collection and Analytics
- MQTT API
- GUI

## Thing Management Platform

The Thing Management Platform is the heart of BeeHive which manages the registration, management, and control of devices in the BeeHive IoT universe. These devices are referred to as *Things* and will be referred to as such throughout this documentation.

### Things

BeeHive sees Things as unique entities that have discrete functionalities called *Attributes*.

![](images/thing-representation.png)

Conceptually, a Thing can be imagined as a container for tightly-coupled functionalities. With the example above, the wallswitch is fully represented by three attributes which have a "switching" functionality (ie. can be 1 or 0), all of which belong to the same *Thing* which is the wallswitch. 

Device makers must adhere to this Thing model for the devices to fully utilize BeeHive's API. 

### Groups

Groups are a virtual entity which allows for organization of Things based on functionality and/or user preference. Things can be grouped into one or multiple groups and groups can be grouped into other groups.

Beyond simple organization, groups can also be used to collate data from contained Things. See [Automation Engine](#Automation Engine) and [Data Collection and Analytics](#Data Collection and Analytics) for more information on this functionality.

## Product Management Platform

## Automation Engine

## Data Collection and Analytics