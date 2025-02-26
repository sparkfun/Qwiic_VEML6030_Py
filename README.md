![Qwiic VEML6030 Python Package](docs/images/veml6030-gh-banner-py.png "qwiic VEML6030 Python Package" )

# SparkFun Qwiic VEML6030 - Python Package

![PyPi Version](https://img.shields.io/pypi/v/sparkfun_qwiic_veml6030)
![GitHub issues](https://img.shields.io/github/issues/sparkfun/qwiic_veml6030_py)
![License](https://img.shields.io/github/license/sparkfun/qwiic_veml6030_py)
![X](https://img.shields.io/twitter/follow/sparkfun)
[![API](https://img.shields.io/badge/API%20Reference-blue)](https://docs.sparkfun.com/qwiic_veml6030_py/classqwiic__veml6030_1_1_qwiic_v_e_m_l6030.html)

The SparkFun Qwiic VEML6030 Ambient Light Sensor provides a high accuracy and cost effective solution for adding light sensing to your project. Implementing a SparkFun Qwiic I2C interface, these sensors can be rapidly added to any project with boards that are part of the SparkFun Qwiic ecosystem.

This repository implements a Python package for the SparkFun Qwiic VEML6030. This package works with Python, MicroPython and CircuitPython.

### Contents

* [About](#about-the-package)
* [Getting Started](#getting-started)
* [Installation](#installation)
* [Supported Platforms](#supported-platforms)
* [Documentation](https://docs.sparkfun.com/qwiic_veml6030_py/classqwiic__veml6030_1_1_qwiic_v_e_m_l6030.html)
* [Examples](#examples)

## About the Package

This python package enables the user to access the features of the VEML6030 via a single Qwiic cable. This includes reading ambient light in lux, setting gain, setting integration time and more. The capabilities of the VEML6030 are each demonstrated in the included examples.

New to qwiic? Take a look at the entire [SparkFun qwiic ecosystem](https://www.sparkfun.com/qwiic).

### Supported SparkFun Products

This Python package supports the following SparkFun qwiic products on Python, MicroPython and Circuit python. 

* [SparkFun Atmospheric Sensor Breakout - VEML6030](https://www.sparkfun.com/sparkfun-ambient-light-sensor-veml6030-qwiic.html)

### Supported Platforms

| Python | Platform | Boards |
|--|--|--|
| Python | Linux | [Raspberry Pi](https://www.sparkfun.com/raspberry-pi-5-8gb.html) , [NVIDIA Jetson Orin Nano](https://www.sparkfun.com/nvidia-jetson-orin-nano-developer-kit.html) via the [SparkFun Qwiic SHIM](https://www.sparkfun.com/sparkfun-qwiic-shim-for-raspberry-pi.html) |
| MicroPython | Raspberry Pi - RP2, ESP32 | [SparkFun RP2040 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-rp2040.html), [SparkFun RP2350 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-rp2350.html), [SparkFun ESP32 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-esp32-wroom-usb-c.html)
|CircuitPython | Raspberry Pi - RP2, ESP32 | [SparkFun RP2040 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-rp2040.html), [SparkFun RP2350 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-rp2350.html), [SparkFun ESP32 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-esp32-wroom-usb-c.html)

> [!NOTE]
> The listed supported platforms and boards are the primary platform targets tested. It is fully expected that this package will work across a wide variety of Python enabled systems. 

## Installation 

The first step to using this package is installing it on your system. The install method depends on the python platform. The following sections outline installation on Python, MicroPython and CircuitPython.

### Python 

#### PyPi Installation
The package is primarily installed using the `pip3` command, downloading the package from the Python Index - "PyPi". 

Note - the below instructions outline installation an Linux-based (Raspberry Pi) system.

First, setup a virtual environment from a specific directory using venv:
```sh
python3 -m venv path/to/venv
```
You can pass any path as path/to/venv, just make sure you use the same one for all future steps. For more information on venv [click here](https://docs.python.org/3/library/venv.html).

Next, install the qwiic package with:
```sh
path/to/venv/bin/pip3 install sparkfun-qwiic-veml6030
```
Now you should be able to run any example or custom python scripts that have `import qwiic_veml6030` by running e.g.:
```sh
path/to/venv/bin/python3 example_script.py
```

### MicroPython Installation
If not already installed, follow the [instructions here](https://docs.micropython.org/en/latest/reference/mpremote.html) to install mpremote on your computer.

Connect a device with MicroPython installed to your computer and then install the package directly to your device with mpremote mip.
```sh
mpremote mip install github:sparkfun/qwiic_veml6030_py
```

If you would also like to install the examples for this repository, issue the following mip command as well:
```sh
mpremote mip install --target "" github:sparkfun/qwiic_veml6030_py@examples
```

### CircuitPython Installation
If not already installed, follow the [instructions here](https://docs.circuitpython.org/projects/circup/en/latest/#installation) to install CircUp on your computer.

Ensure that you have the latest version of the SparkFun Qwiic CircuitPython bundle. 
```sh
circup bundle-add sparkfun/Qwiic_Py
```

Finally, connect a device with CircuitPython installed to your computer and then install the package directly to your device with circup.
```sh
circup install --py qwiic_veml6030
```

If you would like to install any of the examples from this repository, issue the corresponding circup command from below. (NOTE: The below syntax assumes you are using CircUp on Windows. Linux and Mac will have different path seperators (i.e. "/" vs. "\"). See the [CircUp "example" command documentation](https://learn.adafruit.com/keep-your-circuitpython-libraries-on-devices-up-to-date-with-circup/example-command) for more information)
```sh
circup example qwiic_veml6030\qwiic_veml6030_ex1_basic_readings
circup example qwiic_veml6030\qwiic_veml6030_ex2_settings
circup example qwiic_veml6030\qwiic_veml6030_ex3_threshold_interrupts
circup example qwiic_veml6030\qwiic_veml6030_ex4_power_saving
```

Example Use
 ---------------
Below is a quickstart program to print ambient light measurements in lux.

See the examples directory for more detailed use examples and [examples/README.md](https://github.com/sparkfun/qwiic_veml6030_py/blob/main/examples/README.md) for a summary of the available examples.

```python
import qwiic_veml6030
import time
import sys

def runExample():
	print("\nQwiic Ambient Light Sensor Example 1 - Basic Readings\n")

	# Create instance of device
	light_sensor = qwiic_veml6030.QwiicVEML6030()

	# Check if it's connected
	if light_sensor.is_connected() == False:
		print("The device isn't connected to the system. Please check your connection", \
			file=sys.stderr)
		return

	# Initialize the device
	light_sensor.begin()

	# Loop forever
	while True:
		# Give some delay between prints
		time.sleep(1)

		# Get light measured by sensor in lux
		ambient_light = light_sensor.read_light()

		# Print measurement
		print("Lux:\t%.1f" % ambient_light)
```
<p align="center">
<img src="https://cdn.sparkfun.com/assets/custom_pages/3/3/4/dark-logo-red-flame.png" alt="SparkFun - Start Something">
</p>
