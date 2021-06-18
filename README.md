# Saudi-Encyclopedia-Sparql

this repo contain a python Demo in How to use Saudi Encyclopedia Sparql Endpoint.
Encyclopedia URL http://158.101.230.190/mediawiki/index.php

**Example 1** 
اسعتادة جميع المحافظات المرتبطة بالصفحة الرئيسية

```python
from SPARQLWrapper import SPARQLWrapper, XML

sparql = SPARQLWrapper("http://158.101.230.190:8080/fuseki/ds/query")
sparql.setQuery("""

prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>
prefix owl: <http://www.w3.org/2002/07/owl#>
prefix property:<http://158.101.230.190/mediawiki/index.php/Special:URIResolver/Property-3A>
prefix wiki:<http://158.101.230.190/mediawiki/index.php/Special:URIResolver/>


SELECT  ?object
WHERE {
  wiki:الصفحة_الرئيسة property:مرتبط_ب ?object
}
LIMIT 25



""")

sparql.setReturnFormat(XML)
results = sparql.query().convert()

print(results.toxml())
```
