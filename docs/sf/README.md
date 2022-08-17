# Sharing Framework

In order for global analysis to be successful, organizations must participate above all. This includes sharing data with other organizations in order to build the corpus of data used in global analytics.

One key area to ensure sharing is tenable, is to minimize the barrier to entry for organziations. Any size organization should be able to contribute easily and receive contributions from others that can be readily used in their own analyses. This means the primary data to share must be: small, simple, timely, relevant and trustworthy. We can address each of these:

Small: data size must not be excessive, meaning it is must be calculated surrogates from raw data such as metrics or trained model parametrics (e.g. histograms or weights).

Simple: data must be easy to compute, format, transmit and integrate. This means we must consider Occam's razor and utilize the simplest structures and analytic methods that yield results. Each organization will determine what costs they can bear and vendors will implement tools of varying sophistication.

Timely: data must be exchanged in near-real-time at a rate that allows analytics to be updated at speed to enable detection and elimination of malware. The actual time resolution is to be determined, but is clearly closer to hourly than monthly.

Relevant: data must be relevant to both producers and consumers relative to the task(s) at hand. We need to detect attacks, persistent threats, lateral movements, etc. Any data to be shared must be usable to that end using the tools and techniques available to the parties involved.

Trustworthy: data must be trusted to be useful. It is important to both prevent bad actors from poisoning the well and to ensure once actors make it in they can be mitigated (e.g. via actor weighting and age-off). Analytic methods that favor good actors via crowd sourcing and/or ratings will additionally ensure participants can have an active role in curating trust.



The houskeeping bits are:

[standardization](standardization.md): how we plan to deal with a sharing framework via standardized data models

[standard markups](markup_model.md): the standard "language" for models - really loosely based on BNF/EBNF
And the [base types](base_types.md) that go along with defining a foundation for schema development.

[standard schemas](schema_defs.md): The directory of defined standard models / schemas