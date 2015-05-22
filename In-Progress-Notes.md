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

---

Search and Replace location => point
Ctrl-H

changed
  //setup map and add layers
to data from
37.760693, -122.418475
zoom 15


change
 //let Socrata do the sorting:
  https://data.cityofnewyork.us/NYC-BigApps/NYPD-Motor-Vehicle-Collisions/h9gi-nx95
  var sodaUrl = "http://data.cityofnewyork.us/resource/h9gi-nx95.json?$where=date%3E%272014-09-01%27%20AND%20zip_code=%2711201%27%20AND%20date%20IS%20NOT%20NULL&$order=date%20ASC";


The well first well formed URL that I've got going changed date to opened and is 
https://data.sfgov.org/resource/gntf-qmc7.json?$select=point,closed,opened,status,case_id,address&$where=opened%3E%272014-09-01%27%20AND%20opened%20IS%20NOT%20NULL&$order=opened%20ASC

Shit-   I want to give up.   I know that I made progress, but I don't have a demonstrateable MVP.

so when I look at this again, describe where I am stuck.

I think that I'm stuck because the SF311 data presents the location as a single column variable with the name "point"
while I changed name from location to point, I don't think it corrects for the two column vs 1 column.

Gonna push all to github, and get lunch



