# ouimeaux

Open source control for Belkin WeMo devices

* Free software: BSD license
* Documentation: http://ouimeaux.rtfd.org

## Features

* Supports WeMo Switch, Light Switch, Insight Switch and Motion
* Command-line tool to discover and control devices in your environment
* REST API to obtain information and perform actions on devices
* Simple responsive Web app provides device control on mobile
* Python API to interact with device at a low level

## Installation

`ouimeaux` supports both Python 3 and Python 2. To install, run:

```
$ pip install git+https://github.com/iancmcc/ouimeaux.git
```

This will allow you to use `wemo` and `wemo server`.

Note you may wish to isolate your `ouimeaux` installation, to do so, install
into a virtual environment as follows:
```
# If Python 3:
$ python3 -m venv ouimeaux-env

# If Python 2:
$ python -m pip install virtualenv
$ python -m virtualenv ouimeaux-env

# And then:
$ source ouimeaux-env/bin/activate
$ pip install git+https://github.com/iancmcc/ouimeaux.git
```

Note, if you install into a virtual environment as above, you'll need to have
activated your environment with `source ouimeaux-env/bin/activate` in order to
use `wemo`.

## HTTP client version

The `client.py` script provided by [BlackLight](https://github.com/BlackLight)
allows the user to send simple commands to a device without the cumbersome
(and [currently broken](https://github.com/iancmcc/ouimeaux/issues/193)) `Discoverer`
object.

Requirements: install requests:

```
pip install requests
```

You can run client.py in two modes:

### Scan mode

Will scan for available WeMo Switch devices on the network. Example:

```
python client.py --scan --subnet 192.168.1.0/24
```

### Action mode

Will run an action on a specified device. Example:

```
python client.py --device 192.168.1.19 --on
```

With no `--on|--off|--toggle` action specified the script will return a JSON
with the device info:

```json
{
  "device": "192.168.1.19",
  "name": "Lightbulbs",
  "state": false
}
```

Run `python client.py --help` for more info about the available options.

## Troubleshooting

#### Using a VPN 
The `wemo` command won't be able to communicate with your devices if you're connected to a VPN. It may be redirecting UDP traffic somewhere else. Disconnect from the VPN and the tool should work.

Open an issue and I'll try to help.
