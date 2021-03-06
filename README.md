![gdal2mb logo](http://mapbox.com/sites/mapbox.com/files/imagecache/scale_150x/tools_gdal2mb.png)

An importer for [MBTiles](https://github.com/mapbox/mbtiles-spec) that processes GeoTIFF and other [GDAL](http://www.gdal.org/)-compatible [raster](http://en.wikipedia.org/wiki/Raster_graphics) formats into tilesets.

### Installation

* GDAL
 * OSX: [GDAL Complete](http://www.kyngchaos.com/software/frameworks) from kyngchaos
 * Other systems: [GDAL binaries](http://trac.osgeo.org/gdal/wiki/DownloadingGdalBinaries)
* [Python](http://www.python.org/) (included on OSX and Linux)

Clone the repository

    git clone git://github.com/mapbox/raster2mb.git

Add raster2mb to your PATH and make it executable.

### Usage

    raster2mb raster_merc.tiff raster_merc.mbtiles

_If GeoTIFFs are in projections other than `EPSG:900913` (as many are), run gdalwarp first:_

    gdalwarp -t_srs EPSG:900913 raster.tiff raster_merc.tiff

Run `raster2mb -h` for usage instructions.

### Description

This is a variation of the [gdal2tiles](http://www.klokan.cz/projects/gdal2tiles/) script that supports MapBox `mbtiles` SQLite tilesets as an output option. It has the same requirements as the original script - notably an installation of [GDAL](http://www.gdal.org/).

### MBTiles

This tool is compatible with [MBTiles 1.1](https://github.com/mapbox/mbtiles-spec/blob/master/1.1/spec.md). It does not implement the optional `bounds` entry.

### Restrictions

Because mbtiles is limited in the profiles it supports, it is only possible
to use it to create tilesets from imagery that covers the entire world; 
imagery which is smaller will create a database successfully, but it will
not be in the neccesary spherical mercator profile. If you wish to build a
tileset, you must first make your image cover the entire world.
