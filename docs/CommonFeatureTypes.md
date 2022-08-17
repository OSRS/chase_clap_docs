CONNDestIpFeature `uuid:`
- TimeRangedEntry, **mandatory**
- dest_ip, **IPAddress** (key field from **ConnLog.NetConnection**)
- dest_ip_total_all, *count of all log entries handled over the interval*, **uint64**
- dest_ip_total_feature, *count of all log entries to this ip over the interval*, **uint64**
- dest_ip_relative_percent, *ratio of dest_ip_total_feature/(unique_source_ips / dest_ip_total_all)*, **f64**
  - eqn: `dest_ip_total_feature/(unique_source_ips / dest_ip_total_all)`

CONNSourceIpFeature `uuid:`
- TimeRangedEntry, **mandatory**
- source_ip, **IPAddress** (key field from **ConnLog.NetConnection**)


CONNDestIpTrafficFeature `uuid:`
- dest_ip_min_conn_dest-bytes-sent, *the minimum number of bytes sent from this destination ip*, **uint64**
- dest_ip_max_conn_dest-bytes-sent, *the maximum number of bytes sent from this destination ip*, **uint64**
- dest_ip_avg_conn_dest-bytes-sent, *the average number of bytes sent from this destination ip*, **f64**
- dest_ip_stdev_conn_dest-bytes-sent, *the standard deviation of the number of bytes sent from this destination ip*, **f64**

- dest_ip_min_conn_dest-pkts-sent, *the minimum number of packets sent from this destination ip*, **uint64**
- dest_ip_max_conn_dest-pkts-sent, *the maximum number of packets sent from this destination ip*, **uint64**
- dest_ip_avg_conn_dest-pkts-sent, *the average number of packets sent from this destination ip*, **f64**
- dest_ip_stdev_conn_dest-pkts-sent, *the standard deviation of the number of packets sent from this destination ip*, **f64**

- dest_ip_min_conn_dest-bytes-sent_conn_dest-pkts-sent_percent, *the minimum ratio of the number of bytes over packets sent from this destination ip*, **uint64**
- dest_ip_max_conn_dest-bytes-sent_conn_dest-pkts-sent_percent, *the maximum ratio of the number of bytes over packets sent from this destination ip*, **uint64**
- dest_ip_avg_conn_dest-bytes-sent_conn_dest-pkts-sent_percent, *the average ratio of the number of bytes over packets sent from this destination ip*, **f64**
- dest_ip_stdev_conn_dest-bytes-sent_conn_dest-pkts-sent_percent, *the standard deviation of the ratio of the number of bytes over packets sent from this destination ip*, **f64**


CONNSourceIpTrafficFeature `uuid:`
- source_ip_min_conn_dest-bytes-sent, *the minimum number of bytes sent from this source ip*, **uint64**
- source_ip_max_conn_dest-bytes-sent, *the maximum number of bytes sent from this source ip*, **uint64**
- source_ip_avg_conn_dest-bytes-sent, *the average number of bytes sent from this source ip*, **f64**
- source_ip_stdev_conn_dest-bytes-sent, *the standard deviation of the number of bytes sent from this source ip*, **f64**

- source_ip_min_conn_dest-pkts-sent, *the minimum number of packets sent from this source ip*, **uint64**
- source_ip_max_conn_dest-pkts-sent, *the maximum number of packets sent from this source ip*, **uint64**
- source_ip_avg_conn_dest-pkts-sent, *the average number of packets sent from this source ip*, **f64**
- source_ip_stdev_conn_dest-pkts-sent, *the standard deviation of the number of packets sent from this source ip*, **f64**

- source_ip_min_conn_dest-bytes-sent_conn_dest-pkts-sent_percent, *the minimum ratio of the number of bytes over packets sent from this source ip*, **uint64**
- source_ip_max_conn_dest-bytes-sent_conn_dest-pkts-sent_percent, *the maximum ratio of the number of bytes over packets sent from this source ip*, **uint64**
- source_ip_avg_conn_dest-bytes-sent_conn_dest-pkts-sent_percent, *the average ratio of the number of bytes over packets sent from this source ip*, **f64**
- source_ip_stdev_conn_dest-bytes-sent_conn_dest-pkts-sent_percent, *the standard deviation of the ratio of the number of bytes over packets sent from this source ip*, **f64**


