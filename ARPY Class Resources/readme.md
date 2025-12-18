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
TThe GIS module consists of 5 main classes: GIS, User, Role, Group, Item
![gis module](https://developers.arcgis.com/python/latest/guide/images/guide_gis_module_01.png)
There are many manager classes in the API for Python. We've seen the UserManager class. 
Resource manager classes:
- Provide access to different properties and methods for a single item, or many items
- Examples: UserManager, ContentManager, GroupManager
- The "Resources" of a given item can be access via the `resources` property of an item.

Search in the ArcGIS API for Python [implements](https://developers.arcgis.com/python/latest/guide/accessing-and-creating-content/#searching-for-content:~:text=content.search()%2C-,implements,-the%20ArcGIS%20REST) the [ArcGIS REST API search operation](https://developers.arcgis.com/rest/users-groups-and-items/search/). `gis.content.search()` is the search resource manager.
- The search is fuzzy because the search engine uses many different inputs to rank and display results, which change (like view count). When automating a script, use `get` or search using `ID` when possible.
- > The ArcGIS Portal Directory REST API has a [full-featured text search engine](https://developers.arcgis.com/rest/users-groups-and-items/search-reference/#:~:text=The%20ArcGIS%20Portal%20Directory%20REST%20API%20has%20a%20full%2Dfeatured%20text%20search%20engine%20that%20allows%20you%20to%20create%20your%20own%20queries) that allows you to create your own queries
- One search parameter is `query`. [Without specifying the field used in your search, these are the default fields used to interpret the request](https://developers.arcgis.com/rest/users-groups-and-items/search-reference/#fields) for searching for items and groups. 
- Fields are used to focus the search.
    - [List of all Item fields](https://developers.arcgis.com/rest/users-groups-and-items/search-reference/#item-fields)
    - [List of all Group fields](https://developers.arcgis.com/rest/users-groups-and-items/search-reference/#group-fields)
- Without a field, the search ranks results according to various factors. You have less control this way. , `res = gis.content.search('Yosemite')` 

## Workflows for feature layer management

## Strategies for updating feature layer properties

## Strategies for editing feature layers