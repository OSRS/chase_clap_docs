# FieldSets for Log File Types
In all cases, strings should be preserved with lower-case affinity as comparisons are made with case-sensitive compares.
Most string fields that are directly taken from a sources should preserve case such that processors can determine case handling.
Most string fields that are "set" by the processing pipeline (e.g. a sensor), should maintain lower-case affinity and expect direct case-sensitive comparisons

Sensored `uuid:{C5F513A5-D83D-45BE-8473-CFE59AD62504}`
- sensor_id: *identifier for the sensor itself*, **uuid**

CorrelatedEntry `uuid:{C4EA4051-36C3-4925-91EC-366306EC2D93}`
- key_id: *identity value primary key*, **string**

TimeStampedEntry `uuid:{22AE73D2-C366-40E6-A47B-D4CD85F7336D}`
- ts: *time stamp in UTC*, **DateTime**, **mandatory**

TimeRangedEntry `uuid:{1ABD411B-A20E-421A-AED6-40A62249DD29}`
- start_date: *time stamp in UTC*, **DateTime**, **mandatory**
- end_date: *time stamp in UTC*, **DateTime**, **mandatory**

NetConnection `uuid:{12A571A1-0683-40A2-96C2-8FD642BF3C19}`
- source_ip: *source IP*, **IPAddress**
- source_port: *source Port*, **ushort**
- dest_ip: *destination IP*, **IPAddress**
- dest_port: *destination port*, **ushort**
- net_direction: *traffic direction relative to local network*, (enum) **byte**
  - 0: `Unknown`, direction not known or unset
  - 1: `Inbound`, traffic traversal from outside to inside network
  - 2: `Outbound`, traffic traversal from inside to outside network
  - 3: `Local`, traffic traversal from inside to inside network
  - 4: `External`, traffic traversal from outside to outside network

NetProtocol `uuid:{D086B5A4-2EAA-4CE6-9DCE-FD3E1E10DAAC}`
- conn_proto: *transport layer protocol in use*, **string**
  - examples: `unknown`, `tcp`, `udp`, `icmp`
- conn_service: *application protocol service in use*, **string**
  - examples: `unknown`, `http`, `ftp`

NetTraffic `uuid:{58E2E955-AD5C-4D4B-84EC-892AAC4D0551}`
- conn_source_bytes_sent: *number of payload bytes the originator sent*, **ulong**
- conn_dest_bytes_sent: *number of payload bytes the responder sent*, **ulong**
- conn_source_pkts_sent: *Number of packets that the originator sent*, **ulong**
- conn_dest_pkts_sent: *Number of packets that the responder sent*, **ulong**

NetState `uuid:{E12CD4BC-9D21-46DB-94E3-E5B3853FD8CC}`
- conn_duration: *length of connection in fractional milliseconds*, **double**
- conn_state: *state of the connection*, **string**
  - unknown: *unknown or unreported conn_state*
  - s0: *Connection attempt seen, no reply*
  - s1: *Connection established, not terminated*
  - sf: *Normal establishment and termination*
  - rej: *Connection attempt rejected*
  - s2: *Connection established and close attempt by originator seen (but no reply from responder)*
  - s3: *Connection established and close attempt by responder seen (but no reply from originator)*
  - rsto: *Connection established, originator aborted (sent a RST)*
  - rstr: *Responder sent a RST*
  - rstos0: *Originator sent a SYN followed by a RST, we never saw a SYN-ACK from the responder*
  - rstrh: *Responder sent a SYN ACK followed by a RST, we never saw a SYN from the (purported) originator*
  - sh: *Originator sent a SYN followed by a FIN, we never saw a SYN ACK from the responder (hence the connection was “half” open)*
  - shr: *Responder sent a SYN ACK followed by a FIN, we never saw a SYN from the originator*
  - oth: *No SYN seen, just midstream traffic (one example of this is a “partial connection” that was not later closed)*
- conn_bytes_missed: *number of bytes missed in content gaps*, **ulong**
- conn_parents: **, **ulong**
- conn_hist: *ordered set of characters representing state changes with case indicating direction where orig->dest==upper_case, dest->orig==lower_case (per zeek model)*, **string**
  - s|S: *SYN*
  - h|H: *SYN+ACK*
  - a|A: *ACK*
  - d|D: *packet with data payload*
  - f|F: *FIN*
  - r|R: *RST*
  - c|C: *packet w/bad checksum*
  - g|G: *content gap / dropped packets*
  - t|T: *packet with retransmit*
  - w|W: *packet with ZeroWindow Advertisement*
  - i|I: *inconsistent packet (e.g. FIN+RST)*
  - q|Q: *multi-flag packet (SYN+FIN or SYN+RST) 
  - ^: *direction of orig/dest are backward in log*

Domained `uuid:{587161DA-0857-4389-8C90-D5A80A7FF685}`
- host: *DNS host name*, **string**

