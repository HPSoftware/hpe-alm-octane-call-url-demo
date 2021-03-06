# Micro Focus ALM Octane Trigger Webhook/REST API Demo

This project is a simple [node.js](http://nodejs.org) project that demonstrates using Micro Focus ALM Octane's *Trigger Webhook* to call
an external system and Octane's REST API to call back and change a field with Octane.

This project demonstrates how a loop can be built that enables Octane to integrate with any external system that supports
REST calls.

For more information about *Trigger Webhook* and the *REST API* please see Octane's documentation.  Note this functionality 
was previously called *Call URL*.

This project uses the [alm-octane-js-rest-sdk](https://github.com/MicroFocus/alm-octane-js-rest-sdk) project that enables
easy integration with REST APIs.

## Use Case
* A UDF is created for a *defect* called *rework_counter_udf*.  This field is of type number.
* A *Trigger webhook* business rule is created for *defects*.  The rule has a condition that the *Phase* field is modified.
 When the defect is updated the URL `server:port/calculator` resource is called
* Using the UDF label name, add it to the Fields

![](.images/octanerule.png?raw=true)
* This node.js server listens to that URL and if the phase was either **fixed** or **closed** and is now **opened** then
it will get the *rework_counter_udf* field from the calling *defect* and update the number by 1

## Installation
* Make sure that you have at least version 12 of node.js installed
* Run `npm install` on the root of the project
* Update the *configuration.json* file in the root of the project with the correct details of the Octane server.
  * You have a choice of using either client_id/secret authentication (recommended) or user/pass  
* Run the server using the `node bin/www` command

## License
Apache 2.0

## Disclaimer
Certain versions of software accessible here may contain branding from Hewlett-Packard Company (now HP Inc.) and Hewlett Packard Enterprise Company.  As of September 1, 2017, the software is now offered by Micro Focus, a separately owned and operated company.  Any reference to the HP and Hewlett Packard Enterprise/HPE marks is historical in nature, and the HP and Hewlett Packard Enterprise/HPE marks are the property of their respective owners.
