# Network Status Plugin

The NetworkStatus plugin allows you to get network status information.

## How to use

* Import the plugin to your project as explained [here](https://github.com/cobaltians/cobalt/wiki/Plugins-usage)
* Add the cobalt.networkStatus.js to your web JS folder
* Add a html link to the cobalt.networkStatus.js plugin script after the cobalt link in the `<head>` tag

### Getting the network status from JavaScript

Use the `cobalt.networkStatus.getStatus` shortcut :

    // Somewhere after cobalt initialized
    cobalt.networkStatus.getStatus(function (status) {
        cobalt.log('Current connection to the network is: ', status);

        if (status === cobalt.networkStatus.status.WIFI || status === cobalt.networkStatus.status.ETHERNET) {
            // Do something that needs to be done on a fast network
        }
    });

Possible network status values are listed in the `cobalt.networkStatus.status` enum :

| Enum field | Value | Description |
| ---------- | ----- | ----------- |
| WIFI | `wifi` | Wifi connection |
| MOBILE | `mobile` | Mobile connection |
| NONE | `none` | No connection |
| UNKNOWN | `unknown` | Connection type unknown |

*Note*: on Android, connections behind a VPN and over Ethernet are returned as Wifi to match the iOS counterpart behaviour.

### Be warned of status changes

The web can also subscribe to network status changes:

    // First, set the callback function
    cobalt.networkStatus.onStatusChanged = function (status) {
        cobalt.log('Network status changed: ', status);
    };

    // Then, start listening to network changes
    cobalt.networkStatus.startStatusMonitoring();

    // Later on, you can stop listening
    cobalt.networkStatus.stopStatusMonitoring();

Alternatively, you can set the callback function and start listening at the same time:

    cobalt.networkStatus.startStatusMonitoring(function (status) {
        cobalt.log('Network status changed: ', status);
    });

*Note*: you can only have one callback defined for each page. Using the shortcut above will simply set `cobalt.networkStatus.onStatusChanged`.

## Want more?

If you have any ideas or improvements to propose, please feel free to do so in the issues tracker!
