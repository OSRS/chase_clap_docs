# Work Breakdown areas

**OLD FINAL STATUS SEP2021**

feature calc stuff (per log type)
- feature calculation type (ip-like traffic)
  - inter-arrival time
- calculation
  - define fieldsets
  - determine features relative to fieldsets
  - build feature calculation processor
- histocalc (per log type)
  - determine features which can support histograms
  - evaluation range and breakpoints
  - build histocalc processor
- aggregate
  - build feature aggregation
  - build histocalc aggregation

stores stuff
- metricstore
  - sqlite provider updates to allow simulation
  - buffering provider wrapper (full in-memory buffer for current state)
- model store
  - sqlite provider creation for direct storage
  - memory store for direct storage
  - buffering provider wrapper
  - simulation support for sqlite store
- feature store
  - sqlite provider (w/simulation support)

analytics starts
- training/prediction abstractions (DONE)
- prototype analytic
  - build training
  - build predict
  - build model-merge function
  - proof of model IO 
    (lazy read of model state by push trigger ->DispatchData pardigm) 


external data sources (e.g. OSINT)
- whitelists
  - Cisco top 1m (MC)(DONEish)
  - Data store / API (MC)(DONEish)
- blacklists
  - Abuse.ch lists (MC)(DONEish)
  - Data store / API (MC)(DONEish)
- whois mining / scoring
  - RDAP (MC)(DONEish)
  - WhoIs (MC)(IP)
  - Data store / API (MC)(TODO)
- dns mining
  - core client (MC)(IP)
  - dynamic server list (MC)(TODO)
  - Data store / API (MC)(TODO)
- geoip mining
  - MaxMind client (MC)(TODO)
  - WebAPI clients (MC)(TODO)
  - Data store / API (MC)(TODO)
- asn mining
  - MaxMind client (MC)(TODO)
  - WebAPI clients (MC)(TODO)
  - Data store / API (MC)(TODO)
- virustotal mining client
  - core client (MC)(TODO)
  - dynamic apikey list (MC)(TODO)
  - Data store / API (MC)(TODO)
- fireeye mining
  - core file client (JP)(DONEish)
  - file mining (MC)(DONEish)
  - Data store / API (JP)(DONEish)

Labelling
- label generation from OSINT, etc.
  - compute label / update (DONEish)
  - persist to metrics store (DONEish)

- label enrichment hooks (maybe already doneish)

analytic library prep
- aforge updates on model defs
- naive bayes???
- bucketing???
    
********************************************
priority goal
- get data flowing to analytics so Frank can engage + we can get results out.
- need to hit HTTP host (existing from py) + SOMETHING ELSE (e.g. conn logs)
********************************************

cross-organizational sharing support
- HTTPD library to host service endpoints
- implmentation of sharing prototype for store apis
  - metric store provider
  - model store provider


# Task Priorities

| Task Area | Task Name | Priority | Owner | Staffer | Status | Description |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| **FE, AR&D, SF, IV** | - | **1=low, 10=high** | **fb,mc,jp** | **fb,mc,jp** | **obe, to-do, in-prog, done** | - |
| Feature Engineering | DNS Mining | 2 | mc | mc | in-prog | enhance dns mining code to better descriminate field types |
| + | +	| 2 | mc | mc | to-do | enable multi-source lookups for same url/ip |
| + | WHOIS Mining | 2 | mc | mc | in-prog | enhance whois mining code to better descriminate field types |
| + | VirusTotal Mining | 3 | mc | mc | in-prog | enhance virustotal mining code to better populate sub-keys and rankings (evaluate each source) |
| + | MISP Integration | 1 | mc | mc | to-do | build MISP server and mine data (already did static pull of several list sites) |
| + | TAXII Mining | 1 | mc | mc | to-do | build MISP server and mine data (already did static pull of several list sites) |
| + | OTX Mining | 1 | mc | mc | to-do | build MISP server and mine data (already did static pull of several list sites) |
| Analytics R&D | bucket development | 5 | fb | fb | to-do | add mechanism for describing buckets in a sharable fashion such as by GMM |
| + | + | 5 | fb | fb | to-do | apply bucketing analytic to non-HTTP log data |
| + | + | 7 | fb | jp | to-do | apply bucketing analytic to other special data source |
| + | + | 5 | fb | fb | to-do | develop efficacy measurement (TP/FP, TN/FN) |
| + | bucket merging | 5 | fb | fb | to-do | add mechanism for combining multiple sets of buckets (over time or between organizations), such as by GMM or geometric intersecion |
| + | new analytic methods | 6 | fb | fb | to-do | come up with additional analytic methods to use against data |
| + | ensembling methods | 3 | fb | fb | to-do | work on mechanisms for evaluating data and producing applicable metrics/analytics |
| + | reinforcement learning | 3 | fb | fb | to-do | work on mechanisms for evaluating data and producing applicable metrics/analytics |
| + | iterative refinement | 3 | fb | fb | to-do | work on mechanisms for evaluating data and producing applicable metrics/analytics (integrating multiple time steps) |
| + | regression/clustering | 3 | fb | fb | to-do | work on mechanisms for evaluating data and producing applicable metrics/analytics |
| + | HOTL | 5 | fb | jp | to-do | build ability to allow analyst to interactively score data from display |
| + | + | 3 | fb | jp | to-do | store user-driven metrics for known features (e.g. score for fqdn, ip) |
| + | + | 3 | fb | jp | to-do | enable analysts / organizations to rank each other |
| Interactive Visualization | web-app to display data | 5 | jp | jp | to-do | build simple web application to view data interactively (mvp) |
| + | display bucketed data | 5 | jp | jp | to-do | create ability to display bucketed results in web-app via interactive chart |
| Sharing Framework | build pipeline model | 5 | mc | mc | to-do | build python model to enable DAG of data flow for analytics |
| + | + | 5 | mc | mc | to-do | build simple example to demonstrate code for pipelining data |
| + | standardization of data | 5 | mc | mc | to-do | define model for standardization (schemas, metrics, analytics, scores) |
| + | + | 4 | mc | mc | to-do | standard data models for raw-log features |
| + | + | 4 | mc | mc | to-do | standard data models for MADE metrics |
| + | + | 4 | mc | mc | to-do | standard data model for goodness/badness scores |
| + | + | 4 | mc | mc | to-do | standard data model for existing buckets |
| + | + | 4 | mc | mc | to-do | evaluate dns, whois, virustotal for standardizable features |


