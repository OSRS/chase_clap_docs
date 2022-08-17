# Analytic Compatibility Matrix

### Fields
| Name | Values | Definition
| ------ | ------ | ------
| Analytic Name | Text | Name of the analytic
| Detect New Threats | (T)rue, (F)alse, (N)/A | Ability to detect new / untrained threats
| Analytic Type | (T)rained, (U)ntrained | Analytic is trained or untrained
| Sharing Type | (M)erging, (N)on-Merging, (L)ocal | Merging supports merging of the shared values, Non-Merging requires combining results post-analysis, local is not shared
| Output Type | (DM) Discrete malicious, (DMB) Discrete malicious/benign, (MS) Maliciousness Scores Single (0-1), (MP) Maliciousness Score Pair (0-1Malicious, 0-1Benign) | What format is the output of the analytic prediction
| Applicability | (G)eneral, (S)pecific | Analytic is applicable to any data types (e.g. HTTP log vs PCAP logs) or only to specific data types
| Missing Feature Support | Boolean | Does the analytic support computation over a different set of features than what is shared. Meaning that the features available are not identical to the features "trained on" from the source.
| Complexity | (L)ow, (M)edium, (H)igh | How computationally expensive is the analytic to compute - (cluster implies M/H) Low is better for barrier to entry
| Exchange | (S)mall, (M)edium, (L)arge | How large is the size of the data exchanged (shared) Small - kb-mb, Medium - mb, Large - 100mb-gb+
| Memory | (L)ow, (M)edium, (H)igh | How memory intensive is the analytic to compute - L - kb-mb, M - mb, H - gb/cluster - lower is better for barrier to entry
| GPU | (N)ot Used, (O)ptional, (R)equired | Is GPU usage supported, optional or required - Not used or optional is better for barrier to entry

### Analytics
| Analytic Name | Detect New Threats | Analytic Type | Sharing Type | Output Type | Applicability | Missing Feature Support | Complexity | Exchange | Memory | GPU
| ------        | ------             | ------        | ------       | ------      | ------        | ------                  | ------     | ------   | ------ | ------
| Decision Tree Bucketing | T | T | N | MS | G | False | M | S | M | N/O
| Histogram+NaiveBayes    | T | T | M | MS | G | True | L | S | L | N
| Logistic Regression     | T | T | N | MS | G | False | M | S | M | N
| Dynamic NB              | T | T | M | MS | G | True | L | S | L | N
| DBSCAN                  | T | T | N | MS | G | False | M | S | M | N