
# Intro to Web Maps using Leaflet


<p align="left">
  <a href="#digital-map--web-map">Digital Map ≠ Web Map</a>&nbsp;|
  <a href="#what-in-leaflet">What is Leaflet?</a>&nbsp;|
  <a href="#qgis">Make Your Own Web Map</a>&nbsp;|
  <a href="#hands-on">What's Next?</a>&nbsp;
</p>

# Introduction

This workshop is intended for anyone interested in getting started with creating web maps, aimed at a beginner-level, and meant to be given in a lab setting. We will use [Leaflet](https://leafletjs.com/) as a base for understanding how web maps work. There are two main sections: an intro to web maps, and a hands-on where code is copy/pasted to make interactive maps. The goal is to develop essential skills and knowledge to get started, and provide an opportunity to ask questions (in person). As a bonus, students will create and have boilerplate code to be built upon and tinkered with at a later time.    
#### Software used     
- **Internet browser (and an internet connection)**. The most recent versions of [Mozilla Firefox](https://www.mozilla.org) and [Google Chrome](https://www.google.com/chrome/) are the recommended browsers.
- **Source code editor**. To make your life easier while viewing or editing code, it's good to use a [source code editor](https://en.wikipedia.org/wiki/Source_code_editor). This workshop uses [Atom](https://atom.io/) for screenshots, but other editors like [Notepad++](https://notepad-plus-plus.org/) and [Sublime Text](https://www.sublimetext.com/3) will work similarly.

<!--
#### GIS Resources at UBC:
- General Informational website for all things UBC GIS: [gis.ubc.ca](http://gis.ubc.ca/)    
- UBC Library's guide for finding and working with GIS resources: [guides.library.ubc.ca/gis](http://guides.library.ubc.ca/gis)
- UBC's GIS email list (participate or lurk!): [UBC GIS ListServ](https://lists.ubc.ca/scripts/wa.exe?SUBED1=GIS-LIST&A=1)  
- UBC's GIS Slack (create your own channel or lurk!): [ubcgis.slack.com](https://ubcgis.slack.com/)
- Evan Thornberry, GIS Librarian @ UBC Library: evan.thornberry AT ubc.ca
-->

#### Prerequisites
Making maps is hard. And without practice, working in the web is hard too. While there are no actual prerequisites for the in person workshop, these things would be good to know before jumping right in, or to refer to later:

- **Intro level knowledge of computer programming**. [Matt Adesanya's *A Gentler Introduction to Programming*](https://www.freecodecamp.org/news/a-gentler-introduction-to-programming-1f57383a1b2c/) is a great starting point, and will be more than you need for this workshop.
- **Intro level knowledge of HTML, CSS and JavaScript**. [Sololearn.com offers several courses on these topics and more](https://www.sololearn.com/Courses/), but there are several other educational resources to choose from on the web if you prefer something different. You'er not expected to be a pro for this workshop, but understanding these concepts will provide some very useful perspective.
- **Understanding of basic cartographic design concepts**. What is map making without a consideration of cartography? Axis Maps has written a phenomenal [short guide to cartography](https://www.axismaps.com/guide/), and [the web map module](https://www.axismaps.com/guide/web/should-a-map-be-interactive/) is especially relevant.

### Workshop Data
All of the data you'll need for this workshop is included in this repository. You can simply copy/paste the text from here to your local computer without downloading. However, if you'd like to download the whole package to repurpose, click on the green download link, then download the ZIP:

![Download](/img/download.png "Download")

## What is Leaflet?
Let's get started!

So, what exactly is Leaflet? Leaflet is a set of instructions that your web browser or mobile device uses to display maps and let you interact with them. So like when you double click a mouse on a map, leaflet tells your browser to zoom in. Leaflet defines the style of your map - and includes things like zoom controls, attribution links, colors for markers on top of the map, etc. It is made up of only 38kb of Javascript, so it is really fast and lightweight - meaning browsers don’t have to work very hard to load it. It is open source, free, and hugely customizable. And because of all of that it is really widely used. There are lots of alternative to Leaflet, but I think the one that is most widely used is Google Maps, which you need an API key to use.
### As Code
Technically speaking, Leaflet consists of JavaScript and CSS code libraries which power the ways your web browser interprets and interacts with geospatial data, displays colors and style. For instance, when you double click a map to zoom in, Leaflet is at work. When you add data to your map, Leaflet assigns it a default color. And because Leaflet is open-source, the code is hugely customizable and extensible. [Here are some examples](https://leafletjs.com/plugins.html) of Leaflet-based plugins to give you some idea of the variety of added functionality that comes from the community of developers.

### In a Browser
Take a look at this basic [Leaflet map example](https://ect123.s3.amazonaws.com/map01.html). You can zoom in, pan around, etc. It's meant to be displayed in your internet browser or a mobile application, so it loads and responds to you quickly.  

## Web Map ≠ Digital Map
While we're talking about maps loading and working in the web, let's also talk the difference between a **web map** and a **digital map**. The term digital map is used quite often. As a benchmark, Wikipedia's entry for "Digital Mapping" is:


and it may not refer to anything specific. Rather it's more a catch-all term that refers


### Digital Maps
A digital map is a map that was somehow derived from a computer. Sometimes we use this term to refer to scanned paper maps since they've been digitally reformatted like this old map of Vancouver:

![Digital surrogate of a historical map of Vancouver](/img/commonwealth_4m90fg11z_access800.jpg "Map reproduction courtesy of the Norman B. Leventhal Map & Education Center at the Boston Public Library")    
<sub><sup>[Map reproduction courtesy of the Norman B. Leventhal Map & Education Center at the Boston Public Library](https://collections.leventhalmap.org/search/commonwealth:4m90fg11z)</sup></sub>     

More commonly, we use this term for "born digital" maps like this cycling map from the City of Vancouver. This map was likely constructed with geospatial data and a Geographic Information System (GIS), and published at a static scale and dimension.

![Front of City of Vancouver Cycling Map 2019](/img/vancycle.jpg "Front of City of Vancouver Cycling Map 2019")     

<sub><sup>[Front of City of Vancouver Cycling 2019 Map](https://vancouver.ca/streets-transportation/cycling-routes-maps-and-trip-planner.aspx)</sup></sub>

### Web Maps
Using the definition above, a web map is a type of digital map since it is derived from a computer. However there are some important differences:
- **Web may have dynamic scales and content**. For instance when you zoom in, more information may appear that wasn't apparent before. For this reason, web maps are not designed for print.
- **Interactive**. This has been stated already, but web maps are built to be interacted with - usually by an end user.
- **Often relies on web and mobile technology**.    
We see web maps all the time in the web, and usually we think of [Google Maps](https://www.google.com/maps/embed?pb=!1m14!1m12!1m3!1d10414.983406806172!2d-123.24297379757083!3d49.26226286690077!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!5e0!3m2!1sen!2sca!4v1542068116121) as a familiar example. For small businesses, web maps are helpful for [finding directions](https://luppolobrewing.ca/contact/). For app builders, web maps might provide a [method for routing to locations](https://www.pogomap.info/) using a mobile device's geolocation features. For researchers, they may help [communicate important information](https://www.uvic.ca/research/centres/cisur/projects/map/index.php) in an area of study. For journalists, they may help [provide perspective on a story in the news](https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html#4.04/39.97/-84.35).

In any case, web maps are a canvas for visualizing and interacting with geographic data.

## Basic Structure
Let's talk a little bit about what makes this map work. To do that, we'll dissect the main moving parts of a basic web map. These parts work in concert to make a functioning web map.
### Map Tiles
Map tiles are squares of geographic data that are loaded to your frame of view whenever you zoom or pan your map. You've probably noticed them if you've had choppy internet connection and had to wait for data to load:    

![tiles](/img/tiles.gif)   
### Zoom Levels
Because web maps refresh content as you zoom in, they don't have a traditional map scale. Instead, there are different levels associated with the amount of detail shown on the map.
### Tile Servers
### Raster and Vector Tiles
### Data (.shp ⇢ .geojson)
If you've ever tried to share a Shapefile in the web, you've encountered some problems or the need to transform your file into something else. Shapefiles are meant for GIS and other software to consume. They weren't designed to be displayed in the web. [GeoJSON](https://geojson.org/) on the other hand, are meant for the web. They're "easy for humans to read, and easy for machines to read", meaning that they're a lightweight, simplified and format so your average web browser can use them, and they're also pretty easy to understand if you want to view and edit them in a code editor. Here's a GeoJSON point over UBC:

```json
    {
      "type": "Feature",
      "properties": {
        "name": "The University of British Columbia"
      },
      "geometry": {
        "type": "Point",
        "coordinates": [
          -123.25012207031249,
          49.26186749272789
        ]
      }
    }
```
In contrast, a Shapefile is a binary (not text) format, so you wouldn't be able to read the file with human eyes.
### Style
### Interaction

# Workshop
## Getting Started
### Software Used
We will be using two pieces of software - a web browser, which will render/display your map. We’re using I think Firefox. And a source code editor to edit the html file that contains the map. We are going to use Dreamweaver, which is our only option here. Dreamweaver isn’t my first choice, but it is all we have. I recommend using Atom if anyone is interested in doing this at home. Atom is free and open source, and full of bells and whistles. Anyone here familiar with using a source code editor for web technologies?
### Putting it into Perspective
### Development Environment
First things first, let's set up your development environment. This is a fancy way of saying make the tools you are using accessible on your computer screen display. In our case, we’re just using a web browser and source code editor, so we’ll split our screen in half - web browser on one side and the code editor on another. Let’s take a second to do this. This is really entirely up to your personal preferences.
## Create and Open Your Map Boilerplate
Below is a bunch of code - this is our map boilerplate. We need to cut this and paste this to a new file into your source code editor. It’s important that you don’t lose any of this text, and that it remains in its original structure and arrangement.

```HTML
<html>
  <head>

    <title>Leaflet</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- Source for your Leaflet JavaScript and CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.2.0/dist/leaflet.css" integrity="sha512-M2wvCLH6DSRazYeZRIm1JnYyh22purTM+FDB5CsyxtQJYeKq83arPe5wgbNmcFXGqiSH2XR8dT/fJISVA1r/zQ==" crossorigin=""/>
    <script src="https://unpkg.com/leaflet@1.2.0/dist/leaflet.js" integrity="sha512-lInM/apFSqyy1o6s89K4iQUKg6ppXEgsVxT35HbzUupEVRh2Eu9Wdl4tHj7dZO0s1uvplcYGmt3498TtHq+log==" crossorigin=""></script>

  </head>

  <body>
    <!-- Your map's HTML container -->
    <div id="mapid" style="height: 100%;"></div>

    <!-- Script for your map between <script> and </script> -->
    <script>

      // Initialize your map, sets the initial view location and zoom level
      var mymap = L.map('mapid').setView([49.2827, -123.1207], 11);

      //Load the tile layer, paste in new tile layer of choice.
      var Stamen_Terrain = L.tileLayer('https://stamen-tiles-{s}.a.ssl.fastly.net/terrain/{z}/{x}/{y}.{ext}', {
      attribution: 'Map tiles by <a href="http://stamen.com">Stamen Design</a>, <a href="http://creativecommons.org/licenses/by/3.0">CC BY 3.0</a> — Map data © <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
      subdomains: 'abcd',
      minZoom: 0,
      maxZoom: 18,
      ext: 'png'
        }).addTo(mymap);

      //Paste your marker here

      //Paste UBC's buildings layer here

      //Paste popup function here

    </script>
  </body>
</html>

```

### In a Browser
Once you have pasted the text, save the file to your desktop. Save it as ubc-buildings.html. When it is, in your browser, open a new tab open the file. Now you’ll have two tabs open in your browser, so I hope this isn’t too tricky. In your browser, you should see a map that looks something like this:

![Map loads over the center of Vancouver](/img/map01.png "Your first map loads over Vancouver")


### In a Source Code Editor
in Atom, let's look at what is making this file work. The html document is split into two sections - a head which is between lines 2-13, and a body between lines 15-39. Are you all seeing the lines? Each of these sections are contained in opening and closing tags. Inside the head is the metadata that your browser is given about the document. And the body is the container for the document.
#### Head
inside the head are things like on line 4, the metadata field for the document’s title. Your title is displayed in your browser tab. Lines 8-9 are links to the source for leaflet - including the js library as well as the style sheet (the .css) that defines how elements of this map will look. And on line 11 is the same link to jQuery. If you copy the link to the leaflet js and paste it in a new tab in your browser, you’ll see the raw javascript code. If you wanted to, you could just add that to this page, but we don’t need to.
#### Body
In the body, you have on line 17, the container for your map (contained in a div tag), including a name/id for the container, as well as a style attribute telling your browser to make this container as high as the page allows. Line 19-37 is the script for your map. This is what we’ll be editing today.
#### Script
in the script, on line 22 we have our map variable containing the initial starting point and zoom level. When someone opens this page, or refreshed their browser, this is what the map will show. Zoom levels are a digital map’s way of dealing with scale. In the paper world we have maps that are printed at different scales which show differing levels of detail. A paper map with a small scale has little detail, a map at a large scale has lots of detail. But with digital maps, we can just double-click our mouse to load more detail. There are up to 22 standard zoom levels, with zoom level 22 being the most detailed, and zoom level 0 being all the way zoomed out to see the entire world. We also have in lines 24-31 a tile layer variable. Your tile layer in this case is the basemap that we see when we are zooming and panning. What that is is a streaming set of georeferenced tiles that we are pulling in from some remote server. And we are defining that in these lines. There’s some other info in here too like attribution and a max min zoom level - this particular layer will only zoom into layer 18. And then it stops.
## Configure the Starting View
Ok so we have our map boilerplate, and its a good starting point for making a map of ubc. One thing that we’ll notice is that when the map loads, it’s just starting over vancouver, and not UBC. So, let’s change that.
On line :exclamation: you should see this text:
```javascript
var mymap = L.map('mapid').setView([49.2827, -123.1207], 11);
```
You can see that there are a couple of recognizable elements here - most noticeably the latitude and longitude coordinate pair (49.2827, -123.1207). That location is the geographic center point for the city of Vancouver. When your browser loads the map, it starts with that point in the center of your screen.

Say we want to load the map over UBC, which is about 5 km to the west. We'd need to change that coordinate pair to be the center point of UBC. There are several ways to find this, but an easy one is to use [latlong.net](https://www.latlong.net/). Type in UBC in latlong.net, and you return a coordinate pair of 49.260605 and -123.245995.

**:heavy_check_mark: Replace the coordinate pair on line :exclamation: so your map loads over UBC.**

Save your .html file, and reload your browser. If everything went as planned, you should see this:


![Map loads over the center of UBC](/img/map02.png "Your second map loads over UBC")

If you don't see a map like the one above, undo your edit in your source code editor (**ctl + z**), and save (**ctl + s**) when it's working again. At that point try again making sure your code syntax is exactly as shown:

```javascript
var mymap = L.map('mapid').setView([49.260605, -123.245995], 11);
```

### Zoom Levels
Your map currently loads at a zoom level which requires a user to zoom in immediately toward UBC. Ideally, if this map is meant to show information for UBC's campus, it would load as close to campus as possible, without different screen dimensions cutting off parts of the campus area. So we'll need to change the loading zoom level.

Looking again at our <code>mymap</code> variable, the loading view is set at the coordinate pair over UBC, and at a zoom level of 11. In our case, the map best loads at zoom level 14.


![Map loads over the center of UBC!](/img/map03.png "Map loads over the center of UBC!")

## Adding Data




### Markers
![Map loads over the center of UBC with a marker!](/img/map04.png "Map loads over the center of UBC with a marker!")


### GeoJSON

![Map loads over the center of UBC with a marker, and a data layer!](/img/map05.png "Map loads over the center of UBC with a marker, and a data layer!")

## Change the Base Map/Layer Style

![Map loads over the center of UBC with a marker, a data layer, and a custom base map!](/img/map06.png "Map loads over the center of UBC with a marker, a data layer, and a custom base map!")

## Interaction

### Hover Effects
### Popups
If you want to change the popup text, feel free, or delete it all together.

![Map loads over the center of UBC with a marker, a data layer, a custom base map, and popup for the data layer!](/img/map07.png "Map loads over the center of UBC with a marker, a data layer, a custom base map, and popup for the data layer!")


## What's Next?    
You are not required to think about web maps ever again, but if this workshop has inspired you to expand your skills, try making another map on your own using data for a different location on your own. This will give you some clarity around where you might have some gaps in understanding. There are some additional clean .geojsons included here to practice.

***Keep in mind that not all data will be nicely packaged and cleaned. In fact, it never is. If you proceed to use data that you've found on the web, be prepared to spend time preparing your data to be usable with Leaflet and the web.***

### More Resources for Web Mapping
This workshop builds from several other resources for web mapping. Here are some great places to start extending your knowledge:

Web map basics: [Anatomy of a Web Map - Alan McConchie and Beth Schechter](http://maptime.io/anatomy-of-a-web-map/)    
Leaflet basics: [Leaflet Quick Start Guide](https://leafletjs.com/examples/quick-start/)   
Web map functionality examples: [Mapbox.js Examples](https://docs.mapbox.com/mapbox.js/example/v1.0.0/)    
GeoJSON: [More than you ever wanted to know about GeoJSON - Tom MacWright](https://macwright.org/2015/03/23/geojson-second-bite.html)    

### License
CC 0.0 Public Domain
