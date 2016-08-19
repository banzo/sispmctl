sispmctl python wrapper
===========

This quick extension enables rudimentary control for sispmctl.

Installation
-------

Install sispmctl (debian-like systems)

```
sudo apt-get install sispmctl
```

Install this wrapper with `pip` (or from source): 

```
pip install sispmctl
```

Usage
--------

First get your device serial number:

```
$ sispmctl -s
Gembird #0
USB information:  bus 001, device 004
device type:      4-socket SiS-PM
serial number:    XX:XX:XX:XX:XX
```

Then inside your python script:

```
from sispmctl import SisPM
device = SisPM(serial="XX:XX:XX:XX:XX", binary="/usr/local/bin/sispmctl")
# get status of all outlets  
device.get("all") # example result: {1: True, 2: True, 3: True, 4: True}
# turn on outlet 1
device.on(1)
```

Misc
-----

To run the script as regular user on debian-like systems:

```
sudo groupadd -f --system usb
sudo chgrp usb /usr/local/bin/sispmctl
sudo chmod u=rwxs,g=rx,o= /usr/local/bin/sispmctl
sudo usermod -a -G usb <username>
# logout and log back in as `<username>` to be able to run sispmctl without sudo
exit 
```

References
-------

* SiS-PM  (Silver Shield PM) Control for Linux 3.0 http://sispmctl.sourceforge.net/#mozTocId127686