CONNDestIpStateFeature `uuid:`
- dest_ip_percent_unknown, *Percentage of traffic by destination ip with state "unknown or unreported conn_state"*, **f64**
- dest_ip_percent_s0, *Percentage of traffic by destination ip with state "Connection attempt seen, no reply"*, **f64**
- dest_ip_percent_s1, *Percentage of traffic by destination ip with state "Connection established, not terminated"*, **f64**
- dest_ip_percent_sf, *Percentage of traffic by destination ip with state "Normal establishment and termination"*, **f64**
- dest_ip_percent_rej, *Percentage of traffic by destination ip with state "Connection attempt rejected"*, **f64**
- dest_ip_percent_s2, *Percentage of traffic by destination ip with state "Connection established and close attempt by originator seen (but no reply from responder)"*, **f64**
- dest_ip_percent_s3, *Percentage of traffic by destination ip with state "Connection established and close attempt by responder seen (but no reply from originator)"*, **f64**
- dest_ip_percent_rsto, *Percentage of traffic by destination ip with state "Connection established, originator aborted (sent a RST)"*, **f64**
- dest_ip_percent_rstr, *Percentage of traffic by destination ip with state "Responder sent a RST"*, **f64**
- dest_ip_percent_rstos0, *Percentage of traffic by destination ip with state "Originator sent a SYN followed by a RST, we never saw a SYN-ACK from the responder"*, **f64**
- dest_ip_percent_rstrh, *Percentage of traffic by destination ip with state "Responder sent a SYN ACK followed by a RST, we never saw a SYN from the (purported) originator"*, **f64**
- dest_ip_percent_sh, *Percentage of traffic by destination ip with state "Originator sent a SYN followed by a FIN, we never saw a SYN ACK from the responder (hence the connection was “half” open)"*, **f64**
- dest_ip_percent_shr, *Percentage of traffic by destination ip with state "Responder sent a SYN ACK followed by a FIN, we never saw a SYN from the originator"*, **f64**
- dest_ip_percent_oth, *Percentage of traffic by destination ip with state "No SYN seen, just midstream traffic (one example of this is a “partial connection” that was not later closed)"*, **f64**


CONNSourceIpStateFeature `uuid:`
- source_ip_percent_unknown, *Percentage of traffic by source ip with state "unknown or unreported conn_state"*, **f64**
- source_ip_percent_s0, *Percentage of traffic by source ip with state "Connection attempt seen, no reply"*, **f64**
- source_ip_percent_s1, *Percentage of traffic by source ip with state "Connection established, not terminated"*, **f64**
- source_ip_percent_sf, *Percentage of traffic by source ip with state "Normal establishment and termination"*, **f64**
- source_ip_percent_rej, *Percentage of traffic by source ip with state "Connection attempt rejected"*, **f64**
- source_ip_percent_s2, *Percentage of traffic by source ip with state "Connection established and close attempt by originator seen (but no reply from responder)"*, **f64**
- source_ip_percent_s3, *Percentage of traffic by source ip with state "Connection established and close attempt by responder seen (but no reply from originator)"*, **f64**
- source_ip_percent_rsto, *Percentage of traffic by source ip with state "Connection established, originator aborted (sent a RST)"*, **f64**
- source_ip_percent_rstr, *Percentage of traffic by source ip with state "Responder sent a RST"*, **f64**
- source_ip_percent_rstos0, *Percentage of traffic by source ip with state "Originator sent a SYN followed by a RST, we never saw a SYN-ACK from the responder"*, **f64**
- source_ip_percent_rstrh, *Percentage of traffic by source ip with state "Responder sent a SYN ACK followed by a RST, we never saw a SYN from the (purported) originator"*, **f64**
- source_ip_percent_sh, *Percentage of traffic by source ip with state "Originator sent a SYN followed by a FIN, we never saw a SYN ACK from the responder (hence the connection was “half” open)"*, **f64**
- source_ip_percent_shr, *Percentage of traffic by source ip with state "Responder sent a SYN ACK followed by a FIN, we never saw a SYN from the originator"*, **f64**
- source_ip_percent_oth, *Percentage of traffic by source ip with state "No SYN seen, just midstream traffic (one example of this is a “partial connection” that was not later closed)"*, **f64**


