# Streamline GIS Content Management with ArcGIS API for Python
Here I will keep notes and resources about this course.

## Connecting to an organization
Classes seen: 
- `GIS` class
- `PropertyMap` class with `helperServices` property
- `UserManager` class with `me` property

Technical concepts:
- Authentication schemes
- Organization architecture; ArcGIS Online and/or Enterprise on one/multiple servers.

Classes mentioned:
- `arcgis.features.GeoAccessor` class adds the `spatial` namespace to the Pandas DataFrame.
    - Some functionality from this class requires a geometry engine. We prefer ArcPy. If not available, other packages, like GDAL, can be used [(see help doc)](https://developers.arcgis.com/python/latest/api-reference/arcgis.features.toc.html#arcgis.features.GeoAccessor:~:text=%3Cmem_addr%3E%3E-,NOTE,-Setting%20the%20I)

    ```python
    import os
    os.environ["ARCGIS_IO_ENGINE"] = "<engine of choice>"  # e.g., "gdal"
    ```
    - Examples are: `arcgis.GeoAccessor.from_featureclass`, `arcgis.FeatureSet.from_arcpy`, `GeoAccessor.from_table`, `arcgis.GeoAccessor.select`, and potentially more.

## Strategies for content management
There are many manager classes in the API for Python. We've seen the UserManager class. 
Resource manager classes:
- Provide access to different properties and methods for a single item, or many items
- Examples: UserManager, ContentManager, GroupManager
- The "Resources" of a given item can be access via the `resources` property of an item.

Search in the ArcGIS API for Python [implements](https://developers.arcgis.com/python/latest/guide/accessing-and-creating-content/#searching-for-content:~:text=content.search()%2C-,implements,-the%20ArcGIS%20REST) the [ArcGIS REST API search operation](https://developers.arcgis.com/rest/users-groups-and-items/search/). `gis.content.search()` is the search resource manager.

## Workflows for feature layer management

## Strategies for updating feature layer properties

## Strategies for editing feature layers