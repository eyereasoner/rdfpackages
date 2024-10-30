# RDF Proof

## RDF Proof is supported by reasoning and querying in RDF TriG 

### Reasoning with forward rules described in RDF as
```
_:bng_1 log:implies _:bng_2.

_:bng_1 {
    RDF triples
}

_:bng_2 {
    RDF triples
}
```

### Reasoning with backward rules described in RDF as
```
_:bng_1 log:isImpliedBy _:bng_2.

_:bng_1 {
    RDF triple
}

_:bng_2 {
    RDF triples
}
```

### Querying with queries described in RDF as
```
_:bng_1 log:query _:bng_2.

_:bng_1 {
    RDF triples
}

_:bng_2 {
    RDF triples
}
```

The var: prefix is <http://www.w3.org/2000/10/swap/var#> and is used for
variables that are interpreted as universally quantified variables except for
forward rule conclusion-only variables which are interpreted existentially.

RDF proofs are composed of
```
(rule_or_query instantiated_premise) log:proves instantiated_conclusion.
```
triples.

Literal subjects are described as
```
[] rdf:value "aha"; :p :o.
```
