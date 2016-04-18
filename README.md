# History of theaters in New York City

Repository created during [Broadway Hackathon 2016](http://www.nypl.org/blog/2016/02/19/announcing-broadway-hackathon).

Goal: create (crowd-sourced) database of the history of NYC's theaters.

## Wikidata

https://query.wikidata.org

```sparql
#defaultView:Table
SELECT DISTINCT ?item ?name ?lat ?lon ?ibdbid ?owner ?capacity ?openingDate ?architect ?address
WHERE {
   ?item wdt:P131* wd:Q60 .
   ?item wdt:P31/wdt:P279* wd:Q24354 .
   OPTIONAL { ?item wdt:P1217 ?ibdbid } .
   OPTIONAL { ?item wdt:P127 ?owner } .
   OPTIONAL { ?item wdt:P1083 ?capacity } .
   OPTIONAL { ?item wdt:P1619 ?openingDate } .
   OPTIONAL { ?item wdt:P84 ?architect } .
   OPTIONAL { ?item wdt:P969 ?address } .
   OPTIONAL { ?item p:P625 ?coordinate .
   ?coordinate psv:P625 ?coordinate_node .
   ?coordinate_node wikibase:geoLatitude ?lat .
   ?coordinate_node wikibase:geoLongitude ?lon } .
  SERVICE wikibase:label {
    bd:serviceParam wikibase:language "en" .
    ?item rdfs:label ?name
  }
}
ORDER BY ASC (?name)
```

## Google Spreadsheet

https://docs.google.com/spreadsheets/d/17iY1RrtjrBksKMd7SP7mj34RZnaj1sZ90MmDtkBTKNs/pubhtml
