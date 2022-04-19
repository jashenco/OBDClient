# OBDClient

This repo is a OBD Client. OBD is used to collect data from your car and read erros.

To run this script, you'll need a Raspberry Pi and an OBD-II Cable. Connect the OBD-II cable from the USB port on the Raspberry Pi to the OBD port of the car.

The script connects to the car using the obd-python library. 

As a simple example, we take the cars speed in kph. 
We tranform the data to the JSON format and add the speed (value) and add the corresponding unit: "kph" (key). We also add a timestamp.

After this, we send the data via HTTP (TCP) to a webserver. We'll call the webserver the OBD Server from now on.
Link to OBD Server Github: https://github.com/jashenco/OBDServer.
For the sake of this project, I've ran the webserver on a Ubuntu Server which can by found following this URL: http://89.99.4.132:8080/.
The OBD CLient POSTs data to the OBD Server on the following URL: http://89.99.4.132:8080/stats (So with 'stats' added).
The same URL also accepts a GET command to display the data in a JSON format. From here, the data can be used for further use. In this case, I haven't implemented a front-end yet.

# To-Dos for in the future

- Collect more of available data using OBD-Python library (information about steeringwheel position, pedal positions, etc.).
- Add GPS for location of the car when collecting data.
- Store data in seperate JSON file on Raspberry Pi and send data per (e.g.) 15 minutes to make it better to handle for the OBD server.
- Implement front-end with a map that displays information about last trips (e.g. fuel consumption, calculated emissions).
- Implement some kind of recommendation system with tips for drivers.
