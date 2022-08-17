[[_TOC_]]

# Overview

DARPA CHASE - PCORE - UVA Cyber Stream Processing

General Open Source name "CLAP"
Cyber Log Analytic Processor


CCRi product name "X-CAPE"
Extensible Cyber Analytic Processing Engine

# CLAP System Documentation and Planning

Repo for documentation / planning activities

## Project Members
- Michael Corsello (MC): PI (UVA / OsrsOpen Coordinator)
### Prior Project Members
- Josh Palm (JP): Software Engineer (CCRi)
- Frank Bentrem (FB): Data Scientist (CCRi)


# Documents to Read More

[Accomplishments](accomplishments.md): general listing of accomplishments to date (periodically updated)

[References](references.md): links to relevant content on the interwebs

[Definitions](global_definitions.md): general dictionary for terms we use and our working definitions

[Task Priorities](tasking_priorities.md): racking/stacking of task areas where current efforts are focused (periodically updated)

[Workplan](workplan.md): high-level breakdown of work areas (periodically updated)

## Common Compute Model - CLAP DAG

[Standard DAG Model](StandardDAGModel.md): description of the streaming plaform/framework used in CLAP

[Routing](routing.md): the data routing model used in the standard DAG

[Analytics](analytics.md): how analytics work in the standard DAG model at a high-level

[Global Analysis](global_analysis.md): key concepts around global integration for analytics used in the standard DAG model

## Task Areas
Each task area will focus on a dimension of the total problem of cyber global analysis. The intent is to foster an internal scrutiy of each dimension from the perspective of the other dimensions to ensure a continual "sanity check" of techniques to ensure global analysis is feasible.
In general, more information is available via the content at: /scratch/mc6rt/working_docs/

subdirectories are for Task-Areas:

------
[fe - Feature Engineering](fe/README.md)
------
primary: MC
description:
Focus on data, fields, direct generation and grouping of traffic properties - the local dimension of cyber global analysis.


------
[ar_d - Analytics R&D](ar_d/README.md)
------
primary: FB
description:
Focus on methods to analyse data, automatability of methods, defensibility of analytic approaches - the mathematical dimension of cyber global analysis.

------
[iv - Interactive Visualization](iv/README.md)
------
primary: JP
description:
Focus on people, processes, skillsets and experiences - the human dimension of cyber global analysis.

------
[sf - Sharing Framework](sf/README.md)
------
primary: MC
description:
Focus on data pipelines, infrastructure, standardization, economics, barriers to entry - the hidden dimension of cyber global analysis.