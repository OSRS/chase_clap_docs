# Adding Log Types
Add sourcing for new log types, currently HTTP, CONN are "completish"
feature engineering is "completish" for HTTP, CONN, all others are nascent
- Still need to work on HTTP and CONN features for OSINT sourcing (e.g. WHOIS, DNS, GEOIP, ASNs)
Pin down data sources, currently only supporting Zeek files (json or zeek "csv-ish")

# Nexus Capabilities
Add in-Nexus list reduction... required to keep CLAP footprints smaller and to free up compute on CLAP instances
- Compute all community model rating reductions
- Compute score reductions (CLAP request should return only a single value in general per target)

Add in-Nexus stat monitoring of usage and display of content

Add OSINT mining to NEXUS w/sharing between NEXUS instances
- WHOIS, DNS, GEOIP, ASN passive mining with submission lists/expirations
- Score mining for "virtual nodes" (e.g. community black/white lists)

# CLAP 
More analytics
- Additional HTTP analytics (only real existing analytics at this point)
- CONN log Neural Net(s)
- All other analytics for all other log types (none have been built yet)