HTTPProt `uuid:{286C2128-8E51-4B1F-9FAA-0A94D7C7E8B4}`
- uri: *uri string for request*, **string**
- method: *HTTP verb in request*, **string**
- status: *HTTP status code*, **ushort**
- version: *HTTP version string*, **string**
- status_msg: *status message from server*, **string**

HTTPHead `uuid:{CE190D33-A0E2-49CE-9C4F-7EAB7DFFA387}`
- client_headers: *all headers sent by client in request*, **dictionary[string, Element]**
  - well-known-fields: 
    - Accept: **set[string]**
- server_headers: *all headers sent by server in response*, **dictionary[string, Element]**
  - well-known-fields:
    - Content-Type: **set[string]**

HTTPSize `uuid:{24E7291E-0F44-4A21-9012-36604BCCB535}`
- request_body_len: *uncompressed data size from client*, **uint32**
- response_body_len: *uncompressed data size from server*, **uint32**

HTTPContent `uuid:{2F2C75F0-6DA2-4065-B701-C804F34BED47}`
- request_body *raw bytes of body from client*, **uint8[]**
- response_body *raw bytes of body from server*, **uint8[]**

DNSHead `uuid:`
- dns_id *id of the query generated by the client* **uint16** (rfc1035+)
- opcode *kind of query* **uint8** (nibble) (rfc1035+)
  - 0 **QUERY**
  - 1 **IQUERY** (inverse query)
  - 2 **STATUS**
- aa *authoritative answer* **boolean**
- tc *truncation* **boolean**
- rd *recursion desired* **boolean**
- ra *recursion available* **boolean**
- z *reserved* **boolean**
- rcode *RCODE (response code) for the request*, **uint8** (nibble) (rfc1035+)
  - 0 **NOERROR**
  - 1 **FORMERR**
  - 2 **SERVFAIL**
  - 3 **NXDOMAIN**
- qdcount *number of entries in question* **uint16** (rfc1035+)
- ancount *number of rr in answer* **uint16** (rfc1035+)
- nscount *number of ns rr in ar section* **uint16** (rfc1035+)
- arcount *number of rr in add. rec. section* **uint16** (rfc1035+)

