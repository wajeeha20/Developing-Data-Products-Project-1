# Developing Data Products Week 2 Assignment
Muhammad Hassaan Khan.  
July 6, 2020  



## Introduction

The goal of this assignment is to create a web page using R Markdown that features a map created with Leaflet. The webpage should be hosted on either Github Pages, RPubs, or NeoCities. The webpage must also contain the date when the document was created.

## Top 10 Most Populous Cities in the Philippines

The map shows the 10 most populous cities in the Philippines. Hover on each location to see how large is the population of the city. The data was taken from http://www.worldatlas.com/webimage/countrys/asia/philippines/phlatlog.htm.


```r
library(leaflet)
df <- read.csv("locations.csv")
df %>% leaflet() %>%
  addTiles() %>%
  addMarkers(
    lat = df$lat, 
    lng = df$long, 
    popup = paste(df$popup, "<br>", "Population:", df$population),
    clusterOptions = markerClusterOptions()) %>%
  addCircleMarkers(radius = sqrt(df$population/10e3))
```

```
#/> Assuming 'long' and 'lat' are longitude and latitude, respectively
```

<!--html_preserve--><div id="htmlwidget-3bfd1ac4869f0cb6542f" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-3bfd1ac4869f0cb6542f">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"maxNativeZoom":null,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"continuousWorld":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":null,"unloadInvisibleTiles":null,"updateWhenIdle":null,"detectRetina":false,"reuseTiles":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addMarkers","args":[[14.6042,14.6488,7.20417,7.07306,7.16083,10.31672,6.11278,14.5243,14.58691,14.62578],[120.9822,121.0509,124.43972,125.61278,124.475,123.89071,125.17167,121.0792,121.0614,121.12251],null,null,null,{"clickable":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["Manila <br> Population: 10444527","Quezon City <br> Population: 2761720","Budta <br> Population: 1273715","City <br> Population: 1212504","Malingao <br> Population: 1121974","Cebu City <br> Population: 798634","General Santos City <br> Population: 679588","Taguig <br> Population: 644473","Pasig City <br> Population: 617301","Antipolo <br> Population: 549543"],null,{"showCoverageOnHover":true,"zoomToBoundsOnClick":true,"spiderfyOnMaxZoom":true,"removeOutsideVisibleBounds":true,"spiderLegPolylineOptions":{"weight":1.5,"color":"#222","opacity":0.5},"freezeAtZoom":false},null,null,null,null]},{"method":"addCircleMarkers","args":[[14.6042,14.6488,7.20417,7.07306,7.16083,10.31672,6.11278,14.5243,14.58691,14.62578],[120.9822,121.0509,124.43972,125.61278,124.475,123.89071,125.17167,121.0792,121.0614,121.12251],[32.3179934401875,16.6184235112721,11.2858982805978,11.011375935822,10.5923274118581,8.93663247537908,8.24371275579153,8.02790757296071,7.85685051404187,7.41311675343104],null,null,{"lineCap":null,"lineJoin":null,"clickable":true,"pointerEvents":null,"className":"","stroke":true,"color":"#03F","weight":5,"opacity":0.5,"fill":true,"fillColor":"#03F","fillOpacity":0.2,"dashArray":null},null,null,null,null,null,null,null]}],"limits":{"lat":[6.11278,14.6488],"lng":[120.9822,125.61278]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->
