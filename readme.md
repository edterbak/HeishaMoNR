<a id="top"></a>

<img src="images/dashboard/banner_heishamonr.png" width="1000">
<span style="display:inline-block; margin-right:6px;">
  <a href="https://www.paypal.com/donate?business=ed_terbak%40hotmail.com&no_recurring=0&item_name=Support+my+work&currency_code=EUR">
    <img alt="Donate with PayPal" src="https://img.shields.io/badge/Donate-PayPal-0070ba?style=for-the-badge&logo=paypal&logoColor=white">
  </a>
</span>
<span style="display:inline-block;">
  <a href="https://ko-fi.com/edterbak">
    <img alt="Buy me a Ko‑fi" src="https://img.shields.io/badge/Buy%20me%20a-Ko%E2%80%91fi-FF5E5B?style=for-the-badge&logo=ko-fi&logoColor=white">
  </a>
</span>

********
**Previously called:** Node Red dashboard for Heishamon
<br><br>
**Current version:** v26.5.1 Stable<br>
**Release date:** 2026-05-14

********

<a id="index"></a>
## Table of Content
- [Introduction](#introduction)
- [Gallery](documentation/gallery.md)
- [Requirements](documentation/requirements.md)
- [Installation](documentation/nodered_installation.md)
	- [Node-Red](documentation/nodered_installation.md#node-red-installation)
		- [Persistent storage](documentation/nodered_installation.md#persistent-storage)
 		- [Required Node-Red libraries/pallets](documentation/nodered_installation.md#required-node-red-librariespallets)
  		- [Timezone setup](documentation/nodered_installation.md#timezone-setup)
    - [Flow](documentation/flow_installation.md)
    	- [Import](documentation/flow_installation.md#1-download)
     	- [Adjust settings](documentation/flow_installation.md#3-adjust-settings)
      	- [Deploy](documentation/flow_installation.md#4-deploy-the-flow)
- [Update instructions](documentation/update_instructions.md)
- [Flow configuration](documentation/flow_configuration.md)
  - [Quick start](documentation/flow_configuration_quickstart.md)
  - [Setup Guidelines](documentation/flow_configuration_guidelines.md)
  - [Functions](documentation/flow_configuration_functions.md)
  - [External sensors](documentation/flow_configuration_external_sensors.md)
  - [Tips](documentation/flow_configuration_tips.md)
- [Changes](documentation/changes.md)
- [FAQ](documentation/faq.md)
- [Acknowledgments](documentation/acknowledgements.md)
- [Donations](documentation/donations.md)  

********

## Abstract
`HeishaMoNR` is a **Node-Red flow** which gives you a user friendly dashboard for local control of your Panasonic heat pump.<br>

[Top](#top)

********

<a id="introduction"></a>
## Introduction
You can connect your Panasonic heat pump to the default CZ-TAW1 module. Then you are locked in the Panasonic ecosystem depending on using the wallmounted controller or Aquarea Smart Cloud.

Alternatively you can connect and control your Panasonic heat pump locally with Heishamon. The Heishamon board is created by Egyras. AWESOME job! Get one here: https://www.tindie.com/stores/thehognl/ <br/>
```mermaid
---
config:
  look: handDrawn
  theme: forest
---
flowchart LR
    A((A
		Panasonic    
		Heat pump)) <---> B(B
		Heishamon)
	B <---> C{{C
		MQTT Broker}}
    C <---> D(D
		Node-Red)
	style D fill:#f9f,stroke:#333,stroke-width:4px
```
* []() A > B: The Panasonic heat pump communicates with the heishamon board
* []() B > C: Heishamon communicates with your MQTT broker
* []() C > D: Node-Red communicates with the MQTT broker

I have chosen to use **Node-Red** (=NR) as FrontEnd and automation platform. 
In this repository you will find out all about this Node-Red flow.

[Top](#top)

********

## What can `HeishaMoNR` do for you (the simple benefits)
So, what can it do.
* Offers **local control**. No dependency on Panasonic Cloud at all.
* It provides a nice **dashboard**.
* Shows detailed **graphs and charts** with real‑time or historical data.
* Allows advanced **custom functions** such as CCC, RTC, SoftStart, and Solar‑driven DHW optimizations.
* Works with **any sensor** for the custom functions. 
* **Automations** using schedules with conditions.

### Dashboard examples
Here are just a few images to show the dashboard. For more images look in [the gallery.](documentation/gallery.md)

*Home dashboard*<br>
<img src="images/dashboard/home_01.png" width=70%>
<br>

*RoomTemperatureCorrection function*<br>
<img src="images/dashboard/function_rtc_01.png" width=70%>
<br><br>

[Top](#top)

********


