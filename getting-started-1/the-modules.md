# The Modules

The modules are representing all the other softwares and devices you will interact with in your project.

They are divided in main categories representing different types of interfaces. Chataigne provides both dedicated modules for supported softwares and devices with preconfigured control for ease of use, and general modules for allowing control of anything else.

## Anatomy of a Module

Here is the inspector view of an Procol::OSC Module

![](http://benjamin.kuperberg.fr/chataigne/docs/wiki/images/module.png)

### Header

When selecting a module, you can find at the very top a header with some controls. You can here choose to enable/disable the module. When a module is disabled, it will not update or send anything. Depending on whether the module is able to receive and/or send data, you can choose to activate/deactivate the logging of all data received and/or sent from this module. If enabled, you'll be able to check in the Logger panel what's going on with this module.

### Parameters

This section provides all the needed parameters to configure the modules, such as Host and port configuration for network modules, or device name for MIDI controllers, etc. You can find more about a particular module's parameter in its dedicated page.

### Values

This is an important part of the module. The values are all the elements that you will be able to use when creating interactions. Each module has its own set of values, and some modules don't have any if they're not supposed to receive anything or if the Input parameter is deactivated \(for network module for instance\).

### The Scripts

The script section allows you to create more complex logic for this module. You can find more about scripts in the dedicated Scripts page.

### The Command Tester

The command tester is a handy tool to be able to test the functionality of your module by sending commands manually. It is not affecting the rest of the software, and allows you to just verify that the communication between Chataigne and your software or device is functionning properly.

## The Categories

### Protocol

The Protocol category contains all the general purpose modules, so you can configure yourself all the control you need and not be limited to the existing supported softwares and devices.

### Hardware

The Hardware category contains different devices you may want to connect to.

### Software

The Software category contains different softwares already supported that you can already easily use with premade commands

### Generator

The Generator category contains simple signal and trigger generators for general purpose.

### System

The System category contains useful modules for controlling your OS, waking up computers or checking the time of day, the current OS, etc.

