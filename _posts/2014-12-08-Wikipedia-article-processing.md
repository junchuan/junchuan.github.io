---
title: Processing geotagged wikipedia articles 
date: 2014-12-08 11:29:00
categories:
- Big Data

tags:
- wikipedia 
- geospatial semantic
- natural language processing


---

The wikipedia maintainers provide an XML dump of all documents in the database each month. It is a single XML file that contains all the articles in wikipedia. 
- Content
  - Text of current version all pages
  - Some database tables:
    - Page-to-page links
    - list of pages with links outside of the project
    - Media metadata
    - Info about each page
    - Titles of all pages in the main namespace
    - List of pages that are redirects and their targets  
- Data format: The format of the XML file you receive is the same in all ways. It is codified in [XML Schema](http://www.mediawiki.org/xml/export-0.8.xsd).  
- What is wikitext?  
A lightweight markup language used to write pages at wiki-based websites. Wikitext can be converted into html by wiki software.  

- Coord template  
To add `57°18′22″N`,`4°27′32″W` to the top of an article, use {{ "`{Coord`"}}`}`,thus:  
{{ "`{{Coord|57|18|22|N|4|27|32|W|display=title`"}}`}}`   
These coordinates are in degrees, minutes, and seconds of arc. `'title'` means that the coordinates will be displayed next to the title.  
To add `44.112°N 87.913°W `to the top of an article, use either  
{{"`{{Coord|44.112|N|87.913|W|display=title`"}}`}}`  
or  
{{"`{{Coord|44.112|-87.913|display=title`"}}`}}`  
The template displays the formatted coordinates with a hyperlink to GeoHack. 
For terrestrial locations, a blue globe appears to the left of the hyperlink. 




