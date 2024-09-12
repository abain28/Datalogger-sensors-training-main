# Dataloggers introduction

A datalogger is an electronic device that collects, processes and stores data from analogue and digital sensors. The logger can also be used to control relays and switches. Unlike a microprocessor such as a Raspberry Pi type device, a logger has multiple input and output ports built-in to facilitate the connection of a large number of different types of sensors. Dataloggers are similar to microcontrollers in that have an operating system and can run a user written program but the hardware and operating system is optimised for collecting and storing data real time from multiple inputs.

Due to their limited market, specialist nature, rugged construction, high quality electronics, thorough testing and calibration, dataloggers cost considerably more than generic processing units. At the time of writing a CR1000X datalogger costs approximately £2000.

To use a datalogger such as this, the user must set up the logger using the manufacturers provided configuration utility before connecting a sensor to the correct input ports. A logger program must then be written to tell the logger:

- What sensors are connected and in what way.
- What data to collect from the sensors.
- How to store the data (the logger uses its internal memory to store as much data as it can).
- How to send the data to a remote server (loggers can also store data to a memory card).
- How often you wish to get data from the sensor.
- Apply any processing to the raw sensor data (e.g. calculating a mean or max value over a time period).

## Campbell Scientific CR1000X

The datalogger most commonly in use within the Met Office at this time is the [Campbell Scientific CR1000X](https://www.campbellsci.eu/cr1000x). This provides multiple interfaces for different types of analogue and digital sensors, a powerful processor with plenty of memory (for a datalogger!), very fast scan rate (for rapid sampling for sensor data) and very low power requirements (allowing solar panel/battery operation).

In addition, this logger has a USB port for connection to a computer and supports modern network protocols for sending out data such as MQTT. Its digital ports can be configured for RS232 and RS485 and its sufficient memory to allow handling of long data strings. You can access the full, online CR1000X manual [here.](https://help.campbellsci.com/CR1000X/Content/Home.htm)

<img alt="CR1000X layout" src="CR1000X_diag.svg" width="700"/>

This logger runs a proprietary real time operating system, it's tolerant of sudden power removal and each logger is tested to operate over a wide (industrial) temperature range. The device uses a 24bit analogue to digital converter (ADC) and has enough memory to handle long data strings, large programs and complex processing. 

To use the datalogger a logger program must be written in "BASIC" like langauge called "CRBasic". This program is loaded onto the logger via USB or over a network link using tools provided by Campbell Scientific. You read more about CRBasic and access all the programming instructions from the online manual [here.](https://help.campbellsci.com/crbasic/cr1000x/)

It is not possible to connect a screen or keyboard etc. to the logger, monitoring and other tasks are carried out using Windows based utility applications. Many of the input "ports" of the logger can be configured using "instructions" within a CRBasic logger program. For example the "Control - C" ports can be configured to operate in RS232 or RS485 mode.

Campbell Scientific also make available a large of number of add-on accessories for the CR1000X such as modems, radio links and modules to increase the number of analogue and digital inputs. In addition, it is also possible to purchase battery backup and solar charging units designed to work with this logger. See the glossary below for links to additional information about these subjects.

There are other dataloggers available on the market, but they are not used within the Met Office at present. An alternative type of device has just been released by Vaisala called the "DMU801". This is basically a small, power efficient Linux device with an ARM processor and running an embedded Linux operating system. Plugin cards provide the required number of analogue and digital inputs. You can read more about the DMU801 [here.](https://www.vaisala.com/en/products/data-management-unit-dmu801)

<img alt="Vaisala DMU801" src="vaisala_DMU801.svg" width="600"/>

## Glossary

Datalogger
: A datalogger, also known as a data logger or data recorder, is a device or system designed to automatically collect, store, and sometimes transmit data over a period of time. It typically consists of sensors to measure various parameters such as temperature, humidity, pressure, light intensity, voltage, current, or other environmental or process variables.

CR Basic
: CRBasic is a programming language developed by Campbell Scientific for programming their data loggers. Some key things to note about CRBasic:
It is a high-level language designed to be easy to use, yet also provide powerful programming capabilities for measurement and control applications.

: CRBasic programs are written using a text editor/programmer called the CRBasic Editor, which is designed for creating, editing, compiling and transferring CRBasic programs to Campbell Scientific data loggers.

: CRBasic programs have a typical structure that includes a header with metadata, tables to declare variables and constants, and measurement, calculation and control instructions.

: Variables can be declared as different data types like Boolean, byte, word and floating point. Arrays and strings can also be used.
Functions can be created to modularize and reuse code. Functions allow breaking programs into logical components to simplify programming and troubleshooting.

: CRBasic supports conditional structures like If/Then/Else and Select Case as well as loops like Do/Loop and For/Next for control applications.
Programs can be compiled in either sequential or pipeline mode to optimize performance for different applications.

: Variables and constants can be public to make them accessible to external programs and devices for easy data retrieval and control.

Campbell Scientific Ltd.
: Campbell Scientific is a company that specializes in data acquisition and measurement systems for various environmental and research applications. They produce a wide range of data loggers, sensors, and telemetry systems used in fields such as meteorology, hydrology, agriculture, ecology, and geology, among others.

: Founded in 1974 by Dr. Gaylon Campbell, the company has become a prominent supplier of instrumentation for environmental monitoring and research. Their products are known for their reliability, accuracy, and ruggedness, making them suitable for use in harsh environmental conditions and remote locations.

Vaisala Oyj.
: Vaisala Oyj, commonly referred to as Vaisala, is a Finnish company that specializes in environmental and industrial measurement. Founded in 1936 by Vilho Väisälä, a Finnish scientist and inventor, Vaisala has grown to become a global leader in providing observation and measurement solutions for weather, environmental monitoring, and industrial applications.

: The company's product portfolio includes a wide range of instruments and systems for measuring various parameters such as temperature, humidity, pressure, carbon dioxide, liquid concentration, wind speed and direction, and weather phenomena. These instruments are used in applications such as weather forecasting, climate research, aviation, renewable energy, pharmaceuticals, and various industrial processes.

: Vaisala is particularly renowned for its weather observation systems, which are widely used by meteorological agencies, airports, and other organizations involved in weather monitoring and forecasting. Their instruments and systems are known for their accuracy, reliability, and durability, making them suitable for use in demanding environments and critical applications.