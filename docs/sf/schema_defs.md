# Schemas for Standardized Data
Each data type will have a standard definition that is expected for use in the CHASE (CLAP) flows. This will start with the concepts from the other documents in this repo, primarily [StandardDAGModel](../StandardDAGModel.md).

The Standardization of data is broken into 3 key areas:

- Entities (e.g. Logs and Features)
  - Entities are "objects" or "records" composed of many fields representing a singular thing, such as a "log entry"
  - Entities are composed of a combination of Sets and/or Values
- Sets (e.g. FeatureSets aka FieldSets)
  - Sets are a general term for a grouping of values that are taken as a unit for convenience. The Set is not itself an Entity, but is a group of fields within an Entity, such as the "connection properties" of an "http request". In this case, the "connection properties" are a field set within the "http request" entity.
  - The representation of a Set is dependent on the implementation, but are consistently defined in these specifications as "traveling together".
- Values (e.g. Feature, Field, etc.)
  - A value is a single property or field of an Entity or Set.
  - A value is a singular value, such as a string, int or float.
  - All values have a "type" (e.g. string) and all higher level constructs will define a "type constraint" for each value.

## Logs
Logs are entity types in the CHASE (CLAP) model and are therefore well defined. Log are composed of a combination of FieldSets and/or Values. In general, most values should support the notion of "nullability" in the case some source does not support a specific value in the entity.

Basic definitions for Log types and field sets are found here: [CommonLogTypes](../CommonLogTypes.md)

### CONN Log
A connection log entry represents a single instance of a connection/communication log event over any ip-related protocol.

### HTTP Log