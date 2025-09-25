# ArcGIS API for Python
 This repo contains scripts focuing on the ArcGIS API for Python.

# Notes on the ArcGIS API for Python
## Things I wish I knew earlier
- Convert an `arcpy geometry object` using the object's `__geo_interface__` method.
- To bypass bad certificates, use the `verify_cert = False` argument when initializing the GIS class `arcgis.gis.GIS()`