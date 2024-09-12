# Datalogger support applications

Campbell Scientific (CSL) produce a number of Windows software applications to support the configuration, programming
and management of their dataloggers. Some of these programs have overlapping functionality, most are free to download
but some require a license. When starting out it can be difficult to know what application to use, so I hope the
following will help. Some tasks can be equally well carried out by different applications, so just use the one you feel
most comfortable with or have access to.

## Getting help

CSL provide excellent online documentation and manuals for these applications, but perhaps the best resource is their
large collection of instructional videos available on the CSL website
and [YouTube.](https://www.youtube.com/@CampbellScientific)

These videos are also available on the CSL product pages for each application. They cover basic and more advanced
datalogger operations. Don't forget that there are many Engineers with the Met Office (Observations R&D and Field
Services in particular) that are very familiar with working with dataloggers so please ask if you're not sure of
something - you should at least get pointed in the right direction.

## Device configuration utility (DevConfig)

Configuration of Campbell Scientific data loggers and sensors, sending new operating systems, editing settings, sending
new programs. Can monitor live data collection. Note that the easiest way to connect to a logger is via the USB port.
This application is mostly used (as its name suggests) to initially configure make changes to the configuration of a
datalogger.

This application can also be used to configure many of CSL's sensors and datalogger add-on modules. This is probably the
most common/popular tool used by Engineers. You can load programs and update the operating system of the logger and
check its running state.
Read more about it [here.](https://www.campbellsci.com/devconfig) This software is free to use.

<img alt="Device configuration utility" src="devconfig.svg" width="700"/>

## Loggernet

CSL's premium software application (requires a license, Met Office does have a large number of licensed copies
installed). The only application here that allows for scheduled data collection. Can also perform data logger file
control, configuring a network of loggers, data retrieval and monitoring. Loggernet is a bit different in that it has
most of the other applications here ‘built-in’ (DevConfig, ShortCut, CRBasic editor). This makes it very useful but
these applications are also now available to download for free as standalone applications. Read
more about it [here.](https://www.campbellsci.com/loggernet) This software requires a license to use.

<img alt="Loggernet" src="loggernet.svg" width="700"/>

## PC400

Can do most of what Loggernet can do, very similar but cannot do scheduled data collection. Read more about
it [here.](https://www.campbellsci.com/pc400) This software is free to use.

<img alt="PC400" src="PC400.svg" width="700"/>

## ShortCut

Provides a step-by-step ‘wizard’ that can write a basic data logger program for you provided the sensors you’re using
are in the applications sensor list. The end program can be edited later in CRBasic. Handy for creating a program
starting point and a good way to start understanding how a CRBasic logger program is written and structured. Read
more about it [here.](https://www.campbellsci.com/shortcut) This software is free to use.

<img alt="ShortCut" src="shortcut.svg" width="700"/>

## CRBasic editor

A full-featured data logger program editor that can compile and send your program to a connected logger. The program
also checks for coding errors before the compilation stage. Read more about
it [here.](https://www.campbellsci.com/pc400) This software is free to use.

<img alt="CR Basic" src="CRbasic.svg" width="700"/>