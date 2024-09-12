# SurfaceNet

<img src="SurfaceNet Overview.png" alt="Graphical Overview of the SurfaceNet System" />

The SurfaceNet Project replaced the existing ground based met monitoring system at the 300 plus land sites around the UK and beyond; as well as 70 plus marine sites including ships and moored buoys.
The CR1000X dataloggers are commercially available, internet enabled and able to handle two way communication so they can not only upload weather data but can also be updated remotely in the future. The captured met data will be communicated to a cloud-based system where it can be transformed/refined and delivered for operational use to the Met Office. There is robust controls over the quality of the data built into the cloud system’s architecture, ensuring accurate and trusted data gets to those who need it. 

## SurfaceNet High Level process

<img src="SurfaceNet High Level process.png"  />

Data loggers are at site locations (Yellow box). The Monitoring, shaded pink, is the cloud technology processing part of SurfaceNet (which we refer to as ‘SurfaceNet’, as opposed to the applications or other systems which are fed by it). APIs are streams of data which enable users to access data. All lead to the visualisation or products of data shaded in blue.

## Associated Tools
There is a suite of tools used to interact and manage with the SurfaceNet system.

These Systems are:
## ServiceNow ^1^
All site locations are located in ServiceNow – **the source of truth!** This includes *location details, such as latitude and longitude, station height, type of station and site GUID (a unique site identifier)*

Asset information such as loggers and sensors, complete with calibration details and activity history. If the configuration in ServiceNow is not correct, e.g. a sensor is not attached to a site logger, then the data will not be captured in SurfaceNet.

ServiceNow pushes this information to OSMM, where it is stored and used by SurfaceNet. If ServiceNow has an outage then SurfaceNet continues to operate as all required metadata is held in OSMM. 

A training guide for the Field Service Module for ServiceNow can be found here [Field Service Module](https://metoffice.sharepoint.com/:p:/r/sites/MetOfficeServiceNowExt/_layouts/15/Doc.aspx?sourcedoc=%7BB180756D-7FDD-4D7D-B0DA-901AEDC218FF%7D&file=06_Met%20Office_FT%20Slides_Field%20Service%20Management.pptx&action=edit&mobileredirect=true)

## Observation Station Metadata Manager (OSMM)

<img src="OSMM.png" />

ServiceNow feeds OSMM with location and asset metadata. That metadata is added to in OSMM with QC rules and additional information such as site IDs, comms polling frequency and types of coded messages. OSMM holds just enough information to enable SurfaceNet to process required information and to know what coded messages to create. It does not hold historic metadata, that is still held by the MIDAS database

## Network Manager

<img src="Netwok Manager.PNG" />

Network Manager is the tool to interact with the dataloggers at site. Largely for engineers, but not exclusively. All loggers are stored on this application and actions such as downloading new software, rebooting and interrogating loggers for sensor information.

## Grafana/Storm

