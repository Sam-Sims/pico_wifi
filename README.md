# pico_wifi
A MicroPython module written for the raspberry pi pico W to connect to a local wifi network.

The module contains functions to connect to a wifi network, as well as a few helper functions to return the status and current IP address.

There are several steps in the micropython network library in order to establish a connection, this module aims to make it cleaner to connect to a wifi network, as well as providing extra functionality such as a LED status indicator.

## Installation:

On a pico W you can use Thonny to copy pico_wifi.py into the main directory using the save function. Alternatively you can use the brilliant [Pico GO](http://pico-go.net/) in VSCode.

## Usage:

### To establish a connection:

```python
connect(ssid, pwd, retry_timeout=10, led_toggle=False, verbose=False)
```
### Arguments:

`ssid`: The network name (ssid) to connect to. Required

`pwd`: The network password. Required

`retry_timeout`: The time to wait before aborting the connection attempt. Optional, Default 10 seconds

`led_toggle`: If true the pico onboard LED will be switched on if a succesful connection is established. Optional, Default is false

`verbose`: If true will print more messages to the console. Optional, Default is false

### Return assigned IP:

```python
get_ip()
```

This will return the IP if an active connection is found, else will raise an error.

## Example:

To connect to a network it is as simple as:

```python
import pico_wifi

ssid = "my_network"
pwd = "my_network_password"

pico_wifi.connect(ssid, pwd)

ip = pico_wifi.get_ip()
```

## Known Issues:

`wlan.status()` reports `STAT_CONNECTING` when the connection is refused due to wrong password instead of the more appropriate and informative `STAT_WRONG_PASSWORD`
