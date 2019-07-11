
# Web Maps from Scratch with Leaflet.js

[menu]

# Introduction

#### GIS Resources at UBC:
- General Informational website for all things UBC GIS: [gis.ubc.ca](http://gis.ubc.ca/)    
- UBC Library's guide for finding and working with GIS resources: [guides.library.ubc.ca/gis](http://guides.library.ubc.ca/gis)
- UBC's GIS email list (participate or lurk!): [UBC GIS ListServ](https://lists.ubc.ca/scripts/wa.exe?SUBED1=GIS-LIST&A=1)  
- UBC's GIS Slack (create your own channel or lurk!): [ubcgis.slack.com](https://ubcgis.slack.com/)
- Evan Thornberry, GIS Librarian @ UBC Library: evan.thornberry AT ubc.ca

#### Prerequisites
This workshop is meant to be a starting point for anyone wanting to start making webmaps, and there are no actual prerequisites. That said, making digital maps is hard. Things that would be good to know before jumping right in (but you can do this after the workshop too!):
- [Familiarity with code and code editors](#)
- [Working knowledge of HTML / CSS](#)
- [Understanding of JavaScript](#)
- [Cartographic design principals](#)
- [Creating static web content](#)

### Resources for Web Mapping
This workshop builds on a zillion other resources for web mapping. Here are some other great places to start extending your knowledge:

### A Trusty Source Code Editor
To make your life easier what viewing or editing code, it's good to have a nice [source code editor](https://en.wikipedia.org/wiki/Source_code_editor) in your webmapping toolbelt. This workshop uses Atom.io for screenshots
### Workshop Data
All of the data you'll need for this workshop is included in this repository. If you'd like to download the whole package, click on the green download link (:exclamation:)
## Digital Map ≠ Web Map
### Digital Map
### Web Map

## What is Leaflet?
What exactly is leaflet? Leaflet is a set of instructions that your web browser or mobile device uses to display maps and let you interact with them. So like when you double click a mouse on a map, leaflet tells your browser to zoom in. Leaflet defines the style of your map - and includes things like zoom controls, attribution links, colors for markers on top of the map, etc. It is made up of only 38kb of Javascript, so it is really fast and lightweight - meaning browsers don’t have to work very hard to load it. It is open source, free, and hugely customizable. And because of all of that it is really widely used. There are lots of alternative to Leaflet, but I think the one that is most widely used is Google Maps, which you need an API key to use.
### As Code
Leaflet is JavaScript code library that provides interaction to web maps. It powers the ways your web browser interprets geospatial data, displays colors and styles, and provides interaction to maps. For instance, when you double click to zoom in, Leaflet is at work. When you add data to your map, Leaflet controls how it is displayed and how it interacts. And because Leaflet is distributed as open-source code, it is hugely customizable and extensible. [Here are some examples](https://leafletjs.com/plugins.html) of Leaflet-based plugins to give you some idea.

### In a Browser
Here is a basic [Leaflet map example](https://s3.amazonaws.com/ect123/PNWDC-Leaflet-2018/maps/map01.html). You can zoom in, pan around, etc. It's meant to be displayed in your internet browser or a mobile application, so it loads and responds to you quickly.  

## Basic Structure
Let's talk a little bit about what makes this map work. To do that, we'll dissect the
### Map Tiles
### Zoom Levels
### Tile Servers
### Raster and Vector Tiles
### Data (.SHP ⇢ .GeoJSON)
### Style
### Interaction

# Workshop
## Getting Started
### Software Used
We will be using two pieces of software - a web browser, which will render/display your map. We’re using I think Firefox. And a source code editor to edit the html file that contains the map. We are going to use Dreamweaver, which is our only option here. Dreamweaver isn’t my first choice, but it is all we have. I recommend using Atom if anyone is interested in doing this at home. Atom is free and open source, and full of bells and whistles. Anyone here familiar with using a source code editor for web technologies?
### Putting it into Perspective
### Development Environment
First things first, lets set up your development environment. This is a fancy way of saying make the tools you are using accessible on your computer screen display. In our case, we’re just using a web browser and Dreamweaver, so we’ll split our screen in half - web browser on one side and Dreamweaver on another. Let’s take a second to do this. Everyone open Dreamweaver. This is really entirely up to your personal preferences. Once everyone’s there we’ll go ahead.
## Create and Open Your Map Boilerplate
Below is a bunch of code - this is our map boilerplate. We need to cut this and paste this to a new file in Dreamweaver. It’s important that you don’t lose any of this text, so if you want just click the button and paste in Dreamweaver. Do that.

```HTML
<html>
                <head>

                <title>Leaflet</title>
                <meta charset="utf-8" />
                <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <!-- Leaflet JS and CSS CDN source-->
                <link rel="stylesheet" href="https://unpkg.com/leaflet@1.2.0/dist/leaflet.css" integrity="sha512-M2wvCLH6DSRazYeZRIm1JnYyh22purTM+FDB5CsyxtQJYeKq83arPe5wgbNmcFXGqiSH2XR8dT/fJISVA1r/zQ==" crossorigin=""/>
                <script src="https://unpkg.com/leaflet@1.2.0/dist/leaflet.js" integrity="sha512-lInM/apFSqyy1o6s89K4iQUKg6ppXEgsVxT35HbzUupEVRh2Eu9Wdl4tHj7dZO0s1uvplcYGmt3498TtHq+log==" crossorigin=""></script>
        <!-- jQuery CDN source-->
                <script type="text/javascript" src="https://code.jquery.com/jquery-3.2.1.min.js"></script>

                </head>

                <body>
        <!-- Container for your map -->
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

        //Plop your maker here

        //Plop UBC's buildings layer here (this uses jQuery)

        //Plop popup function here

			     </script>

  </body>
</html>



```

### In a Browser
Once you have pasted the text, save the file to your desktop. Save it as ubc-buildings.html. Once you save it, it should become colorful. When it is, in your browser, open a new tab open the file. Now you’ll have two tabs open in your browser, so I hope this isn’t too tricky.
### In a Source Code Editor
in Atom, lets look at what is making this file work. The html document is split into two sections - a head which is between lines 2-13, and a body between lines 15-39. Are you all seeing the lines? Each of these sections are contained in opening and closing tags. Insiide the head is the metadata that your browser is given about the document. And the body is the container for the document.
#### Head
inside the head are things like on line 4, the metadata field for the document’s title. Your title is displayed in your browser tab. Lines 8-9 are links to the source for leaflet - including the js library as well as the style sheet (the .css) that defines how elements of this map will look. And on line 11 is the same link to jQuery. If you copy the link to the leaflet js and paste it in a new tab in your browser, you’ll see the raw javascript code. If you wanted to, you could just add tthat to this page, but we don’t need to.
#### Body
In the body, you have on line 17, the container for your map (contained in a div tag), including a name/id for the container, as well as a style attribute telling your browser to make this container as high as the page allows. Line 19-37 is the script for your map. This is what we’ll be editing today.
#### Script
in the script, on line 22 we have our map variable containing the initial starting point and zoom level. When someone opens this page, or refreshed their browser, this is what the map will show. Zoom levels are a digital map’s way of dealing with scale. In the paper world we have maps that are printed at different scales which show differing levels of detail. A paper map with a small scale has little detail, a map at a large scale has lots of detail. But with digital maps, we can just double-click our mouse to load more detail. There are up to 22 standard zoom levels, with zoom level 22 being the most detailed, and zoom level 0 being all the way zoomed out to see the entire world. We also have in lines 24-31 a tile layer variable. Your tile layer in this case is the basemap that we see when we are zooming and panning. What that is is a streaming set of georeferenced tiles that we are pulling in from some remote server. And we are defining that in these lines. There’s some other info in here too like attribution and a max min zoom level - this particular layer will only zoom into layer 18. And then it stops.
## Configure the Starting View
Ok so we have our map boilerplate, and its a good starting point for making a map of ubc. One thing that we’ll notice is that when the map loads, it’s just starting over vancouver, and not UBC. So, let’s change that.

## Adding Data
### Markers
### GeoJSON

## Change the Basemap Style

## Interaction
### Hover Effects
### Popups
If you want to change the popup text, feel free, or delete it all together.
## What's Next?
### Thanks - Stamen Maps, Alan McConchie, Lizi Diamond, Axis Maps
### License
CC 0.0 Public Domain
