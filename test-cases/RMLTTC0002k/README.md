## RMLTTC0002k

**Title**: Multiple Targets: Datatype Map and Graph Map

**Description**: Test exporting all triples to a Target in a Datatype Map and a Target in a Graph Map.

**Error expected?** No

**Input**
 [http://w3id.org/rml/resources/rml-io/RMLTTC0002k/Friends.json](http://w3id.org/rml/resources/rml-io/RMLTTC0002k/Friends.json)

**Mapping**
```
@prefix rml: <http://w3id.org/rml/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix formats: <http://www.w3.org/ns/formats/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix ex: <http://example.org> .
@base <http://example.com/rules/> .

<#DCATSourceAccess> a rml:Source, dcat:Distribution;
    dcat:downloadURL <http://w3id.org/rml/resources/rml-io/RMLTTC0002k/Friends.json>;
.

<#TriplesMap> a rml:TriplesMap;
  rml:logicalSource [ a rml:LogicalSource;
    rml:source <#DCATSourceAccess>;
    rml:referenceFormulation rml:JSONPath;
    rml:iterator "$[*]";
  ];
  rml:subjectMap [ a rml:SubjectMap;
    rml:template "http://example.org/{$.id}";
  ];
  rml:predicateObjectMap [ a rml:PredicateObjectMap;
    rml:predicateMap [ a rml:PredicateMap;
      rml:constant foaf:name;
    ];
    rml:objectMap [ a rml:ObjectMap;
      rml:reference "$.name";
    ];
  ];
  rml:predicateObjectMap [ a rml:PredicateObjectMap;
    rml:graphMap [ a rml:GraphMap;
      rml:constant ex:PeopleGraph; 
      rml:logicalTarget <#TargetDump1>;
    ];
    rml:predicateMap [ a rml:PredicateMap;
      rml:constant foaf:age;
    ];
    rml:objectMap [ a rml:ObjectMap;
      rml:reference "$.age";
      rml:datatypeMap [ a rml:DatatypeMap;
        rml:constant xsd:integer;
        rml:logicalTarget <#TargetDump2>;
      ];
    ];
  ];
.

<#TargetDump1> a rml:LogicalTarget;
  rml:target [ a rml:Target, dcat:Distribution;
    dcat:downloadURL <file://./dump1.nq>;
  ];
  rml:serialization formats:N-Quads;
.

<#TargetDump2> a rml:LogicalTarget;
  rml:target [ a rml:Target, dcat:Distribution;
    dcat:downloadURL <file://./dump2.nq>;
  ];
  rml:serialization formats:N-Quads;
.

```

**Output 1**
```

```

**Output 2**
```
<http://example.org/0> <http://xmlns.com/foaf/0.1/age> "33"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/1> <http://xmlns.com/foaf/0.1/age> "34"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/2> <http://xmlns.com/foaf/0.1/age> "35"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/3> <http://xmlns.com/foaf/0.1/age> "36"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/4> <http://xmlns.com/foaf/0.1/age> "37"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .

```

**Output 3**
```
<http://example.org/0> <http://xmlns.com/foaf/0.1/age> "33"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/1> <http://xmlns.com/foaf/0.1/age> "34"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/2> <http://xmlns.com/foaf/0.1/age> "35"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/3> <http://xmlns.com/foaf/0.1/age> "36"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .
<http://example.org/4> <http://xmlns.com/foaf/0.1/age> "37"^^<http://www.w3.org/2001/XMLSchema#integer> <http://example.org/PeopleGraph> .

```

