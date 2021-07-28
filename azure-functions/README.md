# Azure Function Examples

These Azure Functions are to be used as examples to process ingested data as well as twin updates. It assumes you already setup your Azure Digital Twin instance with ingress and/or egress steps completed.

#### Learn more

- [How to ingest iot hub data](https://docs.microsoft.com/en-us/azure/digital-twins/how-to-ingest-iot-hub-data?tabs=portal)
- [How to manage endpoints and routes](https://docs.microsoft.com/en-us/azure/digital-twins/how-to-manage-routes?tabs=portal%2Cportal2%2Cportal3)

## Incoming Messages

This function is used to process data as it is ingested into Event Hub and then sets the property values of the device twins in Azure Digital Twins. In this instance, the messages come from devices in IoT Hub that are used to track temperature and humidity values.

1. Each message contains humidity and temperature data. Temperature arrives in Celsius format, and needs to be converted into Fahrenheit.
2. Humidity and temperature need to be rounded up.
3. Devices are a 1-1 match to a room, we need to update the temperature and humidity properties for the associated room.

## Twin Updates

The outcome of this function is to get the average floor temperature and humidity values based on the rooms on that floor.
 
1. Get the incoming relationship of the room. This will get the floor twin ID.
2. Get a list of all the rooms on the floor and get the humidity and temperature properties for each.
3. Calculate the average temperature and humidity across all the rooms.
4. Update the temperature and humidity properties on the floor.

## Publishing an Azure Function

See [Connect an end-to-end solution](https://docs.microsoft.com/azure/digital-twins/tutorial-end-to-end#set-up-the-sample-function-app) in the Azure Digital Twins documentation for more information about publishing an Azure function to work with Azure Digital Twins.