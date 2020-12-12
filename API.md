# Overview

### Things

BeeHive sees Things as unique entities that have discrete functionalities called *Attributes*.

![](/Users/carlomiras/Documents/Symphony/git/BeeHiveDocu/images/thing-representation.png)

Conceptually, a Thing can be imagined as a container for tightly-coupled functionalities. With the example above, the wallswitch is fully represented by three attributes which have a "switching" functionality (ie. can be 1 or 0), all of which belong to the same *Thing* which is the wallswitch. 

This Thing model forms the basis of BeeHive's API and works to either monitor, analyze, and control Things by manipulating these Attributes.

### Attributes

An Attribute is the most basic unit of functionality of a Thing. There are 4 attribute types:

- binary (1 or 0)
- number (64-bit integer or double)
- enumeration (user-defined enum values)
- string

BeeHive views attributes as a direct interface between a Thing and its real-world functionality/ies. BeeHive manipulates attributes as its way of manipulating the functionality/ies of the Thing that contains them.

### Groups

Groups are a virtual entity which allows for organization of Things based on functionality and/or user preference. Things can be grouped into one or multiple groups and groups can be grouped into other groups.

Beyond simple organization, groups can also be used to collate data from contained Things. See [Automation Engine API](https://documenter.getpostman.com/view/11218501/SztEY6hi) and [Data Collection and Analytics API](https://documenter.getpostman.com/view/11218501/SztEY6hj) for more information on this functionality.

# Get Started

To get started, you can try creating your own Thing by making a POST request to this URL:

http://35.241.123.200:8080/test/things/{uid}

In this example, your userID is {userID} and your Thing UID is {uid}. *Save these values somewhere if you want to access them later.*



# Visualization

It is helpful to visualize the API on how data can be accessed:



This API structure follows the REST specifications with a simple and structured API based on the data hierarchy.