# Task Areas / Future Work

## DATA ENGINEERING (fe) (josh)
Additional data sources types (e.g. SSL, HTTP, Connections, etc.)
- Feature engineering
    - HTTP
        *updates to existing features TBD
    - CONN
        *updates to existing features TBD
        build master features/fieldsets
    - DNS
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets
    - SSL
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets
    - SSH
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets
    - DHCP
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets
    - SMTP
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets
    - Files
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets
    - Kerberos
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets
    - SIP
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets
    - SysLog
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets
    - X509
        *updates to CONN common features (source/dest ip)
        build master features/fieldsets

Data Sourcing
- Druid
  - Complete Druid reader
    - Test on Sentinel w/HTTP logs
  - Build readers for Sentinel Net log types
    - CONN, DNS, SSL, SSH, ...
  - Build Nebula-specific Druid reader
    - Log Files
        - Build readers for OptTC log types
        - Build readers for Sentinel log typesData Sourcing

## ANALYTIC PROCESSING (ar_d) (frank)
    adding new analytic methods
        feedback learning loop
        learning without labels / sparse labels
        handling missing data / features

    deal with active attack lifecycle and sharing coordinate attack data (real-time)
        show differential emergence of a coordinated attack (e.g. attacking government systems but not commercial systems)
        show differential state of attack (e.g. targeting specific portion of a network or devices - e.g. disable a generator in a facility / stuxnet)
    Histomaps
        HTTP
            *updates to existing features TBD
        CONN
            *updates to existing features TBD
        DNS
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets
        SSL
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets
        SSH
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets
        DHCP
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets
        SMTP
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets
        Files
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets
        Kerberos
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets
        SIP
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets
        SysLog
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets
        X509
            *updates to CONN common features (source/dest ip)
            build master features/fieldsets

## PROCESSING INFRASTRUCTURE (sf / fe / ar_d) (mac)
    Migration to streaming
        Implementation in .NET Standard 2.0 / .NET Core 3.1 (DONE)
    DAG Model
        Data sourcing
            Integrate each new log type / platform
        Enrichment
            Integrate each new feature type
        Label Enrichment
            Integrate labelling for all mappable types (host, sourceip, destip, cert sha1, ...)
        Analytics (Frank TBD)
            Bucketing approach
        Event Processing
            (Frank TBD)
            Graph - edge production
            Correlations (graph-ish)
        Notifications Events (forwarders connections)
        DAG rework / solidification
            Chains by definition (enrich, label enrich, prediction)
        
Simulation Support
    Time sync in multi-log
        Sorted list buffer
    Simulation Sync (same node/multi-node)
        Log time to Sim clock updating
        Simulation aware data stores
        Nexus sim clock sharing
        Simulation external clock sync

## SHARING CAPABILITIES (sf / ar_d / fe) (mac, josh, frank)
    differentiation of "malicious types" (e.g. tagging + taxonomy)
        support for standardizing tagging and having "malicious" shares

    deal with ratings / rankings and combining different types of shared data (e.g. do we use weighting merging on histograms vs. block "untrusted" members)
        merging shared values (many sharing partners + time series)
        incremental rating feedback and refinement
        develop prototype scoring model
            score merging
            merged score "backout"
            tagging / scoring refinement

    ---Stand up "actual" MISP server at UVA (get into communities via DARPA)

## User Inteface (iv) (josh)
HITL/HOTL Support
    Some kind of UI / dashboard
    Event to dashboard
    Analytst Event to Label (thumbs up/down)
    Desktop analytics(ish)
        Bucketing???
        region-drawing
        point selection
        supervised clustering
        graphs, graph-drawing