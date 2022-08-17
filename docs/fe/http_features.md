# HTTP Features

# Features Framework Existing Features Code
| Category | Feature | Implemented | Type | UVA-Zeek Applicable
| ------   | ------  | ------      | ------ | ------
| Communication | Num_Hosts | T | N | T
| Communication | Num_Conn | T | N | T
| Communication | Avg_Conn | T | N | T
| Communication | Min_Conn | T | N | T
| Communication | Max_Conn | T | N | T
| Communication | Total_Sent_Bytes | T | N | T
| Communication | Total_Bytes_Recvd | T | N | T
| Communication | Avg_Ratio_RBytes | T | N | T
| Communication | Min_Ratio_RBytes | T | N | T
| Communication | Max_Ratio_RBytes | T | N | T
| Communication | Total_GET | T | N | T
| Communication | Total_POST | T | N | T
| Communication | Avg_Ratio_PG | T | N | T
| Communication | Min_Ratio_PG | T | N | T
| Communication | Max_Ratio_PG | T | N | T
| Domain | Dom_Length | T | N | T
| Domain | Dom_Level | T | N | T
| Domain | Dom_Sub | T | N | T
| Domain | Dom_TLD | T | C | T
| URL | Num_URLs | T | N | T
| URL | Avg_URL_length | T | N | T
| URL | Min_URL_length | T | N | T
| URL | Max_URL_length | T | N | T
| URL | Avg_URL_depth | T | N | T
| URL | Min_URL_depth | T | N | T
| URL | Max_URL_depth | T | N | T
| URL | Num_Params | T | N | T
| URL | Avg_Params | T | N | T
| URL | Min_Params | T | N | T
| URL | Max_Params | T | N | T
| URL | Avg_Vals |  | N | T
| URL | Min_Vals |  | N | T
| URL | Max_Vals |  | N | T
| URL | Frac_URL_filename |  | N | T
| URL | Num_filename | T | N | T
| URL | Num_exts |  | N | T
| URL | Frac_query |  | N | T
| URL | Frac_frag |  | N |
| URL | Num_frag |  | N |
| URL | Frac_bare | T | N | T
| UA | Distinct_UAs | T | N | T
| UA | Ratio_UAs | T | N | T
| UA | Avg_UAs | T | N | T
| UA | Min_UAs | T | N | T
| UA | MaxUAs | T | N | T
| UA | Frac_no_UA | T | N | T
| UA | Frac_UA_1 | T | N | T
| UA | Frac_UA_10 | T | N | T
| UA | UA_Popularity | T | N | T
| UA | Browser | T | C | T
| UA | Avg_Browsers | T | N | T
| UA | OS |  | C | T
| UA | Avg_OS |  | N | T
| Result Code | Frac_200 | T | N | T
| Result Code | Frac_300 | T | N | T
| Result Code | Frac_400 | T | N | T
| Result Code | Frac_500 | T | N | T
| Result Code | Num_200 | T | N | T
| Result Code | Num_300 | T | N | T
| Result Code | Num_400 | T | N | T
| Result Code | Num_500 | T | N | T
| Result Code | Ratio_Fail | T | N | T
| Referer | Frac_no_ref | T | N | T
| Referer | Num_ref_doms | T | N | T
| Referer | Ratio_ref | T | N | T
| Referer | Avg_ref | T | N | T
| Referer | Min_ref | T | N | F
| Referer | Max_ref | T | N | T
| Referer | Has_Referer | T | B | T
| Content-Type | Distinct_ct | T | N | T
| Content-Type | Frac_ct_empty | T | N | T
| Content-Type | Frac_ct_js | T | N | T
| Content-Type | Frac_ct_image | T | N | T
| Content-Type | Frac_ct_text | T | N | T
| Content-Type | Frac_ct_video | T | N | T
| Content-Type | Frac_ct_app | T | N | T
| Content-Type | Frac_ct_html | T | N | T
| Content-Type | Frac_ct_sh | T | N | T
| Content-Type | Frac_ct_exe | T | N | T
| Content-Type | Frac_ct_jar | T | N | T
| WHOIS | Reg_Age | T | N | T
| WHOIS | Update_Age | T | N | T
| WHOIS | Reg_Validity | F | N | T
| WHOIS | Update_Validity | F | N | T
| WHOIS | Reg_Email | F | C | T
| WHOIS | Time_Til_Expire | T | N | T
| WHOIS | cnt_registrar | T | N | T
| WHOIS | registrar_freq | T | N | T
| WHOIS | cnt_status | T | N | T
| WHOIS | status_freq | T | N | T
| Hosting Type | Free_Host | F | B | T
| Hosting Type | Dynamic_DNS | F | B | T
| Hosting Type | URL_Shortner | F | B | T
| Geolocation | Set_ASNs | F | C | T
| Geolocation | Num_ASNs | F | N | T
| Geolocation | Set_Countries | F | C | T
| Geolocation | Num_Countries | F | N | T


# Feature Notes
Features are applicable to HTTP logs based upon existing Zeek fields in UVA/VT datasets. These are not complete and standardized models may shift these features.

These features are generally most applicable to OUTBOUND traffic to detect C2 traffic, but also have some applicability to INBOUND traffic to detect scanning/probing/attack behaviors such as SQL Injection, etc.
