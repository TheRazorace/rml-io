## RMLTTC0006e

**Title**: Target TarGzip compression

**Description**: Test export all triples with TarGZip compression

**Error expected?** No

**Input**
 [http://w3id.org/rml/resources/rml-io/RMLTTC0006e/Friends.json](http://w3id.org/rml/resources/rml-io/RMLTTC0006e/Friends.json)

**Mapping**
```
@prefix rml: <http://w3id.org/rml/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix formats: <http://www.w3.org/ns/formats/> .
@base <http://example.com/rules/> .

<#DCATSourceAccess> a rml:Source, dcat:Distribution;
    dcat:downloadURL <http://w3id.org/rml/resources/rml-io/RMLTTC0006e/Friends.json>;
.

<#TriplesMap> a rml:TriplesMap;
  rml:logicalSource [ a rml:LogicalSource;
    rml:source <#DCATSourceAccess>;
    rml:referenceFormulation rml:JSONPath;
    rml:iterator "$[*]";
  ];
  rml:subjectMap [ a rml:SubjectMap;
    rml:template "http://example.org/{$.id}";
    rml:logicalTarget <#TargetDump1>;
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
    rml:predicateMap [ a rml:PredicateMap;
      rml:constant foaf:age;
    ];
    rml:objectMap [ a rml:ObjectMap;
      rml:reference "$.age";
    ];
  ];
.

<#TargetDump1> a rml:LogicalTarget;
  rml:target [ a rml:Target, dcat:Distribution;
    dcat:downloadURL <file://./dump1.nq.tar.gz>;
  ];
  rml:serialization formats:N-Quads;
  rml:compression rml:targz;
.

```

**Output 1**
```

```

**Output 2**
 `dump1.nq.tar.gz`

