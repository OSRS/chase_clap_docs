[[_TOC_]]

# Global Analysis

## Notional Concept
Many organizations will participate in sharing of cyber security data, related to logs that each organization captures on their traffic.

No organization will share "raw log data" with other organziations due to concerns of privacy and security, so that idea is a hard rule. Additionally, "raw log data" is generally too large to effectively share.

Instead, organizations will compute some surrogate data such as "features", "metrics" and "analytics" that are suitably anonomized from the "raw log data" to enable sharing.  Still some organizations will only share select features while others will only receive data without contributing back.


## Environments

At the highest level, an analytic pipeline will look like the following:

```
RawLogData -> Features -> Sharing(Features)
RawLogData -> Features -> Analysis(Training) -> Sharing(Trained Data)
RawLogData -> Features -> Analysis(Training) -> Analysis(Prediction) -> Scores -> Sharing(Good/Bad Scores)

RawLogData -> Features -> Analysis(Training) -> Analysis(Prediction) -> Scores

RawLogData -> Features
Features   -^

Features -> Analysis(Training)
Features -^


Analysis(Tranining) -> Analysis(Prediction)
Features            -^
```

## Considerations
Each organization will have a different tolerance for cost to share as well as cost to compute. Some features and analytics should be "cheap" enough to be processed in near-real-time over streaming log data on a single workstation class machine.

Other features and analytics can be computationally expensive and require a cluster, such as Spark or ELK.  Where practical, the output of expensive compute should be sharable such as "cheap" compute can still make use of the results (e.g. Traning expensive, prediction cheap).


## Combiners, Trust and Sharing

Each participant in a sharing community will be able to either read, write or both to datasets that are then shared across the community. There must be a sense of trust in the community to rely on the shared data, which raises several concerns and considerations.

Each participant can be read-only or read-write in terms of data to share. Read-only should be encouraged for organizations that are not comforatble with sharing their data for any reason. This will be a line of defense against malicious members as well by restricting new members joining a community.

Just because a participant is read-only, they may divine meaningful information as an adversary from the received information, so even read-only access should be scrutinized.

### Types of bad data
Participants with write access can cause concern in several ways from data they share:

intentional bad data sharing -- aka lying
this can be performed by simply fabricating data or by performing analytics using fabricated or cherry-picked inputs. for these participants there is a need to detect, block and remove the organization from the community.

poor data sharing -- aka naive sharing
these are organizations that provide data of lower quality, accuracy or precision than what is acceptable in the community as a whole. there is a desire to diminish the contribution of these organizations until and unless the data improves.

### Types of ratable data shared
In general, shared data can be divided into three classes:

#### Measurement data: 
data such as logs and features which are either "true" or "false" in terms of what is shared. this data is not generally "weighted" when combined and is instead generally "merged" for combining. as such, this data shared by a poorly rated organization should be not used.

In many cases, this form of data can not be measured for correctness, accuracy or precision in that the source of the data is the measurement itself from the sole observer. Instead, we can evaluate how similar this organization's data aligns with the aggregate data across the community for similar measurements. An example of this may be HTTP log features such as avg response size in bytes.  While there is an expectation that all organizations will occupy a similar range of values, any organization can be a real outlier and as such is not "lying".  If however, this organization is an outlier in the majority of all measurement data they provide, the evidence may suggest their data is excluded from most other organization's uses. It may further suggest that this organization is part of a community that is different than the participant organization if they are truthful.

This comes down to a primary argument of should this data be used by this community moreso than weighting the contribution of the measurements.

#### Metric data:
data such as numerical weights from a model or any other source which is combined via a "weighted combination" that can be reasonably diminished in contribution. this form of data may be combined with a weighting that reflects the quality of the data received.
This is a primary goal for weighted combiners to support weight feedbacks to automatically balance relative contribution based upon qualitative "agreement" with expected outcomes.

The more significant an organization's divergence from "correct" outcomes is, the more drastically their contributions should be curtailed. This is the classic weighting problem and feedback adjustment process used in many domains. There may be multiple approaches used in this space and should be further investigated potentially per metric type to be weighted.


#### Ratings data:
while technically another form of metric data, rating data is directly responsible for affecting the other 2 classes of shared data. This should be treated as the most significantly targeted data types for adveraries to bias outcomes. In general, this form of data should be limited both in sources of sharing, and how freely it is both shared and used.
