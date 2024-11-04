# RDF Proofs

RDF Proofs are proofs described in RDF supported by logic described in RDF.

## Forward rules described in RDF
e.g.
```
# rdfs subclass
_:bng_1 log:implies _:bng_2.

_:bng_1 {
    var:A rdfs:subClassOf var:B.
    var:S a var:A.
}

_:bng_2 {
    var:S a var:B.
}
```

## Backward rules described in RDF
e.g.
```
# is the age of a person above some duration?
_:bng_1 log:isImpliedBy _:bng_2.

_:bng_1 {
    var:S :ageAbove var:A.
}

_:bng_2 {
    var:S :birthDay var:B.
    [] rdf:value ""; time:localTime var:D.
    (var:D var:B) math:difference var:F.
    var:F math:greaterThan var:A.
}
```

## Queries described in RDF
e.g.
```Turtle
# query for people above 80 years old
_:bng_3 log:query _:bng_3.

_:bng_3 {
    var:S :ageAbove "P80Y"^^xsd:duration.
}
```

## Proofs described in RDF
e.g.
```
# (rule instantiated_premise) log:proves instantiated_conclusion.
(_:bng_1 _:bng_2) log:proves _:bng_3.

_:bng_1 {
    _:bng_1_1 log:implies _:bng_2_1.
}

_:bng_2 {
    :Human rdfs:subClassOf :Mortal.
    :Socrates a :Human.
}

_:bng_3 {
    :Socrates a :Mortal.
}

_:bng_1_1 {
    var:A rdfs:subClassOf var:B.
    var:S a var:A.
}

_:bng_2_1 {
    var:S a var:B.
}
```

The `var:` prefix is `<http://www.w3.org/2000/10/swap/var#>` and is used for
variables that are interpreted as universally quantified variables except for
forward rule conclusion-only variables which are interpreted existentially.

Literal subjects are described as
```
[] rdf:value "aha"; :p :o.
```
