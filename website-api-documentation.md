# Overview

The BeeHive API revolves around the management of four main resources:

1. Things
2. Attributes
3. Groups
4. Rules

This documentation aims to familiarize you on how to use the BeeHive API, primarily through REST (HTTP) and MQTT.

## When to use REST or MQTT?

The REST API is built on top of HTTP which makes it the choice for administrative jobs (eg. creating a new thing, modifying resources). MQTT is focused more on real-time data transmission, particularly on controlling things (ie. changing attribute values).

At its core, the entire BeeHive API is built on REST. However, HTTP can be expensive and slow for low-power devices (ie. things) so a part of the REST API is interfaced by MQTT to provide an optimal solution for transferring small data to and from devices.

As a rule of thumb, if it's a human that will interact with BeeHive, use REST. For things interacting with BeeHive, use MQTT.

## How to Read this Documentation

BeeHive API is split into two: REST and MQTT. 

# REST

The REST API is built on top of HTTP and follows the standard of using **URLs** and **request methods** as the main interface of the API.

**URLs** form the means of traversing the API and accessing resources. Each URL supports specific **request methods** which allow you to perform actions that BeeHive will execute.

## Resources

This aspect of the REST API is concerned with the access and management of specific resources in your BeeHive IoT universe.

### URL

{host}:{port}/{userID}/{resourceName}/{resourceID}

1. Thing - {host}:{port}/{userID}/things/{thingID}
   1. Sample: http://35.241.123.200:8080/testUser/things/testThingID1
2. Attribute - {host}:{port}/{userID}/attributes/{attributeID}
   1. Sample: http://35.241.123.200:8080/testUser/attributes/testAttributeID1
3. Group - {host}:{port}/{userID}/groups/{attributeID}
   1. Sample: http://35.241.123.200:8080/testUser/groups/testGroupID1
4. Rules - {host}:{port}/{userID}/rules/{attributeID}
   1. Sample: http://35.241.123.200:8080/testUser/rules/testRuleID1

### Methods

1. GET {URL}
   1. retrieves all information of the resource
   2. retrieves all relevant resources of this particular resource (eg. thing attributes, things contained in the specified group)
   3. retrieves relevant actions for the resource (eg. assign thing to a group)
   4. Sample: http://35.241.123.200:8080/testUser/things/testThingID1
      1. The links under *_links* contains the relevant resources and actions
2. POST {URL}
   1. adds the resource (if it doesn't exist yet)
   2. returns an error if the URL already contains a resource
   3. **NOTE:** the body of the POST request follow the JSON structure returned by the GET method, without the *_links* field.
3. PATCH {URL}
   1. updates the resource (if it already exists)
   2. returns an error if the URL does not contain a resource
4. PUT {URL}
   1. adds the resource if it doesn't exist yet, updates it otherwise
5. DELETE {URL}
   1. deletes resource at specified URL

### Sample Requests

## 

