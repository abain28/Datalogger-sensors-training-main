# Sensors overview

In the Met Office we use a variety of sensors to measure meteorological parameters such as temperature,
wind speed, pressure etc. Whilst these sensors can vary greatly in design and the technology used to measure
these parameters, they can be divided into two categories based upon how they present their data output to
the end user; **analogue** or **digital**. The type of output determines how we can connect to and record data
from the sensor.

## Analogue sensors

This type of sensor outputs a voltage, current, resistance or frequency pulse that varies proportionally and
in a predictable manner with parameter being measured. This output has to accurately measured and then
converted to an actual reading (e.g. temperature, humidity, wind speed) by e.g. a datalogger. Example of
output ranges include 0-20mV and 0-1v for a voltage output. The sensor may have a built-in amplifier to lift
the output to a more easily measurable range such as 0-5v.

## Examples of analogue sensors

* HMP110 humidity sensor outputs 0v at 0% humidity and 1v at 100% humidity. This sensor can also be configured
  to output a digital reading. Two analogue outputs are provided, one for humidity and the other for
  temperature from the inbuilt Pt1000 electrical resistance sensing element.
  <img alt="HMP110 Humidity and temperature probe" height="40" src="HMP110.jpeg" width="40"/>
* CMP10 solar radiation pyranometer. A thermopile sensing element generates a 0-20 millivolt output from
  incoming short wave solar radiation. No analogue signal amplification occurs. This device is also available
  in a digital version.
  ![CMP10 Solar radiation sensor](CMP10.jpeg)
* Pt100 temperature sensor. This consists of a film of platinum embedded in a protective sheath, whose
  electrical resistance varies in a known manner with temperature. The "Pt" refers to platinum and the "100"
  refers to its resistance at 0°C in ohms. As temperature increases, the resistance increases in a precisely
  defined, linear manner.
  ![TempVue10](TempVue10.png)

## Digital sensors

