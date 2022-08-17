[[_TOC_]]

# Background

Things will come in 2 core flavors:
1 - Concept
    - The notional thing, e.g. a struct or class definition, which is the model definition
    - In this space, the concept is the schema, or "table" structure

2 - Instance
    - The specific thing, e.g. an object or instance of a concept, which is the "data"
    - In this space, the instance is the data or "rows" conforming to the concept structure


# Defining Concepts

The schema language in our model is intended to be simple so it can be modelled universally.

example schema:

```
{
    name: 'url',
    type_id: '<some uuid literal>'
    properties: [
        {name: 'protocol', type: '<some uuid literal of another type>'},
        {name: 'host', type: '<some uuid literal of another type>'},
        {name: 'port', type: uint8},
        {name: 'path', type: '<some uuid literal of another type>'},
        {name: 'query', type: '<some uuid literal of another type>'}
    ]
}
```

This is just one form of encoding for the schema definition that is json/hocon-like, and other encodings are naturally relvant.
A simple alteration of this model to a more "C-like" definition follows:

```
[type_id = <some uuid literal>]
struct url {
   <some uuid literal of another type> protocol;
   <some uuid literal of another type> host;
   uint8 port;
   <some uuid literal of another type> path;
   <some uuid literal of another type> query;
}
```