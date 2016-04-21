# Network Status Plugin

The NetworkStatus plugin allows you to get network status information.

## How to use

* Import the plugin to your project as explained [here](https://github.com/cobaltians/cobalt/wiki/Plugins-usage)
* Add the cobalt.networkStatus.js to your web JS folder
* Add an html link to the cobalt.networkStatus.js plugin script after the cobalt link in the HEAD tag

### Getting the network status from JavaScript

Use the `cobalt.network.getStatus` shortcut :

    // Somewhere after cobalt initialized
    cobalt.network.getStatus(function(status) {
        cobalt.log('Current connection to the network is: ', status);
    });

Possible network status values are listed in the `cobalt.networkStatus.status` enum :

| Enum field | Value | Description |
| ---------- | ----- | ----------- |
| WIFI | `wifi` | Wifi connection |
| MOBILE | `mobile` | Mobile connection |
| ETHERNET | `ethernet` | Wired Ethernet connection (Android only) |
| VPN | `vpn` | VPN connection (Android only) |
| BLUETOOTH | `bluetooth` | Bluetooth connection (Android only) |
| NONE | `none` | No connection |
| UNKNOWN | `unknown` | Connection type unknown |

### Be warned of status changes

The web can also subscribe to network status changes :

    // First, set the callback function
    cobalt.networkStatus.onStatusChanged = function (status) {
        cobalt.log('Network status changed: ', status);
    };

    // Then, start listening to network changes
    cobalt.networkStatus.startStatusMonitoring();

    // Later on, you can stop listening :
    cobalt.networkStatus.stopStatusMonitoring();

Alternatively, you can set the callback function and start listening at the same time :

    cobalt.networkStatus.startStatusMonitoring(function (status) {
        cobalt.log('Network status changed: ', status);
    });

Note that you can only have one callback defined for each page. Using the shortcut above will simply set `cobalt.networkStatus.onStatusChanged`.

## Want more?

If you have any ideas or improvements to propose, please feel free to do so in the issues tracker!
