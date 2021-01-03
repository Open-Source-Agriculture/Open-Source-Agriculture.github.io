---
layout: post
title: The geotiff Python Package
subtitle: Reading and writing GeoTIFF files with pure Python 
tags: [GeoTiff, geospatial, python, GIS, DataScience, noGDAL]
cover-img: /assets/img/geotiff.png
thumbnail-img: /assets/img/geotiff.png
share-img: /assets/img/geotiff.png
---

#### [TT;DR](https://kipcrossing.github.io/2020-12-22-TT-DR/)?

I'm writing a [noGDAL](https://kipcrossing.github.io/2021-01-03-noGDAL/) python package for reading and writing geotiff files. You can view/follow the project in the [geotiff Github repo](https://github.com/Open-Source-Agriculture/geotiff).

---

## Reading and writing GeoTIFF files with pure Python 

During my adventures into geospatial python, I've noticed that there aren't any pure python packages for reading, manipulating and writing GeoTIFF files with python. There are GDAL and GDAL based packages, but GDAL can be a massive headache to install; it would be much better to have a noGDAL python package for this. You can read about the noGDAL philosophy in my article; [noGDAL: Geospatial Python without GDAL](https://kipcrossing.github.io/2021-01-03-noGDAL/).

## The Start of a Project

I've made a little bit of progress with the [geotiff package](https://pypi.org/project/geotiff/) that provides a simple proof of concept. However, there is still a big learning curve and a lot to do. I think this would be a cool project and a great opportunity to learn, in detail, about the structure of GeoTIFF files. So before continuing the development of this package, I'd like to invite you, and anyone who would be interested in this project to become a contributor and give their input. Please come and introduce yourself on the [projects discussion board](https://github.com/Open-Source-Agriculture/geotiff/discussions/4). 

## Flavour

The following are the features that I would like to see included in this package (open for discussion).

### Core Features

- read tiff files (including BigTiff)
- write tiff files (including BigTiff)
- convert between coordinate systems
- cut a section (bounding box) of the tiff file
- convert the data to numpy arrays

### Additional features 

- Full test coverage
- Typing with lint checking using mypy
- Documentation: doc blocs and readthedocs

## Ingredients 

Based on my research, these are the dependencies that would be used to achieve the above feature goals. 

### tifffile

The [tifffile](https://pypi.org/project/tifffile/) package will be the core dependency that this project will be based around. It will give us the ability to; read and write to and from numpy arrays, read and write the geotags and even handle bigTiff files. Because of this project, most of the work is already done for us.  

### numpy

[Numpy](https://pypi.org/project/numpy/) arrays will be the main outputs when reading the GeoTIFF files. Arrays will give the user the flexibility to manipulate the data however they want. They can also 

### pyproj

The [pyproj](https://pypi.org/project/pyproj/) dependency will be used for converting between different coordinate systems. It would be preferable to abstract coordinate conversion away from the user as much as possible while still giving the flexibility to change the defaults; if needed. 

### zarr
With [zarr](https://pypi.org/project/zarr/), we will be able to read and write BigTIFF files. This would be a game-changing feature.  

### shapely
This one is a maybe. [Shapely](https://pypi.org/project/Shapely/) would be useful for cutting and masking based on polygons. There is also some other 'quality of life' features that may come in handy when working with 2d data. 

## Recipe

The core challenge of this project will be translating the [GeoTIFF spec](https://github.com/Open-Source-Agriculture/geotiff/blob/main/docs/geotif_spec.md) for reading the various geotags and obtaining the coordinate system that should be used to transform the coordinates. 

---

Again, if you see value in this project, please introduce yourself on the [projects discussion board](https://github.com/Open-Source-Agriculture/geotiff/discussions/4). It would be great to see you there are get your input.