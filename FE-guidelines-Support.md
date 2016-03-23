# Frontend Guidelines

## Support and Optimization
It's important to recognize the difference between ["support" and "optimization"](http://bradfrost.com/blog/mobile/support-vs-optimization/). You should do your best to support as many environments as possible while simultaneously optimizing for the environments that make the most sense for your business and users.

> Browser support, progressive enhancement guidelines

* * *

Code support the notion that all our websites should be device agnostic and should be functional regardless of device used to access.

Being device agnostic, whilst helping us deliver a functional website on all our projects can result in confusion in what is actually meant.

This document will try to provide a bit of clarity and outline some specific browsers and devices as a benchmark and standard to refer to.

This document does not outline every browser and device on the market. the browsers detailed in this document are what we believe to be the most popular browsers. Other browser do exist but are considered to have a minor amount of users.

Code will use the browsers and devices documented here as part of their test process.

Two distinct levels of support are given and denoted next to each browser: ‘compliant’ or ‘functional’. Compliant means that the service should look as good in this browser as in other modern browsers. Functional means that while it might not look perfect the service is still usable. In both cases the user should be able to access the information they need or complete their service.

Where ‘latest version’ is listed, it means the latest stable version plus one version back, as these browsers regularly update without intervention from the user.


## Desktop

| Operating system     |Browser                         |Support    |
|----------------------|--------------------------------|-----------|
|Windows	             |Internet Explorer <=8	          |functional |
|                      |Internet Explorer 9+	          |Compliant  |
|                      |Edge (latest version)	          |Compliant  |
|                      |Google Chrome (latest version)  |Compliant  |
|                      |Mozilla Firefox (latest version)|Compliant  |
|Mac OS X              |Safari 8+	                      |Compliant  |
|                      |Google Chrome (latest version)	|Compliant  |
|                      |Mozilla Firefox (latest version)|Compliant  |


## Small screen devices

|Operating system	  |Version	|Browser	        |Support  |
|-------------------|--------|------------------|---------|
|iOS	              |7+	     |Mobile Safari	    |Compliant|
|Google             |        |Chrome	          |Compliant|
|Android            |4.x     |Google Chrome	    |Compliant|
|Android Browser	  |        |                  |Compliant|
|Windows Phone	    |8.1	   |Internet Explorer	|Compliant|
