# Overview

The BeeHive API revolves around the management of four main resources:

1. Things
2. Attributes
3. Groups
4. Rules

This documentation aims to familiarize you on how to use the BeeHive API, primarily through REST (HTTP) and MQTT.

## When to use REST or MQTT?

The **REST API** is built on top of HTTP which makes it the choice for administrative jobs (eg. creating a new thing, modifying resources). The **MQTT API** is focused more on real-time data transmission, particularly on controlling things (ie. changing attribute values).

At its core, the entire BeeHive API is built on REST. However, HTTP can be expensive and slow for low-power devices (ie. things) so a part of the REST API is interfaced by MQTT to provide an optimal solution for transferring small data to and from devices.

As a rule of thumb, if it's a human that will interact with BeeHive, use REST. For things interacting with BeeHive, use MQTT.

# REST

The REST API is built on top of HTTP and follows the standard of using **URLs** and **request methods** as the main interface of the API.

Standard REST conventions use **five HTTP methods** or ***verbs*** that are commonplace in HTTP communication. These HTTP verbs correspond to Create, Read, Update, and Delete (CRUD) operations:

1. GET (Read)
2. POST (Create)
3. PATCH (Update)
4. PUT (Create/Update)
5. DELETE (Delete)

These methods are then used on HTTP requests to specific **URLs** which contain a unique resource (ie. thing, attribute, etc.) or collections of resources.

### How to Read this Section

The API structure is intuitive enough that, with just a short read, you should be able to grasp the general idea of how to traverse and use the REST API. As such, it is very much recommended that you [try out the REST API first]() instead of immediately referring to this documentation.

## Collections

### URL

{host}:{port}/{userID}/{resourceName}

1. Things - {host}:{port}/{userID}/things/{thingID}
   1. Sample: http://35.241.123.200:8080/testUser/things/testThingID1
2. Attributes (of a thing) - {host}:{port}/{userID}/things/{thingID}/attributes/{attributeID}
   1. Sample: http://35.241.123.200:8080/testUser/attributes/testAttributeID1
3. Groups - {host}:{port}/{userID}/groups/{attributeID}
   1. Sample: http://35.241.123.200:8080/testUser/groups/testGroupID1
4. Rules - {host}:{port}/{userID}/rules/{attributeID}
   1. Sample: http://35.241.123.200:8080/testUser/rules/testRuleID1

***NOTE:*** *Notice that the attribute URL is different. This is because attribute IDs are designed to only be unique to a thing (ie. attributes can have the same ID if they're in different things).*

### URL

{host}:{port}/{userID}/{resourceName}/{resourceID}

1. Thing - {host}:{port}/{userID}/things/{thingID}
   1. Sample: http://35.241.123.200:8080/testUser/things/testThingID1
2. Attribute - {host}:{port}/{userID}/things/{thingID}/attributes/{attributeID}
   1. Sample: http://35.241.123.200:8080/testUser/attributes/testAttributeID1
3. Group - {host}:{port}/{userID}/groups/{attributeID}
   1. Sample: http://35.241.123.200:8080/testUser/groups/testGroupID1
4. Rules - {host}:{port}/{userID}/rules/{attributeID}
   1. Sample: http://35.241.123.200:8080/testUser/rules/testRuleID1

***NOTE:*** *Notice that the attribute URL is different. This is because attribute IDs are designed to only be unique to a thing (ie. attributes can have the same ID if they're in different things).*

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

#### Get

1. 

## 

