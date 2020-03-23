---
title: Geomesa SimpleFeatureType
date: 2018-05-22 22:19:00
categories:
- Big Data
- 

tags:
- big geospatial data
- spatiotemporal database
- hdfs
- geomesa
--- 

## Geomesa SimpleFeatureType

In GeoTools, a **SimpleFeatureType** defines the schema for your data. It is similar to defining a SQL database table, as it consists of strongly-typed, ordered, named attributes (columns). Likewise, in Geomesa **SimpleFeatureType** defines the *names* and *types* of attributes in a schema.There are some predefined **SimpleFeatureType** coming with the Geomesa tools. We can use a `specification string` or a `TypeSafe` configuration to define a **SimpleFeatureType**.

A **SimpleFeatureType** definition consists of an *attributes array*, and an optional *user-data* section. *attributes* is an array of column definitions, each of which must include a *name* and a *type*. *user-data* element consists of key-value pairs that will be set in the user data for the **SimpleFeatureType**.

For example:
```json
 twitter = {
      type-name = "twitter"
      fields = [
        { name = user_id      , type = String, index = true }
        { name = user_name    , type = String }
        { name = text         , type = String }
        { name = in_reply_to_user_id  , type = String }
        { name = in_reply_to_status_id, type = String }

        { name = hashtags             , type = String }
        { name = media                , type = String }
        { name = symbols              , type = String }
        { name = urls                 , type = String }
        { name = user_mentions        , type = String }

        { name = retweet_count        , type = Int }
        { name = lang                 , type = String }

        { name = place_name           , type = String }
        { name = place_type           , type = String }
        { name = place_country_code   , type = String }
        { name = place_full_name      , type = String }
        { name = place_id             , type = String }

        { name = dtg                  , type = Date }
        { name = geom                 , type = Point, srid = 4326 }
      ]
      user-data = {
        geomesa.table.sharing = "false"
      }
    }

```

Checkout next post about [geomesa converter]({{site.baseurl}}{% post_url 2018-05-23-geomesa-converter %}), which will discuss how to transform source file into SimpleFeatureType in Geomesa datastore. 