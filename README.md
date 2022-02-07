# Mapping Earthquakes

## Overview
In this analysis, an earthquake map with two different maps and the earthquake overlay was created using VS Code, JavaScript, HTML, and CSS. The creation of more maps will show the earthquake data in relation to the tectonic plates’ location on the earth, and they would like to see all the earthquakes with a magnitude greater than 4.5 on the map, and they would like to see the data on a third map. The steps to complete this are:

- Add Tectonic Plate Data
- Add Major Earthquake Data
- Add an Additional Map

## Results

Add Tectonic Plate Data
- Add a second layer group variable for the tectonic plate data
- Add a reference to the tectonic plate data to the overlay object
- Using d3.json() callback method, make a call to the tectonic plate data
```
d3.json(tpBoundariesURL).then(function(data) {
    console.log(data);
    L.geoJSON(data).addTo(tectonicPlates);
});
```
- Start the Python server and launch the index.html file
 
![image](https://user-images.githubusercontent.com/67409852/146695296-11a77209-d79b-4f1f-a242-3af0b1c73837.png)

Add Major Earthquake Data
- Add a third layer group variable for the major earthquake data
- Add a reference to the major earthquake data to the overlay object
- Use the d3.json() callback method to make a call to the major earthquake data from the GeoJSON Summary Feed for M4.5+ Earthquakes for the past 7 days
```
d3.json(majorEarthquakesURL).then(function(data) {
    function styleInfo(feature) {
        function getRadius(magnitude) {
            if (magnitude === 0) {
                return 1;
            }
            return magnitude * 4;
        }
```
- Use the same parameters in the styleInfo() function that will make a call to the getColor() and getRadius() functions
- Change the getColor() function to use only three colors for the following magnitudes; magnitude less than 5, a magnitude greater than 5, and a magnitude greater than 6
```
function getColor(magnitude) {
            if (magnitude > 5) {
                return "#ea2c2c";
              }
              if (magnitude > 4) {
                return "#ea822c";
              }
              if (magnitude > 3) {
                return "#ee9c00";
              }
              if (magnitude > 2) {
                return "#eecc00";
              }
              if (magnitude > 1) {
                return "#d4ee00";
              }
              return "#98ee00";
        }
```
- Use the same parameters from the preceding step in the getRadius() function
- Then, pass the major earthquake data into the GeoJSON layer and do the following with the geoJSON()
- Add the major earthquake layer group variable to the map, i.e, majorEQ.addTo(map), and then close the d3.json() callback
- Start Python server

## Summary

![image](https://user-images.githubusercontent.com/67409852/146695276-277fa2e9-ac54-4531-b56b-aac8453f5541.png)

![image](https://user-images.githubusercontent.com/67409852/146695321-2466b66d-115a-42ea-bd79-f2fbb817cab8.png)

![image](https://user-images.githubusercontent.com/67409852/146695348-ad137d4f-1b5f-4494-a278-f7e35ba371a4.png)

![image](https://user-images.githubusercontent.com/67409852/146695372-dd0232c2-a5ce-423f-a808-d411af042bc2.png)
