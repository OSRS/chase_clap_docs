# Feature Engineering

The features used in global analysis will be based upon "raw log" features - the properties that are intrinsic in what is measured, plus features derived from these properties.

A feature is a "column" or "property" of a "row" or "record" of data.

Features can be singular, or grouped to "feature groups" (columns that always appear together).

Raw features are the features that are directly captured in logs such as TCP logs, HTTP logs, PCAP logs, etc. Through standardization in the SF area, we will define the standard raw features and where they appear.

Synthetic (Computed) features are features generated from other features (Raw, Synthetic or both), often as a "roll-up" (such as min/max/mean).