CONNDestIpProtocolFeature `uuid:`
- DestIp_PercentProtocol_icmp, *Percentage of traffic by source ips with the protocol of icmp*, **f64**
- DestIp_PercentProtocol_tcp, *Percentage of traffic by source ips with the protocol of tcp*, **f64**
- DestIp_PercentProtocol_udp, *Percentage of traffic by source ips with the protocol of udp*, **f64**
- DestIp_PercentService_dcerpc, *Percentage of traffic by source ips with the application protocol id of dcerpc*, **f64**
- DestIp_PercentService_dhcp, *Percentage of traffic by source ips with the application protocol id of dhcp*, **f64**
- DestIp_PercentService_dns, *Percentage of traffic by source ips with the application protocol id of dns*, **f64**
- DestIp_PercentService_dtls, *Percentage of traffic by source ips with the application protocol id of dtls*, **f64**
- DestIp_PercentService_ftp, *Percentage of traffic by source ips with the application protocol id of ftp*, **f64**
- DestIp_PercentService_http, *Percentage of traffic by source ips with the application protocol id of http*, **f64**
- DestIp_PercentService_krb, *Percentage of traffic by source ips with the application protocol id of krb*, **f64**
- DestIp_PercentService_ntp, *Percentage of traffic by source ips with the application protocol id of ntp*, **f64**
- DestIp_PercentService_rfb, *Percentage of traffic by source ips with the application protocol id of rfb*, **f64**
- DestIp_PercentService_sip, *Percentage of traffic by source ips with the application protocol id of sip*, **f64**
- DestIp_PercentService_smtp, *Percentage of traffic by source ips with the application protocol id of smtp*, **f64**
- DestIp_PercentService_smtpssl, *Percentage of traffic by source ips with the application protocol id of smtpssl*, **f64**
- DestIp_PercentService_ssh, *Percentage of traffic by source ips with the application protocol id of ssh*, **f64**
- DestIp_PercentNetState_Service_ssl, *Percentage of traffic by source ips with the application protocol id of ssl*, **f64**
- DestIp_PercentNetState_Service_sslsmtp, *Percentage of traffic by source ips with the application protocol id of sslsmtp*, **f64**
- DestIp_PercentNetState_Service_sslsocks, *Percentage of traffic by source ips with the application protocol id of sslsocks*, **f64**
- DestIp_PercentNetState_Service_teredo, *Percentage of traffic by source ips with the application protocol id of teredo*, **f64**


CONNSourceIpProtocolFeature `uuid:`
- SourceIp_PercentProtocol_icmp, *Percentage of traffic by destination ips with the protocol of icmp*, **f64**
- SourceIp_PercentProtocol_tcp, *Percentage of traffic by destination ips with the protocol of tcp*, **f64**
- SourceIp_PercentProtocol_udp, *Percentage of traffic by destination ips with the protocol of udp*, **f64**
- SourceIp_PercentService_dcerpc, *Percentage of traffic by destination ips with the application protocol id of dcerpc*, **f64**
- SourceIp_PercentService_dhcp, *Percentage of traffic by destination ips with the application protocol id of dhcp*, **f64**
- SourceIp_PercentService_dns, *Percentage of traffic by destination ips with the application protocol id of dns*, **f64**
- SourceIp_PercentService_dtls, *Percentage of traffic by destination ips with the application protocol id of dtls*, **f64**
- SourceIp_PercentService_ftp, *Percentage of traffic by destination ips with the application protocol id of ftp*, **f64**
- SourceIp_PercentService_http, *Percentage of traffic by destination ips with the application protocol id of http*, **f64**
- SourceIp_PercentService_krb, *Percentage of traffic by destination ips with the application protocol id of krb*, **f64**
- SourceIp_PercentService_ntp, *Percentage of traffic by destination ips with the application protocol id of ntp*, **f64**
- SourceIp_PercentService_rfb, *Percentage of traffic by destination ips with the application protocol id of rfb*, **f64**
- SourceIp_PercentService_sip, *Percentage of traffic by destination ips with the application protocol id of sip*, **f64**
- SourceIp_PercentService_smtp, *Percentage of traffic by destination ips with the application protocol id of smtp*, **f64**
- SourceIp_PercentService_smtpssl, *Percentage of traffic by destination ips with the application protocol id of smtpssl*, **f64**
- SourceIp_PercentService_ssh, *Percentage of traffic by destination ips with the application protocol id of ssh*, **f64**
- SourceIp_PercentNetState_Service_ssl, *Percentage of traffic by destination ips with the application protocol id of ssl*, **f64**
- SourceIp_PercentNetState_Service_sslsmtp, *Percentage of traffic by destination ips with the application protocol id of sslsmtp*, **f64**
- SourceIp_PercentNetState_Service_sslsocks, *Percentage of traffic by destination ips with the application protocol id of sslsocks*, **f64**
- SourceIp_PercentNetState_Service_teredo, *Percentage of traffic by destination ips with the application protocol id of teredo*, **f64**


