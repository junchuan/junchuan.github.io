---
title: Web map tiling
date: 2017-10-19 09:16:00
categories:
- Visualization

tags:
- geo-visualization
- map tile
- web map

---

To offer world map to user and allow user to interact, you have to pre-render the map at many different levels of details. The following is how Bing map organizes map tiles. 
After rendering ,you then cut each map into tiles for quick retrieval and display.
- First, we need a unified projection system.
- Second, set ground resolution or map scale. Ground resolution indicates the distance on the ground that’s represented by a single pixel in the map. At a map scale of 1:100,000, each inch on the map represents a ground distance of 100,000 inches.
```
map width = map height = 256 *  2^level  pixels  
ground resolution 
= cos(latitude * pi/180) * earth circumference / map width    
= (cos(latitude * pi/180) * 2 * pi * 6378137 meters) / (256 * 2^level) pixels  
map scale 
= 1 : ground resolution * screen dpi / 0.0254 meters/inch  
= 1 : (cos(latitude * pi/180) * 2 * pi * 6378137 * screen dpi) / (256 * 2^level * 0.0254)
```

- Third, set pixel coordinates. Since map width and height is different at each level, so are the pixel coordinates. Pixel at upper-left corner of the map has a pixel coordinate (0,0).
```
sinLatitude = sin(latitude * pi/180)   
pixelX = ((longitude + 180) / 360) * 256 * 2^level  
pixelY = (0.5 – log((1 + sinLatitude) / (1 – sinLatitude)) / (4 * pi)) * 256 * 2^level
```

Tile coordinates: to optimize the performance of map retrieval and display, the rendered map is cut into tiles of 256 x 256 pixels each.  
- Given a pair of pixel XY coordinates, you can easily determine the tile XY coordinates of the tile containing the pixel
```
tileX = floor(pixelX / 256)
tileY = floor(pixelY / 256)
```
Two-dimensional tile XY coordinates are combined into one-dimensional strings called quadtree keys, or “quadkeys” for short
```
tileX = 3 = 0112
tileY = 5 = 1012
quadkey = 1001112 = 2134 = “213”
```
- First, the length of a quadkey (the number of digits) equals the level of detail of the corresponding tile. 
- Second, the quadkey of any tile starts with the quadkey of its parent tile
- Finally, quadkeys provide a one-dimensional index key that usually preserves the proximity of tiles in XY space.  

Google Map and Openlayer use the similar idea but the tiling coordinates are different.
