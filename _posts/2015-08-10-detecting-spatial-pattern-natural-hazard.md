---
title: Detecting Spatial Patterns of Natural Hazard from Wikipedia Corpus
date: 2015-08-10 11:22:00
categories:
- Research

tags:
- big geospatial data
- geospatial semantic
- natural language processing 
- natural hazard
---


## Brief Description
Wikipeida corpus includes thousands of geo-tagged articles, including, for example, almost real-time updates on current and historic natural hazards. This includes user-contributed information about the location of natural hazards, the extent of the disasters, and many details relating to response, impact, and recovery. In this research, a computational framework is proposed to detect spatial patterns of natural hazards from the Wikipedia corpus by combining topic modeling methods with spatial analysis techniques.  

<!-- more -->

This research uses wildfire as the exemplar hazard, but this framework is easily generalizable to other types of hazards, such as hurricanes or flooding. The geo-tagged articles are converted into an LDA topic space based on the topic model, with each article being represented as a weighted multi-dimension topic vector. By treating each article’s topic vector as an observed point in geographic space, a probability surface is calculated for each of the topics. The spatial distribution of wildfire outbreaks in the US is estimated by calculating the weighted sum of the topic probability surfaces using a map algebra approach. 

![wildfire wikipedia result]({{ site.baseurl }}{% link assets/images/wiki-wildfire.png %})  



## Year
2015

## Team members
Junchuan Fan, Kathleen Stewart


## Publication
Fan, J. and Stewart, K., 2015. Detecting Spatial Patterns of Natural Hazards From the Wikipedia Knowledge Base. ISPRS Annals of Photogrammetry, Remote Sensing and Spatial Information Sciences, II-4/W2 (July), 87–93.