HTTPDestIpFeature `uuid:`
- CONNDestIpFeature, **mandatory**

HTTPSourceIpFeature `uuid:`
- CONNSourceIpFeature, **mandatory**

HTTPHostFeature `uuid:`
- TimeRangedEntry, **mandatory**
- Domained, **mandatory** (key field from **HTTPLog.Domained**)
- host_total_all, *the total number of log entries (all hosts included)*, **uint64**
- host_total_feature, *the total number of log entries for this specific host*, **uint64**
- host_relative_percent, *ratio of host_total_feature/(unique_hosts / host_total_all)*, **f64**
  - eqn: `host_total_feature / (unique_hosts / host_total_all)`
- host_response_body_len_percent, *the total number of bytes a host sends over all bytes sent from all hosts*, **f64**
  - eqn: `total_sent_bytes(host) / total_sent_bytes(all_hosts)`
- host_request_body_len_percent, *the total number of bytes a host receives over all bytes sent from all hosts*, **f64**
  - eqn: `total_received_bytes(host) / total_received_bytes(all_hosts)`
- host_method_get_percent, *the total number of get requests a host receives over all get requests from all hosts*, **f64**
  - eqn: `number_get_requests(host) / number_get_requests(all_hosts)`
- host_method_post_percent, *the total number of post requests a host receives over all post requests from all hosts*, **f64**
  - eqn: `number_post_requests(host) / number_post_requests(all_hosts)`
- host_min_source_ip_connection_percent, *for a host, the minimum number of connections with a source ip, normalized by dividing by the average number of connections per source ip for all hosts*, **f64**
  - eqn: `min(host.grpby(source_ips).counts) / (host_total_all / count(uniq(all_hosts.source_ips)))`
- host_max_source_ip_connection_percent, *for a host, the maximum number of connections with a source ip, normalized by dividing by the average number of connections per source ip for all hosts*, **f64**
  - eqn: `max(host.grpby(source_ips).counts) / (host_total_all / count(uniq(all_hosts.source_ips)))`
- host_avg_source_ip_connection_percent, *for a host, the average number of connections with a source ip, normalized by dividing by the average number of connections per source ip for all hosts*, **f64**
  - eqn: `avg(host.grpby(source_ips).counts) / (host_total_all / count(uniq(all_hosts.source_ips)))`
- host_stdev_source_ip_connection_percent, *for a host, the standard deviation of the number of connections with a source ip, normalized by dividing by the average number of connections per source ip for all hosts*, **f64**
  - eqn: `stddev(host.grpby(source_ips).counts) / (host_total_all / count(uniq(all_hosts.source_ips)))`
- host_min_source_ip_request_body_len_response_body_len_ratio, *the minimum ratio of received bytes over sent bytes per source ip*, **f64**
  - eqn: `min(host.grpby(source_ips).received_bytes / host.grpby(source_ips).sent_bytes)`
- host_max_source_ip_request_body_len_response_body_len_ratio, *the maximum ratio of received bytes over sent bytes per source ip*, **f64**
  - eqn: `max(host.grpby(source_ips).received_bytes / host.grpby(source_ips).sent_bytes)`
- host_avg_source_ip_request_body_len_response_body_len_ratio, *the average ratio of received bytes over sent bytes per source ip*, **f64**
  - eqn: `avg(host.grpby(source_ips).received_bytes / host.grpby(source_ips).sent_bytes)`
- host_stddev_source_ip_request_body_len_response_body_len_ratio, *the standard deviation of the ratio of received bytes over sent bytes per source ip*, **f64**
  - eqn: `stddev(host.grpby(source_ips).received_bytes / host.grpby(source_ips).sent_bytes)`
