

#All museums (including subclass of museum) in Washington, D.C. with coordinates
#defaultView:Map
SELECT DISTINCT ?item ?name ?coord ?lat ?lon
WHERE {
   ?item wdt:P131* wd:Q60 .
   ?item wdt:P31/wdt:P279* wd:Q24354 .
   ?item wdt:P625 ?coord .
   ?item p:P625 ?coordinate .
   ?coordinate psv:P625 ?coordinate_node .
   ?coordinate_node wikibase:geoLatitude ?lat .
   ?coordinate_node wikibase:geoLongitude ?lon .
  SERVICE wikibase:label {
    bd:serviceParam wikibase:language "en" .
    ?item rdfs:label ?name
   }
}
ORDER BY ASC (?name)
