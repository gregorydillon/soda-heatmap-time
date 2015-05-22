Perhaps strangely, the working payload code is near the end of the HTML page, 
rather than in a javascript file.

It pulls data from this socrata endpoint
http://data.cityofnewyork.us/resource/h9gi-nx95.json?$where=date%3E%272014-09-01%27%20AND%20zip_code=%2711201%27%20AND%20date%20IS%20NOT%20NULL&$order=date%20ASC

That endpoint reveals a very typical json object.   I think, good, I can work with that.
Here is the first object

    {
  "number_of_persons_killed" : "0",
  "vehicle_type_code1" : "PASSENGER VEHICLE",
  "zip_code" : "11201",
  "vehicle_type_code2" : "PASSENGER VEHICLE",
  "location" : {
    "needs_recoding" : false,
    "longitude" : "-73.983213",
    "latitude" : "40.6959932"
  },
  "number_of_motorist_injured" : "0",
  "date" : "2014-09-01T00:00:00",
  "off_street_name" : "TILLARY STREET",
  "time" : "6:45",
  "on_street_name" : "GOLD STREET",
  "number_of_pedestrians_injured" : "0",
  "number_of_cyclist_killed" : "0",
  "longitude" : "-73.9832130",
  "number_of_cyclist_injured" : "0",
  "unique_key" : "1017506",
  "borough" : "BROOKLYN",
  "number_of_pedestrians_killed" : "0",
  "contributing_factor_vehicle_1" : "Driver Inattention/Distraction",
  "number_of_motorist_killed" : "0",
  "number_of_persons_injured" : "0",
  "contributing_factor_vehicle_2" : "Unspecified",
  "latitude" : "40.6959932"
}

<!---->
Notice in the js code, that the original splits location variable into latitude and longitude
I believe in San Francisco, that variable is called point

 var goodData = [];
    for(var i=0;i<rawData.length;i++){
      rawData[i].value = 0;
      rawData[i].fresh=true;
      if(rawData[i].location) {
        rawData[i].lat = parseFloat(rawData[i].location.latitude);
        rawData[i].lng = parseFloat(rawData[i].location.longitude); 
      }
<!---->
      
//
Notice that Chris W Hong, give credit to Chris Metcalf.
Want to go through his github too.



