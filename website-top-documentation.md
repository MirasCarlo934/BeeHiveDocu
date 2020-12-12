# Overview

## Things

Things are the entities that make up IoT. They can be anything from bedroom lights, door locks, to streetlamps, and even cars and buildings which transmit and receive data from each other.

In BeeHive, Things are the basic units that make up the IoT universe.

## Attributes

Attributes define the functionality of Things. Each Thing can be broken down into one or more Attributes which outline what they can do and what data they can handle.

A basic example of which is a wallswitch with three individual switches—the wallswitch is the Thing and the three switches are its Attributes. Each switch can be virtualized as three binary Attributes which can either be "on(1)" or "off(0)".

Another analogy would be a TV Thing. Its Attributes can be its 0-to-100 volume and brightness settings, the current channel it's tuned to, and even the total time it's been turned on.

## Groups

Groups are simply containers which "group" Things and other groups together. It's a way to organize your Things so they're easier to look for and navigate to.

Groups can also be a way to group together Things that have a common purpose or context. Like all the lights, switches, and appliances in a bedroom. Or all the temperature sensors in a greenhouse. As such, groups can be a way to generalize data from individual Things or broadcast commands to all Things under the same group.

## High-Level Architecture

*show architecture diagram concerning Things, Attributes, Groups in relation to BeeHive*

# Getting Started

## Create a Thing

Let's get started by creating your own Thing! To do this, you can send this HTTP request to BeeHive:

**curl --location --request PUT "{{thingURL}}" --data-raw "{{thingJSON}}" -H "Content-Type: application/json"**

That's it! You've now created your first BeeHive Thing! Let's break down this request:

You are sending a **PUT** request to BeeHive with the following Thing specifications:

**{** 

 **"userID": "{{userID}}",**

  **"uid": "{{uid}}",**

  **"name": "{{name}}",**

  **"product": null, // do not worry about this for now!**

  **"active": "{{active}}"**

**}**

What this does is that it creates a Thing with the name ***{{name}}*** which is currently active. For this guide, let's assume that your newly created Thing is a simple lightbulb in your bedroom. This Thing is registered under the user ***{{userID}}*** with the UID (unique ID) ***{{uid}}***. *Reloading this page generates a new user ID and UID so remember both if you want to access this Thing later!*

If you enter <u>{{thingURL}}</u> in your web browser, it will show your Thing as it currently exists in BeeHive!

## Adding Attributes

Now you'll want to add a bit of functionality to your Thing. You can do this by adding an Attribute to your current Thing by sending this request:

**curl --location --request PUT "{{attrURL}}" --data-raw "{{attrJSON}}" -H "Content-Type: application/json"**

This adds a new Attribute named ***{{attrName}}*** with the AID (Attribute ID) ***{{aid}}***. You can view this Attribute by entering <u>{{attrURL}}</u> in your web browser. 

Because it's **controllable** and **binary**, you can set this Attribute to either be 1 or 0. We will do this in the next part.

## Set/Get Fields

In order to do something meaningful, you must be able to turn your lightbulb on or off. To do this, you can set the **value** of your ***{{attrName}}*** Attribute:

**curl --location --request PATCH "{{attrValURL}}" --data-raw "1" -H "Content-Type: application/json"**

You just turned your light bulb on! If you access the Attribute on <u>{{attrURL}}</u>, you'll find that your Attribute has updated its value from 0 to 1.

If you send the same request but with a **GET** method and without data:

**curl --location --request GET "{{attrValURL}}" -H "Content-Type: application/json"**

BeeHive will return just the value of your Attribute, without the other Attribute details.

If you notice the pattern, you can do this for other fields as well! And not just on Attribute fields but also Thing fields. If you send this request:

**curl --location --request PATCH "{{thingNameURL}}" --data-raw "\"Awesome Lightbulb Name\"" -H "Content-Type: application/json"**

It will change your Thing's name! You can check it by accessing <u>{{thingURL}}</u>, or more specifically, <u>{{thingNameURL}}</u> if you just want to get the Thing name. You can try sending this request with another name under **--data-raw** to change it to some other name that you want!

## Creating Groups

Finally, you'd want to have a group that will contain your Thing as well as your future Things.

# API

The previous section covers the basics of BeeHive's comprehensive API. To make use of all the fantastic capabilities and functionalities of BeeHive, read the complete API document <u>here</u>.