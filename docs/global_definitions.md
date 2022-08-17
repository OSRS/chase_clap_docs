[[_TOC_]]

# Global Definitions

## Notional Concept
In order to be successful at global analyses, organizations have to share some form of data. For that data to be interoperable, we need good working definitions upon which to build operational semantics that support inter-organizational operations.

[Standardization](sf/standardization.md) is the key to enabling inter-organizational interoperability of analytics. In the cyber realm, much of the standardization will be based upon log data, which often originates relative to some current [RFC](https://en.wikipedia.org/wiki/Request_for_Comments).

The CLAP framework defines a set of standard data models that attempt to partition, group and compute data based on the premise that the raw (source) data is derived from these well-defined RFC conforming sources and that minimal processing should occur to maintain a measure of tracability back to the RFC defined models. This approach should provide some measure of simplicity to implementers.

## Terms

NOTE: terms and definitions are still in a working state and subject to change

| Term | Definition |
| ----- | ----- |
| Log (File) | the automatically produced and time-stamped documentation of events relevant to a particular system. Virtually all software applications and systems produce log files |
| RFC | https://en.wikipedia.org/wiki/Request_for_Comments  A Request for Comments (RFC) is a publication from the Internet Society (ISOC) and its associated bodies, most prominently the Internet Engineering Task Force (IETF), the principal technical development and standards-setting bodies for the Internet. |
| Data Model | https://en.wikipedia.org/wiki/Data_model A data model (or datamodel) is an abstract model that organizes elements of data and standardizes how they relate to one another and to the properties of real-world entities. For instance, a data model may specify that the data element representing a car be composed of a number of other elements which, in turn, represent the color and size of the car and define its owner |
| Entity | a thing with distinct and independent existence, an **instance** of an entity type, such as "My Car" is an entity of type "Car" |
| Entity Type | a definable **concept** that an entity is an instance of, such as "Car" is an entity type where "My Car" is an entity of type "Car" |
| Field | A single well-defined **data column** that is computed from other data. (e.g. avg request body size) any field may be a "feature" if it is computed rather than measured |
| Field Set | A grouping of fields that are taken together in a single "round" and are therefore generally assumed to be collectively present or absent. |
| Raw Data | Data taken from a measurement or collection source, such as log data. |
| Raw Log Data | Raw Data consisting of (computer) log messages. (e.g. HTTP logs) |
| Feature | A single well-defined data column that is computed from other data. (e.g. avg request body size) a specific type of "Field" |
| Basic Feature | A feature computed soley from raw data. |
| Compound Feature | A feature computed from one or more other features. |
| Complex Feature | A feature computed from a combination of raw data and one or more other features. |
| Feature Set | A grouping of features that are computed together in a single "round" and are therefore generally assumed to be collectively present or absent. (e.g. min/max/mean count of requests per host) |
| Scores | A single or group of numeric values in the range of 0-1 that indicate some notion of likelihood, certainty, percentage, etc., often the result of an analytic prediction step. (e.g. goodness/badness score pair) | 
| Maliciousness Scores | A single or pair of score values that indicate the maliciousness/benigness (badness/goodness) of an item. In a pair, each value 0-1 represents the relative "goodness" or "badness" of the item. The sum of the scores is not limited to 0-1 but instead 0-2 (goodness and badness can conflict). A single score value represents the gradient score from "goodness" at 0 to "badness" at 1. |
| Analytic | A computational model to derive a resulting score or other outcome. Analytics may use any combination of raw data, features and scores as needed. An analytic should function with a lack of input in a predictable way (e.g. a feature is missing from the input). | 
| Trained Analytic | An analytic in which there are distinct "training" and "predcition" phases. Each of these phases has a distinct input data requirement. The training phase will result in an "Analytic Metric Set" that is used as input during the "prediction" phase along with any other required data. | 
| Untrained Analytic | An analytic in which there is no discinct "training" and "prediction" phases. Data in passed in and an analytic result is passed out. | 
| Training Features | The features expected to be sent to an analytic for some phase. This is essentially the definition of the expected inputs. |
| Training Data Set | A collection of actual data sent to a Trained Analytic to perform a training phase, which results in an Analytic Metric Set. | 
| Analytic Metric Set (AMS) | A collection of values output by an training run of a Trained Analytic. This will ultimately be an input to the Training Analytic for a subsequent "prediction" phase. |


## Types

In this context, "types" means types or classifications of features, organizations and processes. In order for global analysis to be successful, it is necessary to at least consider the barrier to entry and cost for an organization to participate in some way. As such, we will first define the ways that inter-organizational flows work.

### Comms Models

| Term | Definition |
| ----- | ----- |
| Inbound only | Data is consumed from other organizations and nothing is shared back. |
| Outbound only | Data is shared out to a community, but no data is consumed from other organizations. |
| Bidirectional | Data is shared out and consumed from other organizations. |
| Share Type | Type of the data to be shared. |
| Raw Data Share | Sharing of raw data. This is not expected across organization from the CHASE model. All raw sharing is considered to be "organization local", but perhap across data centers. |
| Feature Share | Sharing of features. This is expected to be somewhat limited with only specific features being shared between organizations with an adequate level of trust to share the specific features. Some features may be considered to be "globally safe" to share, but that is still unlikely. |
| Untrainined Analytic Share | Sharing of the results of an Untrainined Analytic. This is one common sharing expectation. |
| Analytic Metric Set Share | Sharing of the results of an Analytic Metric Set from a Trained Analytic. This is one common sharing expectation. |


### Organization Types

| Term | Definition |
| ----- | ----- |
| Type 1 | Organization that has ample resources to deploy technology as needed to support analytics of any scale. |
| Type 2 | Organization that has moderate resources to compute features and analytics but cannot support high-complexity analytics |
| Type 3 | Organization that has limited resources to compute features and analtyics such that they will tend to be able to use Trained Analtyics that are of moderate-complexity |
| Type 4 | Organization that has extremely limited resources or operational constraints that prevent computation beyond that supportable from one or two standalone workstations. Often this organization can have one of thousands of desktops in the network but few dedicated servers (e.g. AD, email, file share/NAS) |


### Trained Analytic Types

| Term | Definition |
| ----- | ----- |
| Type 1 | Analytic Metric Sets can be combined directly to form a new Analytic Metric Set which can then be used for a prediction phase. |
| Type 2 | Analytic Metric Sets cannot be combined directly, instead each of multiple AMS are used in a separate prediction phase where the resulting Scores can be directly combined to form a merged score. |
| Type 3 | Analytic Metric Sets cannot be combined directly, nor can resulting scores be combined. This is a standalone analytic. |
