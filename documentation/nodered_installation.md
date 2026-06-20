<a id="top"></a>
<a id="requirements"></a>
## Installation details for Node Red<br/>

1. [Node Red installation](#requirements)
	- [Persistent storage](#persistent_storage)
 	- [Required Node Red libraries/palettes](#node_red_libraries)
  	- [Timezone setup](#time_zone)
2. [Flow installation](flow_installation.md)


****

## Node Red installation
There are some things required for the Node Red installation itself. <br>
- First; You want your data and settings to survive a reboot, so persistent storage is a must. <br>
- Second; The flow makes use of some node red libraries (or palettes). These need to be installed.<br>
- Third; It is advisable to know if you system is setup with the correct time/date. <br>

These will be explained here. <br>

[Back](../readme.md)

****

<a id="persistent_storage"></a>
### Persistent storage
You need to change some settings in settings.js to enable persistent storage.<br/>
In addition it is a good idea to reduce the frequency of writing to your disk. 

In a (proxmox) docker install, you can find this settings.js file in:
```
/var/lib/docker/volumes/FOLDER/_data
```

On a Raspberry Pi, you can find this settings.js file here:
```
/home/pi/.node-red/settings.js".
```

Look for the **contextStorage:** section.
Modify or put in the text as below:
```
contextStorage: {
	default: "memoryOnly",
	memoryOnly: { module: 'memory' },
	file: { module: 'localfilesystem', config: {flushInterval: '300'}, }
},
```
Reboot Node Red for the changes to be applied.<br/>

> [!IMPORTANT]
> Test and verify if persistent storage is working correctly and see that all settings *stick* after a reboot of Node Red.
> Check if you can find context store "file" within Node Red.

> [!IMPORTANT]
> Please also note that this flow writes to disk every 5 minutes. Storage on sd-card is not advised because of possible high wear levels.

[Top](#top) / [Back](../readme.md)

****

<a id="node_red_libraries"></a>
### Required Node Red libraries/palettes
- To make use of the dashboard functionality, you need to install the dashboard library.<br/>
		https://flows.nodered.org/node/node-red-dashboard <br/>
- The scheduler makes use of the moment lib<br/>
		https://flows.nodered.org/node/node-red-contrib-moment <br/>
- node-red-contrib-dashboard-bar-chart-data<br/>
		https://flows.nodered.org/node/node-red-contrib-dashboard-bar-chart-data <br/>
- node-red-node-smooth<br/>
		https://flows.nodered.org/node/node-red-node-smooth<br/>
- node-red-node-ui-table<br/>
		https://flows.nodered.org/node/node-red-node-ui-table<br/> <br/>
As of **Node Red version 5.0**, Dashboard 1.0 does not come bundled in a clean install anymore. You have to install it manually yourself.<br/>		
- node-red-dashboard<br/>
		https://flows.nodered.org/node/node-red-dashboard<br/>

> [!NOTE]
> The Dashboard 1.0 pallette is indeed deprecated by Node Red. This means it will no longer receive safety fixes, or updates. But it works fine. <br/>
> Again; **It works just fine**... There is no reason to fear it will stop working at all. 

[Top](#top) / [Back](../readme.md)
 
****

<a id="time_zone"></a>
### Timezone setup
If you use a linux version, make sure you set your correct timezone. You can do this by running this command from CLI root and go through the setup process.
```
dpkg-reconfigure tzdata
```
You can check if it was successful by executing this command
```
timedatectl 
```
If you are running Node Red from within HomeAssistant, follow the instructions from HomeAssistant on how to do that.

[Top](#top) / [Back](../readme.md) / [Continue to flow installation](flow_installation.md)

****
