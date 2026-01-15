# Demo explanations

## Demo 2
This demo explores the help documentation. 
- [gis Module](https://developers.arcgis.com/python/guide/the-gis-module/)
- [Content Manager](https://developers.arcgis.com/python/api-reference/arcgis.gis.toc.html#contentmanager)

## Demo 3
This demo uses a notebook to explore Feature Layer properties. Help doc:
- [Item help](https://developers.arcgis.com/python/api-reference/arcgis.gis.toc.html#item)
- [FeatureLayer class](https://developers.arcgis.com/python/api-reference/arcgis.features.toc.html#featurelayer)
- Extra: When I cant find something, like the meaning of `maxRecordCount`, I go to the [ArcGIS REST API help doc](https://developers.arcgis.com/rest/services-reference/enterprise/feature-service/)

```python
from arcgis.gis import GIS
gis = GIS('pro')

RBtreesItem = gis.content.get('d3edc9376b1d4d20a93e3bfbad8e2bc0')
RBtreesItem.layers

lyr = RBtreesItem.layers[0]
lyr.properties['maxRecordCount']
```

## Demo 4
This is another example of a manager being accessed through a class. In this case, the FeatureLayerManager is accessed through the FeatureLayer class through the `manager` property and provides additional functionality for those with proper privileges (ownership or administrator role)
- Consider showing the differences between the two
- [Feature Layer manager](https://developers.arcgis.com/python/latest/api-reference/arcgis.features.toc.html#arcgis.features.FeatureLayer.manager)
- [Feature Layer Manager class](https://developers.arcgis.com/python/latest/api-reference/arcgis.features.managers.html#arcgis.features.managers.FeatureLayerManager)

```python
### Module importsfrom arcgis.gis import GIS
gis = GIS('pro')

### Access the featurelayer item, layer and manager property
RBtreesItem = gis.content.get('d3edc9376b1d4d20a93e3bfbad8e2bc0')
lyr = RBtreesItem.layers[0]
lyrMngr = lyr.manager

### Modify a field
modFldDefinition = {'fields':[{
			"name": "Status",
			"type": "esriFieldTypeString",
			"alias": "TreeSpecies",
			"sqlType": "sqlTypeOther",
			"length": 125,
			"nullable": True,
			"editable": True,
			"visible": True,
			"domain": None,
			"defaultValue": None
		}]}
lyrMngr.update_definition(modFldDefinition)
```

## Demo 5: Feature Service data structures
Here we explore the help doc. There is no code. This is the structure of a feature:
```python
{"attributes": 
           {"latitude": 33.75,
            "longitude": -118.25,
            "country": "US",
            "harborsize": "L",
            "label_position": "SW",
            "port_name": "LOS ANGELES",
            "short_form": "LAX"}, 
           "geometry": 
           {"x": -13044788.958999995, "y": 3857756.351200014}}
```
Resources:
- [Editing features](https://developers.arcgis.com/python/latest/guide/editing-features/)
- [Spatially enabled DataFrame Load data](https://developers.arcgis.com/python/latest/guide/introduction-to-the-spatially-enabled-dataframe/#accessing-gis-data)
- [Export options of the SEDF](https://developers.arcgis.com/python/latest/guide/introduction-to-the-spatially-enabled-dataframe/#export-options)
- [`edit_features` in the FeatureLayer help](https://developers.arcgis.com/python/latest/api-reference/arcgis.features.toc.html#arcgis.features.FeatureLayer.edit_features)