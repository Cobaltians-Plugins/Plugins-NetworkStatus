# Network Status Plugin

NetworkStatus plugin allows you to get network status information.


## How to use

* import the plugin to your project as explained [here](https://github.com/cobaltians/cobalt/wiki/Plugins-usage)
* Add the cobalt.networkStatus.js to your web JS folder
* Add an html link to the cobalt.networkStatus.js plugin script after the cobalt link in the HEAD tag

### Getting the network status from JavaScript

use the `cobalt.network.getStatus` shortcut like this

    //somewhere after cobalt inited
    cobalt.network.getStatus(function(status){
        //TODO 
        //cobalt.log('current connection to the network is :', status.connected)
    });

Current full returned fields are :

| field | type | description |
| ----- | ---- | ----------- |
| TODO | string     | TODO |
| TODO | string     | TODO |

Sample : 

    {
        TODO : "TODO",
        TODO : TODO
    }

### Be warned of status changes

The web can also subscribe to network status changes. For example when the current connection is moving from state `TODO` to state `TODO`.

Here is how to subscribe :

    //somewhere after cobalt inited
    cobalt.network.onStatusChange(function(status){
        //TODO 
        //cobalt.log('new status is', status)
    });


##Want more ?

 * other ideas ? propose yours in the issues tracker
 * ...
