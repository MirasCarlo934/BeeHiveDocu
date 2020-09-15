# Notes

The BeeHive demo exists only as a *Proof-of-Concept*. For context, the demo only runs on one VM instance on a free-tier Google Cloud account. Bugs, downtimes, and slow response rates may occur when using the demo.

## Authentication

Since the demo is only a POC, **no authentication mechanisms are implemented**. The only form of security (if there is any) offered is the use of a *User ID*

The only way to differentiate resources between users is through the use of a user-generated User ID. For this reason, we recommend that you use a v4 UUID string (check out [https://www.uuidgenerator.net/](https://www.uuidgenerator.net/)).

The User ID is implemented only as a means of differentiating the resources between users and is NOT in any way secure. For this reason, we recommend that you use a v4 UUID string (check out [https://www.uuidgenerator.net/](https://www.uuidgenerator.net/)) to achieve a certain level of security through randomness. *We highly discourage the use of sensitive data when using the demo*.

Sample use of User ID:

* [http://35.241.123.200:8080/4c965153-8ffe-4aae-9ecb-c39800a56da5/things/12345678](http://35.241.123.200:8080/4c965153-8ffe-4aae-9ecb-c39800a56da5/things/12345678)
* [http://35.241.123.200:8080/9ff1f01d-49d9-4e1e-a47a-e51519d3f877/things/12345678](http://35.241.123.200:8080/9ff1f01d-49d9-4e1e-a47a-e51519d3f877/things/12345678)

*^ The samples above point to two different things of two different users with the same Thing ID.*

## ID Generation

All user resources (things, attributes, groups, rules) posses a unique ID. **Upon creation of a new resource, the demo users must supply the ID**. The reason for this is to allow easier testing and use (since users can assign any ID they want). An ID can contain the following characters:

* Numbers (0-9)
* Letters (a-z & A-Z)
* Hyphens (-)
* Underscores (_)

*Once BeeHive enters production, ID generation will be automated and users will no longer need to supply IDs for their resources.*