- host_min_source_ip_post_get_ratio, *the minimum ratio of POST requests over GET requests per source ip*, **f64**
  - eqn: `min(host.grpby(source_ips).number_posts / host.grpby(source_ips).number_gets)`
- host_max_source_ip_post_get_ratio, *the maximum ratio of POST requests over GET requests per source ip*, **f64**
  - eqn: `max(host.grpby(source_ips).number_posts / host.grpby(source_ips).number_gets)`
- host_avg_source_ip_post_get_ratio, *the average ratio of POST requests over GET requests per source ip*, **f64**
  - eqn: `avg(host.grpby(source_ips).number_posts / host.grpby(source_ips).number_gets)`
- host_stdev_source_ip_post_get_ratio, *the standard deviation of the ratio of POST requests over GET requests per source ip*, **f64**
  - eqn: `stddev(host.grpby(source_ips).number_posts / host.grpby(source_ips).number_gets)`
- host_status_100_percent, *the percentage of logs with status codes in the 100s over the total number of logs for that host*, **f64**
  - eqn: `host_100_count / host_total_feature`
- host_status_200_percent, *the percentage of logs with status codes in the 200s over the total number of logs for that host*, **f64**
  - eqn: `host_200_count / host_total_feature`
- host_status_300_percent, *the percentage of logs with status codes in the 300s over the total number of logs for that host*, **f64**
  - eqn: `host_300_count / host_total_feature`
- host_status_400_percent, *the percentage of logs with status codes in the 400s over the total number of logs for that host*, **f64**
  - eqn: `host_400_count / host_total_feature`
- host_status_500_percent, *the percentage of logs with status codes in the 500s over the total number of logs for that host*, **f64**
  - eqn: `host_500_count / host_total_feature`
- host_status_fail_percent, *the percentage of logs with failure status codes (400s and 500s) over the total number of logs for that host witin the time interval*, **f64**
  - eqn: `(host_400_count + host_500_count) / host_total_feature`
- host_min_referrer_count, *the minimum of the counts of the referer domains sent to a host, normalized by dividing by the total number of logs sent to the host*, **f64**
  - eqn: `host_min_referrer_count / host_total_feature`
- host_max_referrer_count, *the maximum of the counts of the referer domains sent to a host, normalized by dividing by the total number of logs sent to the host*, **f64**
  - eqn: `host_max_referrer_count / host_total_feature`
- host_avg_referrer_count, *the average of the counts of the referer domains sent to a host, normalized by dividing by the total number of logs sent to the host*, **f64**
  - eqn: `host_avg_referrer_count / host_total_feature`
- host_stdev_referrer_count, *the standard deviation of the counts of the referer domains sent to a host, normalized by dividing by the total number of logs sent to the host*, **f64**
  - eqn: `host_stdev_referrer_count / host_total_feature`
- host_no_referrer_percent, *the percentage of logs that have no referer domain for the host*, **f64**
  - eqn: `host_no_referrer_count / host_total_feature`
- host_num_distinct_urls, *the number of distinct urls for a host*, **uint64**
- host_min_url_len, *the minumum length of the url for a host*, **uint64**
- host_max_url_len, *the maximum length of the url for a host*, **uint64**
- host_avg_url_len, *the average length of the url for a host*, **f64**
- host_stdev_url_len, *the standard deviation of the length of the url for a host*, **f64**
- host_min_url_depth, *the minimum depth of the url for a host*, **uint64**
- host_max_url_depth, *the maximum depth of the url for a host*, **uint64**
- host_avg_url_depth, *the average depth of the url for a host*, **f64**
- host_stdev_url_depth, *the standard deviation of the depth of the url for a host*, **f64**
- host_min_url_params, *the minimum number of parameters of the url for a host*, **uint64**
- host_max_url_params, *the maximum number of parameters of the url for a host*, **uint64**
- host_avg_url_params, *the average number of parameters of the url for a host*, **f64**
- host_stdev_url_params, *the standard deviation of the number of parameters of the url for a host*, **f64**
- host_is_ip, *a boolean for determining whether or not the hostname is an ip address*, **Boolean**
- host_domain_length, *length of the string for the hostname*, **uint64**
- host_number_levels, *the number of levels in the hostname (separated by '.')*,  **uint64**
- host_number_subdomains, *the number of subdomains in the hostname*, **uint64**
- host_tld, *categorical feature for the top level domain of the hostname*, **string**
