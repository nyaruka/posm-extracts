# POSM-Extracts

This is snapshot of the Open Street Map boundary data extracted using the [POSM Extractor](https://github.com/nyaruka/posm).  We'll make a best effort to keep these up to date as we run them, though note that we only tend to rerun extracts when we find problems and we only look hard for countries we are currently involved in.

In time we'd like to automate the process of building and updating these. Note that we will NOT accept updates or corrections to this data. If you want to change something, change it in OSM and get it reviewed and notify us and we'll try to run a new extract, but the whole point is that this data is not massaged in any way but rather reflects the current state of OSM.

Organization
--------------

Apologize for the flat structure, these files were made for consumption by other scripts. We'd like to switch to using directories and ISO codes for filenames in time.

Right now filenames correspond to the relation id of the country as known in OSM. You can easily find these using [Open Street Map](http://www.openstreetmap.org/) by searching for a country name, then looking for the country boundary result. Click on it and your URL should be something like ```http://www.openstreetmap.org/relation/114686``` where 114686 is the relation id (in this case for Mexico). That corresponds to the files starting with R (for relation) 114686.

For each country we create six files, all our valid GEOJSON:
    [id]admin0.json - Full resolution of the country boundary
    [id]admin0_simplified.json - Simplified country boundary appropriate for use in web browsers
    [id]admin1.json - Full resolution of the state boundaries (level 1 administrative levels)
    [id]admin1_simplified.json - Simplified state boundaries
    [id]admin2.json - Full resolution of the district boundary (level 2 administrative levels)
    [id]admin2_simplified.json - Simplified district boundaries

For each feature in the GEOJSON we add the following attributes to let you build a parent-child relationship:
 - osm_id: This is id of the source Open Street Map object that this feature was built from
 - name: The local name for this feature
 - name_en: The English name for this feature
 - iso3166: The ISO code for this feature if a country
 - is_in_country: The osm_id of the feature that contains this feature (None if a country)
 - is_in_state: The osm_id of the feature that contains this feature (None if a country or state)



  
