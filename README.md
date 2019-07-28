
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
Map tiles are squares of geographic data that are loaded to your frame of view whenever you zoom or pan your map. Each tile is a 256px x 256px (traditionally a .png image at roughly 20-40kb each), making them quick to load over an internet connection. These tiles provide a geographic reference for other data layers that might be added later (we'll get to that in a minute). You've probably noticed them if you've had choppy internet connection and had to wait for data to load:    

![tiles](/img/tiles.gif)    

Every time you pan your map, new tiles are loaded to fill that frame of view. The tiles outside of that view are not loaded because loading the entire world's tiles would be time consuming, especially if you were just focused on a small area. When you zoom in or out, new tiles are loaded to correspond with the level of detail needed at each **zoom level**.    

#### Zoom Levels
Because web maps refresh content as you zoom in, they don't have a traditional map scale. Instead, there are different levels associated with the amount of detail shown on the map.
Web maps typically have around 20 zoom numbered levels. Zoom level 0 has the least amount of detail, and is from a viewpoint as far away as earth as it gets. As the zoom level number goes up, so does the detail. Zoom level 18 has enough detail that displaying building titles makes sense. Zoom level 0 consisting of only 1 tile for the entire world (this zoom level loads the fastest!). Zoom level 18 consists of around 69 billion tiles. That's a lot of data!!!!    

Level 0 | Level 18
--- | ---
![tiles](http://a.tile.openstreetmap.org/0/0/0.png) | ![tiles](http://a.tile.openstreetmap.org/18/41325/89736.png)
1 tile covers the world| 69 billion tiles cover the world    

<!-- Here's the map tile grid for **zoom level 11 over Vancouver**:    
![tiles](/img/vanzoom11.png)   

Here's the map tile grid for **zoom level 13 over Vancouver**:    
![tiles](/img/vanzoom13.png)   
-->


#### Tile Servers  
You might be thinking: ***Where are all these tiles loading from?*** Well, there are services that render these tiles for consumption. The main two being Google and [OpenStreetMap](https://wiki.openstreetmap.org/wiki/Tile_servers), but there are many others.     

You might also be thinking: ***Can I customize my own tiles to make them look cool?*** You can, with services like [Mapbox Studio](https://www.mapbox.com/mapbox-studio/). Or you can [set up your own server](https://medium.com/@Nithanaroy/create-your-own-tile-server-and-map-client-5f7515fff28) to render your own. But these options are both way beyond the scope of this workshop, so for now, don't worry about it. There are several out-of-the-box options to make your map tiles look sleek.    

Here are some interesting styles for the tile covering the south part of UBC Campus at zoom level 13:    

![tiles](img/dark.png)  ![tiles](img/fire.png)  ![tiles](img/otd.png)
![tiles](img/pio.png)  ![tiles](img/stm.png)  ![tiles](img/wtc.jpg)



#### Raster and Vector Tiles    
Another thing to understand about map tiles is that there are both raster and vector tiles. Raster tiles have been around longer, and so are a little simpler to tinker with when learning about and tinkering with web maps. This is why we're using raster tiles for this workshop. Features and attributes on raster tiles are static because they're just images, and there are other limitations on the way we can view and interact with them.    

Vector tiles contain vector data like feature names and other attribute data. While they have been around for several years, they are still newer and faster, and offer more customization options than raster tiles. These tiles are rendered as soon as your browser requests them from the tile server, freeing us from discrete zoom levels and map orientation. [Here's an example](https://openmaptiles.github.io/klokantech-terrain-gl-style/#13.88/49.2567/-123.2454/3.3/44).


### Data (.shp ⇢ .geojson)
Another moving part of a web map is the data added to it. While your map tiles are a necessary part of your map, they're really only there to provide reference to your data. Your data sits on top of your basemap. We call this your "data layer", "map content" and sometimes your "map features". Most of the time, your data is vector data so you can click and interact with it, but you can also add raster data as well.      

If you're a GIS user, you have encountered a Shapefile. Shapefiles are the industry standard file type for geographic vector data. If you've ever tried to share a Shapefile in the web, you've probably had some problems or the needed to transform your file into something else. Shapefiles are meant to be used in GIS and other software and weren't designed to be displayed in the web. [GeoJSON](https://geojson.org/) on the other hand, are geographic files which are meant for the web. They're "easy for humans to read, and easy for machines to read", meaning that they're a lightweight, simplified and format so your average web browser can use them, and they're also fairly easy to understand if you want to view and edit them in a code editor. Here's a GeoJSON point over UBC:

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
In contrast, a Shapefile is a binary (not text) format, so you wouldn't be able to read the file with human eyes. For these reasons, we're using GeoJSON files for this workshop.

One other great thing about GeoJSON, is that becuase they are open-source and simple to understand, there are several tools that allow you to create and edit them in the web, like [geojson.io](http://geojson.io).

**:heavy_check_mark: Copy the GeoJSON text above and paste it in the </>JSON panel in [geojson.io](http://geojson.io).**

**:heavy_check_mark: Click the edit layer button (above the trash can) to move the marker to a different position, then save.**

**:heavy_check_mark: In the Table panel, edit the GeoJSON file's attributes, by changing the name of the location.**

### Style 😎     
The basic building blocks of the web -- **HTML and CSS** -- also play a role in the way your map looks. We'll be creating a static HTML document to display our map as a full page document, but we could change the formatting with html code if we wanted to. CSS can be used to customize our HTML document, but also our data. Styling our geographic data (AKA digital cartography) so that it is accessible, helps convey a story, and looks good takes a lot of practice and talent. Expert digital cartographers are true artists.   

That said, we will rely on the Leaflet's built-in CSS rules for styling. However, in the future you can always customize these settings to fit the style of your own website or page.    

### Interaction
The interaction seen in web maps is powered by **JavaScript**. There are JavaScript libraries for ALL SORTS of things, and we're using Leaflet as a foundation for our maps. However you can add customization to your map so that it can do just about anything (remember those plugins?).    

For this workshop, we're not creating any new code or writing new scripts. We're just going to copy and paste some pre-assembled text so that you can see how it works to affect your map.

# Workshop
### Putting it into Perspective
Before we start working on our map, let's just put things into perspective. This is an introductory workshop, and meant to get you started with the tools and give you the skills to move forward on your own. Within the greater web mapping ecosystem, we're touching on the essentials. And give you an idea of how what we are doing fits into that ecosystem, take a [look at this diagram from Maptime](http://maptime.io/anatomy-of-a-web-map/#84), and notice the <HTML> document, and the internet browser.
### Software Used
We'll use two pieces of software - a web browser, which will render/display your map, and a source code editor to edit that map.
### Development Environment
First things first, let's set up your development environment which includes the two pieces of software, and a method for you to access them both efficiently. One option is to split your screen in half - web browser on one side and the code editor on another. Or you can move from one application tab to another by minimizing windows. It's totally your call, and the point is to find out what works best for you.
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

      //Paste UBC buildings variable here
      //Paste the L.geoJSON function here

      //Paste popup function here

    </script>
  </body>
</html>

```
**:heavy_check_mark: Copy the text above and paste it into a blank document in your code editor.**     

**:heavy_check_mark: Save the file to you computer and name it *ubc-buildings.html*.**


### In a Browser
Once you have your HTML file saved, open it in a new tab or browser window.    

**:heavy_check_mark: Right-click the .html file you just saved, and open with Google Chrome or Mozilla Firefox.**    

You should see a map that looks something like this:

![Map loads over the center of Vancouver](/img/map01.png "Your first map loads over Vancouver")


### In a Source Code Editor
Let's look at what is making this file work using our code editor. The HTML document is split into two main sections: (1) the <code>head</code> and the (2) <code>body</code>. Each of these sections are contained within opening and closing tags.
```
<head> some stuff </head>
<body> some other stuff </body>
```

#### Head
The stuff inside the <code>head</code> is the metadata for your browser about the document. Inside the <code>head</code> are things like the document’s title - in this case "Leaflet" - so that it can used for things like being displayed in your browser's tab. Additionally, there are some lines with links to the source code for Leaflet's JavaScript and CSS rules:     

```html
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.2.0/dist/leaflet.css" integrity="sha512-M2wvCLH6DSRazYeZRIm1JnYyh22purTM+FDB5CsyxtQJYeKq83arPe5wgbNmcFXGqiSH2XR8dT/fJISVA1r/zQ==" crossorigin=""/>
<script src="https://unpkg.com/leaflet@1.2.0/dist/leaflet.js" integrity="sha512-lInM/apFSqyy1o6s89K4iQUKg6ppXEgsVxT35HbzUupEVRh2Eu9Wdl4tHj7dZO0s1uvplcYGmt3498TtHq+log==" crossorigin=""></script>
```

If you copy either one of those links and paste it in a new tab in your browser, you’ll see a lot of raw code. By linking to the source, we avoid having to carry this text into our own document, while also being assured that the code we're using is up-to-date.
#### Body
The <code>body</code> is the container for the what you see formatted in your browser. Here, you have an HTML container for your map, which is styled to be the height of a full page.     
```HTML   
<div id="mapid" style="height: 100%;"></div>
```    
Also included in the <code>body</code> is a script that loads the map to your page.    
```JavaScript
var mymap = L.map('mapid').setView([49.2827, -123.1207], 11);

var Stamen_Terrain = L.tileLayer('https://stamen-tiles-{s}.a.ssl.fastly.net/terrain/{z}/{x}/{y}.{ext}', {
      attribution: 'Map tiles by <a href="http://stamen.com">Stamen Design</a>, <a href="http://creativecommons.org/licenses/by/3.0">CC BY 3.0</a> — Map data © <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
      subdomains: 'abcd',
      minZoom: 0,
      maxZoom: 18,
      ext: 'png'
        }).addTo(mymap);
```
The first line is our map variable. A JavaScript variable is something that holds values, and our <code>mymap</code> variable holds values for the initial starting view location and zoom level of the loading map.    

The other variable <code>Stamen_Terrain</code> hold values for the map tile layer that we are using for our base layer including where the tiles are coming from, a limit on the max and min zoom level, and attribution.   

## Configure the Starting View
Ok so we have our map boilerplate, and its a good starting point for making a map of UBC. One thing that we’ll notice is that when the map loads, it’s just starting over Vancouver, and not UBC. So let’s change that.

In the <code>mymap</code> variable you can see a couple of recognizable elements - most noticeably the latitude and longitude coordinate pair (49.2827, -123.1207). That location is the geographic center point for the city of Vancouver. When your browser loads the map, it starts with that point in the center of your screen.

Say we want to load the map over UBC, which is about 5 km to the west. We'd need to change that coordinate pair to be the center point of UBC. There are several ways to find this, but an easy one is to use [latlong.net](https://www.latlong.net/). Type in UBC in latlong.net, and you return a coordinate pair of 49.260605 and -123.245995.

**:heavy_check_mark: Replace the coordinate pair so your map loads over UBC.**

Save your .html file, and reload your browser. If everything went as planned, you should see this:


![Map loads over the center of UBC](/img/map02.png "Your second map loads over UBC")

If you don't see a map like the one above, undo your edit in your source code editor (**ctl + z**), and save (**ctl + s**) when it's working again. At that point try again making sure your code syntax is exactly as shown:

```javascript
var mymap = L.map('mapid').setView([49.260605, -123.245995], 11);
```

### Zoom Levels
Your map currently loads at a zoom level which requires a user to zoom in immediately toward UBC. Ideally, if this map is meant to show information for UBC's campus, it would load as close to campus as possible, but not so close that different screen dimensions cut off parts of the campus area. So we'll need to change the loading zoom level.

Looking again at our <code>mymap</code> variable, the loading view is set at the coordinate pair over UBC, and at a zoom level of 11. In our case, the map best loads at zoom level 14.

**:heavy_check_mark: Change your loading zoom level your map loads at zoom level 14.**    

You should see this if you save and refresh your map:

![Map loads over the center of UBC!](/img/map03.png "Map loads over the center of UBC!")

## Adding Data
Let's add some map features!!

### Add a Marker
Leaflet gives us an easy way to add basic map features called **markers**, which represent point locations on the ground. More information about adding basic features to Leaflet can be found in the [Leaflet Quick Start Guide](https://leafletjs.com/examples/quick-start/). Let's add a marker over UBC campus.    

**:heavy_check_mark: Add a Leaflet marker by copy/pasting the text below into the body of your HTML document.<code>body</code>.**

```JavaScript
var ubccampus = L.marker([49.260605, -123.245995]).addTo(mymap).bindPopup("Hi Mom!");

```    
You should see something like this (click on the marker too!):    

![Map loads over the center of UBC with a marker!](/img/map04.png "Map loads over the center of UBC with a marker!")


### Add a GeoJSON
GeoJSON are often more complex data than markers or shapes. But they can be added to your map similarly: by creating a new variable holding the values for the GeoJSON feature(s).    

Let's add a GeoJSON that represents UBC Buildings. Luckily, UBC's Campus and Community Planning releases their data as GeoJSON with an open license. We can [find the data here](https://github.com/UBCGeodata). For this workshop, let's use [this](https://github.com/ect123/intro-to-leaflet-workshop/blob/master/maps/ubcbuildings.js) buildings variable made from the UBCGeodata repository.    

**:heavy_check_mark: Copy/paste the [UBC building variable](https://github.com/ect123/intro-to-leaflet-workshop/blob/master/maps/ubcbuildings.js) into the body of your HTML document, just after your <code>ubcbuildings</code> variable.**

Then we need to include a Leaflet function so that our map loads this data.    

**:heavy_check_mark: Add the buildings to your map by copy/pasting the function below into your HTML document.**    

```JavaScript
L.geoJSON(ubcbuildings).addTo(mymap);
```    

You should see something like this after you save and reload your browser:    


![Map loads over the center of UBC with a marker, and a data layer!](/img/map05.png "Map loads over the center of UBC with a marker, and a data layer!")

## Change the Base Map/Layer Style
Suppose we want our data to stand out from the green base map more than it does now. One thing we can do is change the source of the map tiles to one that has a more appropriate style for our blue data. As mentioned earlier, there are several out of the box options to choose from with a variety of different styles. [This page lists a number of different map tile sources](https://leaflet-extras.github.io/leaflet-providers/preview/), and provides the text to paste into our map document for each one (minus the important <code>.addTo(mymap)</code> which needs to be inserted before the final semi-colon). **some of these sources require an access token, so you won't be able to use them unless you sign up for an account**. For our data, let's choose the Stamen.TonerLite tiles since they're lightly colored and they don't require an access token.    

**:heavy_check_mark: Copy the text below and replace the existing map tile variable in your HTML document.**

```JavaScript
var Stamen_TonerLite = L.tileLayer('https://stamen-tiles-{s}.a.ssl.fastly.net/toner-lite/{z}/{x}/{y}{r}.{ext}', {
	attribution: 'Map tiles by <a href="http://stamen.com">Stamen Design</a>, <a href="http://creativecommons.org/licenses/by/3.0">CC BY 3.0</a> &mdash; Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
	subdomains: 'abcd',
	minZoom: 0,
	maxZoom: 20,
	ext: 'png'
})addTo(mymap);
```    



![Map loads over the center of UBC with a marker, a data layer, and a custom base map!](/img/map06.png "Map loads over the center of UBC with a marker, a data layer, and a custom base map!")

## Interaction

### Hover Effects
### Popups
If you want to change the popup text, feel free, or delete it all together.

![Map loads over the center of UBC with a marker, a data layer, a custom base map, and popup for the data layer!](/img/map07.png "Map loads over the center of UBC with a marker, a data layer, a custom base map, and popup for the data layer!")


## What's Next?    
You are not required to think about web maps ever again, but if this workshop has inspired you to expand your skills, try making another map on your own using data for a different location on your own. This will give you some clarity around where you might have some gaps in understanding. There are some additional clean .geojsons included here to practice. Remember, you can also create your own .geojson with free tools like [geojson.io](http://geojson.io).

***Keep in mind that not all data will be nicely packaged and cleaned. In fact, it never is. If you proceed to use data that you've found on the web, be prepared to spend time preparing your data to be usable with Leaflet and the web.***

### More Resources for Web Mapping
This workshop builds from several other resources for web mapping. Here are some great places to start extending your knowledge:

Web map basics: [Anatomy of a Web Map - Alan McConchie and Beth Schechter](http://maptime.io/anatomy-of-a-web-map/)    
Leaflet basics: [Leaflet Quick Start Guide](https://leafletjs.com/examples/quick-start/)   
Web map functionality examples: [Mapbox.js Examples](https://docs.mapbox.com/mapbox.js/example/v1.0.0/)    
GeoJSON: [More than you ever wanted to know about GeoJSON - Tom MacWright](https://macwright.org/2015/03/23/geojson-second-bite.html)    

### License
CC 0.0 Public Domain
