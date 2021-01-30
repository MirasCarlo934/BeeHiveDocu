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

# Getting Started

This short tutorial can be run on any command line interface that runs **curl**. By default, latest versions of **Windows 10**, **macOS **, and virtually all flavors of **Linux** have curl installed by default. If you're not sure, please see [this article](https://develop.zendesk.com/hc/en-us/articles/360001068567-Installing-and-using-cURL#install) to check and/or install curl.

*All resources created in this tutorial will be stored in BeeHive. If you want to access them later, take note of their IDs!*

## Create a Thing

Things are the entities that make up IoT. They can be anything from bedroom lights, door locks, to streetlamps, and even cars and buildings which transmit and receive data from each other.

Let's get started by creating your own thing! For now, we'll settle on a virtual thing that you can modify and control. 

To create a thing, enter this to your command line interface:

***curl --location --request PUT "{{thingURL}}" --data-raw "{{thingJSON}}" -H "Content-Type: application/json"***

*(Take note of the UID {{uid}} if you want to access this thing in the future!)*

That's it! You've now created your first BeeHive thing! Let's break down this request:

You are sending a **PUT** request to BeeHive with the following thing specifications:

**{** 

 **"userID": "{{userID}}",**

  **"uid": "{{uid}}",**

  **"name": "{{name}}",**

  **"product": null, // do not worry about this for now!**

  **"active": "{{active}}"**

**}**

What this does is that it creates a thing with the name ***{{name}}*** which is currently active. For this guide, let's assume that your newly created thing is a simple lightbulb in your bedroom. This thing is registered under the user ***{{userID}}*** with the UID (unique ID) ***{{uid}}***. *Reloading this page generates a new user ID and UID so remember both if you want to access this Thing later!*

If you enter <u>{{thingURL}}</u> in your web browser, it will show your thing as it currently exists in BeeHive!

## Adding Attributes

Now you'll want to add a bit of functionality to your thing. You can do this by adding an attribute to your current thing.

Attributes define the functionality of things. Each thing can be broken down into one or more attributes which outline what they can do and what data they can handle.

A basic example of which is a wallswitch with three individual switches—the wallswitch is the thing and the three switches are its attributes. Each switch can be virtualized as three binary attributes which can either be *on(1)* or *off(0)*.

Add a new attribute to your thing by sending this request:

***curl --location --request PUT "{{attrURL}}" --data-raw "{{attrJSON}}" -H "Content-Type: application/json"***

This adds a new attribute named ***{{attrName}}*** with the AID (Attribute ID) ***{{aid}}***. You can view this attribute by entering <u>{{attrURL}}</u> in your web browser. 

Because it's **controllable** and **binary**, you can set this attribute to either be 1 or 0. We'll do this in the next part.

## Set/Get Fields

In order to do something meaningful, you must be able to turn your lightbulb on or off. To do this, you can set the **value** of your ***{{attrName}}*** attribute:

***curl --location --request PATCH "{{attrValURL}}" --data-raw "1" -H "Content-Type: application/json"***

You just turned your light bulb on! If you access <u>{{attrURL}}</u>, you'll find that the attribute has updated its value from 0 to 1.

If you send the same request but with a **GET** method and without data:

***curl --location --request GET "{{attrValURL}}" -H "Content-Type: application/json"***

BeeHive will return just the value of your Attribute, without the other Attribute details.

If you notice the pattern, you can do this for other fields as well! And not just on attribute fields but also thing fields. If you send this request:

***curl --location --request PATCH "{{thingNameURL}}" --data-raw "\"Awesome Lightbulb Name\"" -H "Content-Type: application/json"***

It will change your thing's name! You can check it by accessing <u>{{thingURL}}</u>, or more specifically, <u>{{thingNameURL}}</u> if you just want to get the thing name. You can try sending this request with another name under **--data-raw** to change it to some other name that you want!

### Behavioral Fields

Some fields define the behavior of certain resources. If you remember, the {{attrName}} attribute has the **binary** datatype. If you try to change its value to 100 by sending this request:

***curl --location --request PATCH "{{attrValURL}}" --data-raw "100" -H "Content-Type: application/json"***

It will return an error. Because {{attrName}} is binary, BeeHive will only accept values of 0 or 1. 

We can change the attribute's datatype to be able to accept 100 as a value. If you send this request:

***curl --location --request PATCH "{{attrDataTypeURL}}" --data-raw "{{newAttrDataType}}" -H "Content-Type: application/json"***

It changes the datatype to **number**. This datatype can hold any number value! Should you want to restrict this attribute to take only a prescribed range of values, you can even add **min** and **max** fields to the **constraints** subfield of **datatype**. Try this and test for practice!

## Creating Groups

Finally, you'd want to have a way to organize your things. Groups are containers for things and other groups to be put in.

To create a group, send this request to BeeHive:





# API

The previous section covers the basics of BeeHive's comprehensive API. To make use of all the fantastic capabilities and functionalities of BeeHive, read the API overview <u>here</u>.