DNSQuestion `uuid:`
- qname *subject of the query* **string**
- qtype *QTYPE of the query* **uint16** (rfc1035+)
  - 1 **A**
  - 2 **NS**
  - 5 **CNAME**
  - 6 **SOA**
  - 12 **PTR**
  - 15 **MX**
  - 16 **TXT**
  - 28 **AAAA**
  - 33 **SRV**
  - 257 **CAA**
  - 35 **NAPTR**
  - See more entries at [RFC](https://tools.ietf.org/html/rfc1035) or [Wikipedia](https://en.wikipedia.org/wiki/List_of_DNS_record_types) or [IANA](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml)
- qclass *QCLASS value for the query* **uint16** (rfc1035+)
  - 1 **INTERNET**
  - 2 **CSNET / Unassigned** (obsolete)
  - 3 **CHAOS**
  - 4 **Hesoid**
  - 254 **NONE**
  - 255 **ANY**
  - See more entries at [RFC](https://tools.ietf.org/html/rfc1035) or [Wikipedia](https://en.wikipedia.org/wiki/List_of_DNS_record_types) or [IANA](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml)

DNSResourceRecord `uuid:`
- name *question value* **string**
- type *RR type code* **uint16**
- class *resource class* **uint16**
- ttl *time to live* **uint32**
- rdata *answer value encoded to a string* **string**
  - NOTE: encodings will vary by above type, string encoding will be TBD at this point, but will be finalized before considering this type finished

DNSResponses `uuid:`
- answers **DNSResourceRecord[]**
- authorities **DNSResourceRecord[]**
- additionals **DNSResourceRecord[]**

DNSQuery `uuid:`
- head **DNSHead**
- questions **DNSQuestion[]**
- responses **DNSResponses**

SSLCryptoInfo `uuid:`
- version *ssl or tls version* **string**
- cipher *formatted cipher string* **string**
- curve *formatted cipher curve if applicable* **string**

SSLKeyInfo `uuid:`
- server_cert_chain
- client_cert_chain

SSLSessionInfo `uuid:`
- session_id *client provided session id* **string**
- resumed *was session new or resumed* **boolean**
- established *was this established or aborted* **boolean**


*X509 TODO -- Work in progress*

X509CertificateChain `uuid:` (rfc5280)
- ???

X509SubjectAlternateName `uuid:` (rfc5280)
- dns *dns name* **string**
- uri *uri name* **string**
- email *email addresses* **EmailAddress[]**
- ip *ip addresses* **IPAddress[]**
- oid *registered object id* **string[]**
- dir_name *distinguished names* **string[]**
- others *other names* **string[]**

X509NameExtensions `uuid:` (rfc5280)
- long_name *long name extension* **string**
- short_name *short name extension* **string**
- oid *oid extension* **string**
- critical *critical extension* **boolean**
- value *value extension* **string**

X509GeneralExtensions `uuid:` (rfc5280)
- key_usage_critical *criticality of usages* **boolean**
- key_usages *usage values for scope* **string[]**
  - digitalSignature
  - nonRepudiation
  - keyEncipherment
  - dataEncipherment
  - keyAgreement
  - keyCertSign
  - cRLSign
  - enciphermentOnly
  - deciphermentOnly
- basic_constraints *set of constraints* **dictionary[string, Element]**
- crl_distro_points *location for CRLs* **string[]**
- subject_key_id *key identifier* **string**
- authority_key_id *key identifier* **string**

X509ExtensionItem `uuid:`
- key_type_name *name of the key type per rfc* **string**
- key_type_value *ASN.1 compatible string encoding of value* **string**

X509CertInfo `uuid:` (rfc5280)
- version *version of the cert* **string**
- sn *serial number* **string**
- sig_alg *algorithm* **string**
- issuer *issuer of the cert* **X500Name**
- not_valid_before *start date* **datetime**
- not_valid_after *end date* **datetime**
- subject *subject of the cert* **X500Name**
- key_alg *algorithm* **string**
- key_type *algorithm* **string**
- key_length *algorithm* **uint32**
- key *public key* **string**
- issuer_uid *identifier of issuer* **string**
- subject_uid *identifier of subject* **string**
- cn *common name* **string**
- exponent *algorithm* **string**
- curve *algorithm* **string**
- thumbprint *cert hash* **string**

X509Certificate `uuid:`
- info **X509CertInfo** **mandatory**
- names **X509NameExtensions**
- subject_alt_name **X509SubjectAlternateName**
- extensions **X509GeneralExtensions**
- additional_fields **X509ExtensionItem[]**
- chain **X509CertificateChain**

------
# EntityTypeIds for Log File Types

HTTPLog `uuid:{F38C1079-0086-4C26-871E-79723CC30C58}`
- TimeStampedEntry, **mandatory**
- NetConnection
- Domained
- HTTPProt
- HTTPHead
- HTTPSize
    
ConnLog `uuid:{1946D6D8-A951-4098-93B3-FA24C5DC14A4}`
- TimeStampedEntry, **mandatory**
- NetConnection
- NetProtocol
- NetTraffic
- NetState

DhcpLog `uuid:{A90CF7AA-1305-4DFE-B446-05655C27E16C}`
- TimeStampedEntry, **mandatory**
- NetConnection

DnsLog `uuid:{EC94F630-EDB5-44DA-B5EB-B3C22BB45DEA}` (per rfc6895)
- TimeStampedEntry, **mandatory**
- NetConnection
- NetProtocol
- DNSQuery

FilesLog `uuid:{12C764B4-3410-4C41-8957-FD3E29A547E6}`
- TimeStampedEntry, **mandatory**

FtpLog `uuid:{B78C1FF7-815C-4280-A202-9E8B89A2106E}`
- TimeStampedEntry, **mandatory**
- NetConnection

KerberosLog `uuid:{17A5BF48-7B32-48FE-B218-E1C986145EB4}`
- TimeStampedEntry, **mandatory**
- NetConnection

SQLLog `uuid:{477BBCB1-7C84-439C-9801-F12841312244}`
- TimeStampedEntry, **mandatory**
- NetConnection

RadiusLog `uuid:{87909581-78A2-46DC-B80A-11E734C4C487}`
- TimeStampedEntry, **mandatory**
- NetConnection

IRCLog `uuid:{7918FACA-A6FF-4CB6-9486-ECE37AD30217}`
- TimeStampedEntry, **mandatory**
- NetConnection

SIPLog `uuid:{057836D9-E6B6-4ED0-B412-453CD0D21A8B}`
- TimeStampedEntry, **mandatory**
- NetConnection

SoftwareLog `uuid:{55211F1F-71B2-4280-BABB-2550BF650893}`
- TimeStampedEntry, **mandatory**

SSHLog `uuid:{05EA9DE1-0395-42C2-BD62-EC8E752EAB4E}`
- TimeStampedEntry, **mandatory**
- NetConnection

SSLLog `uuid:{9D285D6E-47F3-4FB4-B24B-8DDD73755EEE}`
- TimeStampedEntry, **mandatory**
- NetConnection
- Domained

SMTPLog `uuid:{C1F95D52-3930-48A5-A68D-D411D6AC7F2D}`
- TimeStampedEntry, **mandatory**
- NetConnection

SysLog `uuid:{1CBC19EF-FF59-4A18-92B7-8628FCF428A9}`
- TimeStampedEntry, **mandatory**
- NetConnection

NetTunnelLog `uuid:{D9090E4B-0A41-4C4D-8588-14040EDFD235}`
- TimeStampedEntry, **mandatory**
- NetConnection

X509Log `uuid:{A096B3B8-9D16-4247-8856-83F316035269}`
- TimeStampedEntry, **mandatory**