These sensors transmit an actual reading of the parameter being measured e.g. `21.3` often in the form of
an [ASCII](#glossary) formatted text string e.g.

`T= 21.3 C  H= 79 % P= 1012.5 hPa`

but the data could also be in a binary format message or protocol e.g. ModBus, UMB. The electrical interface
to the sensor could be [RS232](#glossary) or [RS485](#glossary). Internally the sensor will make an analogue
measurement but this is processed onboard the sensor so that an actual reading is presented to the user.

## Examples of digital sensors

* PTB330 pressure transmitter - RS232 interface with ASCII string of the format:

`P1  1007.14 ***.* * 1007.2 1007.1 1007.1 000E8`

This instrument normally has 3 pressure sensing elements so that a mean value can be provided in addition to
each individual pressure reading. Excessive
differences between the readings can be used to flag a suspect sensor. The unit can also be specified with a
built-in display screen as well as optional analogue and RS485 outputs.

<img alt="PTB330" src="PTB330.jpeg"/>

* Thies ultrasonic wind sensor - RS485 full duplex (4-wire) with ASCII string output of wind direction and
  speed.
  ![Thies ultrasonic](thies_ultrasonic.jpeg)
* Lufft SHM31 snow depth sensor - RS485 half duplex, snow depth readings are requested from the instrument
  using the [UMB](#glossary) binary or ASCII protocols. Additionally, many other parameters such as laser
  temperature, measurement distance etc. can be requested from the instrument.
  ![Lufft SHM31](lufft_shm31.jpeg)

## Analogue vs. Digital

All the sensors we've mentioned so far can be considered analogue as far as the measurement of a
meteorological parameter is concerned. This should not be surprising since we are usually measuring analogue
changes in the atmosphere. What we refer to as a digital sensor is merely an analogue sensor with extra
built-in electronics and processing to make the analogue measurement and transmit an actual reading. In fact,
digital sensors are more properly called 'instruments' since they consist of more than just an analogue
sensing element.

Such instruments are easier to connect to another digital device such as a PC since most computers don't have
the electrical interfaces required to accurately measure small voltages, current or resistance, but they do
normally need some configuration before use. Analogue sensors tend to be simpler and don't require
configuration and setup, however you need to connect them to a specialist device such as a datalogger that has
the electrical interfaces that can measure analogue inputs accurately and stably. The conversion to a usable,
digital value is then done by the dataloggers internal processing, usually under the control of a datalogger
program.

These days, many sensors can provide both digital and analogue outputs. The specifications page of the sensor manufacturers documentation will contain information regarding the outputs available from the sensor:

![Analogue and digital outputs](ana_and_dig_sensor.png "Analogue and digital output sensor example")

## Analogue Sensor interfacing

The analogue output (voltage, current or resistance) from an analogue sensor can be connected to a datalogger
with a built-in analogue to digital converter (ADC), modern dataloggers use a high resolution 24bit ADC. 
Under the control of the logger program the analogue output can be converted to a digital value representing 
the parameter we are trying to measure. You can read more about the process of analogue to digital 
conversion [here](https://www.electronics-tutorials.ws/combination/analogue-to-digital-converter.html).

In addition to the ADC, the datalogger usually has two types of terminal connection for analogue inputs: 
* **Single ended (SE)** - one wire of the sensor is connected to an SE input terminal and the other wire to an earth terminal. This way we measure our analogue signal with reference to earth. For higher signal output voltage levels e.g. 0-1 volts, this works fine but for lower output voltages e.g ( 10 millivolts) an incorrect reading could occur due to electrical noise on the inputs which could be attributed to the sensor itself.
* **Differential (H/L)** - For low output signals mentioned above it is better to use a differential input. This way we measure the voltage difference between two terminals, normally labelled high (H) and low (L). Now we are measuring the output voltage difference between the two terminals rather than taking a measurement referenced to ground, this method helps to negate any electrical noise on the inputs since such noise will be affecting both inputs simultaneously. The disadvantage of using differential inputs is that we require two input channels rather than the one used by a single ended input.

Here's an image showing the single ended and differential channels on a CR1000X datalogger. Note how the different channels are numbered and marked on the logger - we have 16 single ended and 8 differential inputs:

![CR1000X datalogger analogue inputs](cr1000x_analogue_inputs.png "CR1000X Analogue inputs")

## Digital sensor interfacing

There is nothing to measure from a digital sensor, the output will be binary data sent over a standard electrical interface such as RS232/RS485. This data has to be decoded into readable text which will contain the measured data from the sensor. A datalogger such as the CR1000X has a number of 'digital' input ports that can be configured for RS232 or RS485 connections. These types of sensors can also be connected to laptop/PC using a USB to RS232/485 converter, which is useful since the best way to set up these sensors (e.g. message output type, units, interval between data transmissions etc.) is using 'terminal' software or a manufacturers software application. This is also the easiest way to check that a digital sensor is working.
It is recommended to use a converter based on an "FTDI" chipset as these have been proven to be most reliable. An FTDI driver is available on the Met Office "Company Portal" to allow installation on Met Office laptops if required.

Digital input ports on dataloggers such as the CR1000X are normally labelled as "C" ports, there may also be a separate dedicated  input as shown below (marked RS232).

![CR1000X datalogger digital inputs](cr1000x_digital_inputs.png "CR1000X digital inputs")

## USB to RS232/485 converters

It is recommended to use a converter based on an "FTDI" chipset as these have been proven to be most reliable. An FTDI driver is available on the Met Office "Company Portal" to allow installation on Met Office laptops if required. An example of this type of converter is shown below. This one can be purchased from [here.](https://thepihut.com/products/ft232rnl-usb-to-rs232-485-422-ttl-interface-converter)

![RS232 / 485/ 422 USB converter](232_485_422_USB.png)

## Terminal software and serial settings

A terminal program can is used to receive and display the data from your USB/RS232/485 converter and setup the correct communications parameters. There are a number of free terminal programs available. My personal favourite is 'CoolTerm' which can be obtained from [here.](https://freeware.the-meiers.org/) This can be installed on a 'dirty' (non Met Office) laptop. 

<img alt="CoolTerm Application" src="coolterm.svg" title="CoolTerm Application" width="450" border-effect="line"/>

In the 'Company Portal' on a Met Office laptop there is a program called "PuTTy" that can be installed. This is pretty basic as far as serial connections are concerned, but it can do the job.

<img alt="Putty_settings" src="putty_settings.svg" width="450" border-effect="line"/>

<img alt="Putty data" src="putty_data.svg" width="450" border-effect="line"/>

When setting up a connection to a serial sensor you will have to select the correct communication parameters for the sensor you are connecting to. This usually means setting the **baud rate** and **parity** (if applicable). The baud rate is the number of bits per second that are used to transfer data over the serial connection. The parity is the method used to check the integrity of the data being transferred. There are two types of parity: **even** and **odd**. Even parity means that the number of 1s in the data stream must be even. Odd parity means that the number of 1s in the data stream must be odd. These parameters may often be written as e.g. **9600-8-N-1** which would signify 9600 bits per second, 8 data bits, no parity, 1 stop bit. Note these parameters are common between RS232/485/422, all of these employ serial communications the difference being the type of electrical interface used.

Whilst there are other parameters that can be set in these terminal applications you can usually leave them set at the default values. The sensor manufacturers documentation will tell you the default communications settings for the sensor you are using. The default settings can normally be changed by sending specific commands to the sensor from the terminal program. Note that most commands will require you to send a carriage return and line feed `<CR><LF>` or at least a `<CR>` to the terminal program to indicate that the command has been sent. You must of course select the correct serial port for the connection. On Windows this is normally `COM1` or `COM2` etc. On Mac OS X this is normally `/dev/tty.usbserial` and on Linux this is normally `/dev/ttyUSB0` etc.

<img alt="CoolTerm settings" src="coolterm_settings.svg" width="450" border-effect="line"/>

You can read more about serial communications [here.](https://en.wikipedia.org/wiki/Serial_communication)

## RS232 wiring

Simple RS232 wiring can be achieved using three wires: `RX` (receive), `TX` (transmit) and `GND` (ground). The `RX` and `TX` wires are used to transfer data from the sensor to the computer and vice versa. The `GND` wire is used to ground the sensor. The `RX` and `TX` wires from the sensor are normally connected "crossed over" to the `RX` and `TX` wires on the USB to RS232 converter. A 9 pin D-type connector was often used for serial connections and the RS232 specifications calls for the `RX` to be connected to pin 2, `TX` to be connected to pin 3 and `GND` to be connected to pin 5 in such a connector.

A simple 3 wire RS232 example is shown below (diagram also shows 9 pin D-type connector pin assignments):

![rs232_wiring.png](rs232_wiring.png)

Note thatRS232 should not be used for long cable runs due to noise degradation of the signal - less than 10 metres is normally fine especially at lower baud rates.

## RS485 / RS422 wiring

RS485 can be implemented using either two wires or four wires. The two wire implementation is the most common and is known as "half-duplex" whereas "four wires" provide "full duplex" communications whereby both the transmitter and receiver can send and receive data simultaneously over two pairs pair of transmit and receive wires. Most sensors use a two wire, semi-duplex implementation. RS422 is not very common these days, but this always uses four wires and is very similar to RS485 four wire.

The RS485 interface allows for either a single connection or a "bus" or "network" type wiring whereby multiple sensors can be connected to a single RS485 bus. In such a case each sensor is known as a "slave" and will have a unique address. The computer of logger controlling the bus is known as a "master" and with such an arrangement it is possible for a master to send and retrieve data to different slaves on the bus using the appropriate address. RS485 buses are not typically used for Met Office setups where each RS485 sensor has its own wiring to the datalogger, in this case every sensor can have the same address e.g. "0" since they are all effectively on a separate bus.

A table showing how to wire RS485 sensors is given below. There are a few different labelling conventions in use for RS485 with regards to how the receive and transmit wires are named, which can be confusing. The table tries to cover most of these conventions. Also remember that different protocols are often used over RS485 e.g. **ModBus** and **UMB**.

**RS485  4-wire:**

| Sensor end |    Processor end    |
|:----------:|:-------------------:|
|    Rx+     | TA / TxD (A)  / TD+ |
|    Rx-     | TB / TxD (B)  / TD- |
|    Tx+     | RA / RxD (+)  / RD+ |
|    Tx-     | RB / RxD (-)  / RD- |

**RS485  2-wire:**

| Sensor end | Processor end |
|:----------:|:-------------:|
|  Tx+ (A)   |  TxD+ / (A)   |
|  Tx- (B)   |  TxD- / (B)   |


RS485 is a good choice for long cable runs, its differential signalling means that it is not as susceptible to noise degradation as RS232.  **Termination resistors** are 120 Ohm resistors that are sometimes installed at either end of the RS485 bus. These resistors are used to prevent reflections occurring on the wires interfering with communications, however for short cable runs and lower baud rates, these are rarely necessary and not normally used in Met Office sensor wiring.

You can read more about RS485 [here.](https://en.wikipedia.org/wiki/RS-485)

## Quick Quiz

## Glossary

A glossary of various terms used on this webpage:

Sensor
: A sensor is a device that detects and responds to changes in physical conditions like heat, light, sound,
pressure, magnetism or motion and converts them into a measurable signal. Sensors measure physical quantities
and convert them into signals which can be read by observers or by instruments.

Interface
: An electrical interface is a shared boundary that allows the transfer of electrical signals between two
electrical devices or systems. It establishes the standards for how voltage levels, frequencies, and signal
durations are transmitted across the connection.

ASCII
: ASCII (American Standard Code for Information Interchange) is a character encoding standard that represents
English letters, digits, and other basic symbols through a binary code. It assigns a unique numeric value to
each character and symbol, allowing computers and other devices to communicate and process text data in a
standard format. ASCII is commonly used for text files and communication protocols.

RS232
: RS-232 (Recommended Standard 232) is a widely used communication standard for serial transmission of data
between devices (e.g. a digital sensor and computer). It defines the electrical and mechanical characteristics
of the interface, including signal levels, timing, and connector pin-outs.
Some key aspects of RS-232 include:
- Uses +/-12V voltage levels for logic 0 and 1 signals instead of TTL standard 0-5V.
- Asynchronous serial communication where data is transmitted one bit at a time over a single line.
- Common baud rates include 110, 300, 1200, 2400, 9600, 19200, 38400, 57600 and 115200 bits per second.

RS485
: RS-485 is a standard defining the electrical characteristics of drivers and receivers for use in serial
communications systems. It allows for multipoint connections and can communicate over long distances. RS-485
uses differential signaling to transmit data signals over a pair of wires. This gives it several advantages
over single-ended signaling schemes like RS-232, including better noise immunity and ability to interface
multiple devices using a bus topology. RS485 allows for half-duplex communication, where data can be
transmitted and received on the same pair of wires
- Common baud rates include 110, 300, 1200, 2400, 9600, 19200, 38400, 57600 and 115200 bits per second.

Full duplex, half duplex
: When using an RS485 electrical interface, full duplex mode allows simultaneous transmission and reception of
data, enabling bidirectional communication between devices (using 4 wires). In contrast, half duplex mode only
allows one-way communication at a time, with devices taking turns transmitting and receiving data (uses 2
wires).

ModBus
: Modbus is a communication protocol used in industrial automation to establish communication between
electronic devices. It enables the exchange of data between a master device (like a computer or controller)
and multiple slave devices (such as sensors, actuators, or other controllers) over serial lines or TCP/IP
networks. Modbus is widely adopted due to its simplicity, versatility, and interoperability across various
manufacturers' devices. Modbus defines a protocol data unit (PDU) that is independent of the lower layer
protocols in the protocol stack and allows for the mapping of the Modbus protocol on specific buses or
networks.

UMB
: The Lufft UMB (Universal Measurement Bus) protocol is a communication protocol used by Lufft environmental
sensors to transmit measurement data. It defines a standard format for sensors to send measurements and status
information in a binary or ASCII format. The UMB protocol uses a colon ':' as a block separator and addresses
each sensor with its unique UMB address. It allows for flexible connection of multiple sensors to a single
datalogger or converter unit.

Datalogger
: A data logger is an electronic device that records data over time from one or more external sources such as
sensors. Data loggers measure and record parameters such as temperature, humidity, voltage, pressure and more.
They are commonly used for monitoring environmental conditions, equipment performance and other
industrial/scientific applications. Data loggers are small, portable devices that store recorded data
internally on memory cards or remotely transfer the data to a computer or cloud for viewing and analysis.
