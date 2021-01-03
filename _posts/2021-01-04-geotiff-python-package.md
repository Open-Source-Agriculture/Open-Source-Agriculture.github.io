---
layout: post
title: The geotiff Python Package
subtitle: Reading and writing geotiff files with Python but without GDAL
tags: [Tiff, geospatial, python, GIS, DataScience]
cover-img: /assets/img/geotiff.png
thumbnail-img: /assets/img/geotiff.png
share-img: /assets/img/geotiff.png
---

*Draft*

#### [TT;DR](https://kipcrossing.github.io/2020-12-22-TT-DR/)?

I'm writing a [noGDAL](https://kipcrossing.github.io/2021-01-03-noGDAL/) python package for reading and writing geotiff files. You can view/follow the project in the [geotiff Github repo](https://github.com/Open-Source-Agriculture/geotiff).

## The start of a new noGDAL python package for reading and writing tiff files

During my adventures into geospatial python, I've noticed that there aren't any pure python packages for reading, manipulating and writing tiff files with python. There are GDAL and GDAL based packages, but GDAL can be a massive headache to install; it would be much better to have a noGDAL python package for this. 

You can read about the noGDAL philosophy in my article; [noGDAL: Geospatial Python without GDAL](https://kipcrossing.github.io/2021-01-03-noGDAL/).