# Overview

The backbone of BeeHive's API is a RESTful API built with ease-of-use and intuitiveness as the top priority. At its base, the API is split into its four main (current) services:

*show high-level API diagram here*

Under each service are the resources that they manage. As an example, the Thing Management Platform has three resources: Things, Attributes, and Groups. Access to these resources follow an intuitive hierarchical URL navigation.

*show URL navigation here*

Performing actions on a resource is simply making use of the standard HTTP methods, which are defined as:

*show HTTP method table here*

Usage of the API basically follows these core mechanisms. When changing the name of an Attribute, you can send a **PATCH** request to **{userID}/things/{UID}/attributes/{attributeID}/name** with the new name in the request body. To get a specific automation rule, simply send a **GET** request to **{userID}/rules/{ruleID**}. And if you want to get ALL the rules, just reduce the URL to **{userID}/rules**.

## REST

REST, or Representational State Transfer, is a software architecture style which enforces the idea that all resources must be accessible via their individual URL. 

Aside from this, REST also enforces the concept of **HATEOAS** which basically means that the API must be traversable within itself. This means that, in BeeHive's context, all relevant information and actions performable on a resource are described in the HTTP response for the said resource. 

For example, first make a new Thing:

**curl --location --request PUT "{{thingURL}}" --data-raw "{{thingJSON}}" -H "Content-Type: application/json"**

*(or access the one you created in the Getting Started page)*

If you enter the URL ***{{thingURL}}*** in your web browser, you'll find a field named **_links** which contains all the relevant stuff to the Thing you're viewing along with the URL to access them.

This HATEOAS principle is followed by BeeHive's API, essentially removing the need for reading long and repetitive API documents just to understand how to use the API.



# How Do I Get My Thing to Talk With BeeHive?

The MQTT API is the backbone of the Thing-to-BeeHive interface. MQTT is a lightweight, publish-subscribe communication protocol that is ideal for handling communication between Things and BeeHive. *This is the recommended API for communication between Things and BeeHive.*

## MQTT vs HTTP

While BeeHive can be completely interacted with using the HTTP RESTful API, HTTP is considered a very cumbersome protocol to use mainly due to the following:

1. Heavy data overhead (e.g. HTTP headers)
2. Slower compared to lower-level protocols (TCP)
3. Unidirectional communication (BeeHive servers can't send to a Thing via HTTP)
   - For Things to get updates from BeeHive, they will have to constantly request and request and request and request...

MQTT mitigates these problems by running on top of TCP. It is also lightweight with a small code footprint, requiring small processing power to run. Because of these, MQTT is considered to be ideal for Things.



# Thing Management Platform

The Thing Management Platform manages three resources: Things, Attributes, and Groups:

*show resource breakdown*

## Thing

*show base fields and performable methods*

## Attribute

*show base fields and performable methods*

## Group

*show base fields and performable methods*



Full API documentation: https://documenter.getpostman.com/view/11218501/SztEY6Ao



# Automation Engine

The Automation Engine manages all the automation rules, or *Rules* for short, that govern all Things in a user's BeeHive IoT universe. Rules dictate how Things interact with each other based on changes in their Attributes.

*show how rules work*

## Rule

*show base fields and performable methods*

Rule execution is *event-based*. Rules are only evaluated and executed when a Thing's Attribute changes value.

{{ruleJSON}}

The JSON above is an example of a Rule. It declares two (2) Attributes: *Attribute **{{ruleJSON.attributes[0].aid}}*** of *Thing **{{ruleJSON.attributes[0].uid}}*** and *Attribute **{{ruleJSON.attributes[1].aid}}*** of *Thing **{{ruleJSON.attributes[1].uid}}***. The first Attribute is declared as a ***condition Attribute*** which means it's to be monitored for its value change to evaluate whether or not the Rule executes.

The next part is the *condition block* which contains ***{{ruleJSON.condition}}***. If this condition is satisfied, the Rule executes the *action **{{ruleJSON.actions}}***.  

To test this rule, let's set-up our Things first:

{{ruleThingsPutCURL}}

If you send the Rule JSON above to BeeHive:

{{rulePutCURL}}

It will add the Rule with the RID (Rule ID) ***{{rid}}***. Now, try changing the value of the condition Attribute:

{{ruleAttrValueChangePutCURL}}

Upon accessing the value of the other Attribute:

{{ruleAttrValueGetCURL}}

You'll see that the Attribute value changed! You can play around these two Attributes to further see how your sample Rule runs.

### Cascaded Rules

Because of the way Rules operate, you can set-up a collection of Rules that are dependent on the execution of other Rules. If **Rule 1** changes *Attribute 2* based on the value of *Attribute 1*, you can create **Rule 2** that changes *Attribute 3 and 4* based on the value of *Attribute 2*. BeeHive intelligently *cascades* these Rules together for a seamless operation.

*show cascaded rules diagram*

BeeHive is also smart enough to warn you of any circular references to your Rules.

*show circular rules diagram*

By default, Rules that have action Attributes that are the condition Attributes of Rules preceding it in the Rule cascade chain will not be accepted by BeeHive.

It's important to keep track of your Rules, especially when making use of cascaded Rules. While circular references can be easily avoided, BeeHive does not warn about *spaghettified* Rule chains!

Using Rules, you can set-up the functionality of your entire IoT universe without having to think about interconnecting your Things or how to send data between them. *With BeeHive, you have centralized control over the entire IoT universe.*



For more details on how to manage Rules and the Rule Engine API, please refer to: https://documenter.getpostman.com/view/11218501/SztEY6hi



# Data Analytics

The Data Analytics service manages the collection and analysis of relevant data from Things. 

**Currently**, the Data Analytics service keeps a record of *Attribute value history* and *Thing active state history* and performs basic data analysis over these records like *MIN/MAX/AVE* and *time spent* on a specific value or state. It also keeps a record of MQTT transactions between Things and BeeHive for network monitoring purposes.

For a list of all functionalities of the Data Analytics service, please refer to its API document: https://documenter.getpostman.com/view/11218501/SztEY6hj



