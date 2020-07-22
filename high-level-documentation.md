# Device Lifecycle

IoT devices typically follow the following lifecycle:

1. Development
2. Production
3. End-user Procurement
4. Set-up and Use
5. Post-production
6. Obsoletion

![](images/device-lifecycle.png)

BeeHive concerns itself in three phases in this lifecycle: **Development**, **Set-up and Use**, and **Post-Production**.

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

### Attributes

An Attribute is the most basic unit of functionality of a Thing. There are 4 attribute types:

- binary (1 or 0)
- number (64-bit integer or double)
- enumeration (user-defined enum values)
- string

BeeHive views attributes as a direct interface between a Thing and its real-world functionality/ies. BeeHive manipulates attributes as its way of manipulating the functionality/ies of the Thing that contains them.

### Groups

Groups are a virtual entity which allows for organization of Things based on functionality and/or user preference. Things can be grouped into one or multiple groups and groups can be grouped into other groups.

Beyond simple organization, groups can also be used to collate data from contained Things. See [Automation Engine](#Automation Engine) and [Data Collection and Analytics](#Data Collection and Analytics) for more information on this functionality.

## Product Management Platform

The Product Management Platform caters specifically to makers that look to mass-produce their Things for the public. This service offers the ability for makers to create and manage *Products* and other maker-related tools such as OTA firmware updating.

### Products

A Product can be imagined as an archetype for Things. It outlines Attributes which a Thing will contain upon registration to the BeeHive IoT universe.

When an end-user procures a Thing from the maker, they will need to register it to BeeHive to use it. Traditionally, the Thing can register its Attributes itself. But this results to an after-market limitation in which the Thing's Attributes can no longer be updated once it leaves the production line. Instead of this, a Thing can register its Product instead, which the maker can manage via the Product Management Platform. This allows for makers to manage their Things' functionalities even after production.

### OTA

Makers can also update the firmware of their Things post-production via the OTA service of the Product Management Platform. The firmware is delivered via HTTP which the Thing needs to request from the BeeHive server, the URL of which is defined in the Product of the Thing.

## Automation Engine

## Data Collection and Analytics

## MQTT API

## GUI