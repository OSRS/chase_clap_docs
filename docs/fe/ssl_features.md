# SSL Features

# Features Framework Existing Features Code
| Category | Feature | Implemented | Type | UVA-Zeek Applicable
| ------   | ------  | ------      | ------ | ------
| Communication | Num_Hosts | T | N | T
| Communication | Num_Conn | T | N | T
| Communication | Avg_Conn | T | N | T
| Communication | Min_Conn | T | N | T
| Communication | Max_Conn | T | N | T
| Domain | Dom_Length | T | N | T
| Domain | Dom_Level | T | N | T
| Domain | Dom_Sub | T | N | T
| Domain | Dom_TLD | T | C | T
| Subject | cnt_subject_O | T | N | T
| Subject | subject_O_freq | T | N | T
| Subject | cnt_subject_C | T | N | T
| Subject | subject_C_freq | T | N | T
| Subject | cnt_subject_L | T | N | T
| Subject | subject_L_freq | T | N | T
| Subject | cnt_subject_ST | T | N | T
| Subject | subject_ST_freq | T | N | T
| Issuer | cnt_issuer_O | T | N | T
| Issuer | issuer_O_freq | T | N | T
| Issuer | cnt_issuer_C | T | N | T
| Issuer | issuer_C_freq | T | N | T
| Version | cnt_version | T | N | T
| Version | version_freq | T | N | T
| Cipher | cnt_cipher | T | N | T
| Cipher | cipher_freq | T | N | T
| Curve | cnt_curve | T | N | T
| Curve | curve_freq | T | N | T

# Feature Notes
Features are applicable to SSL logs based upon existing Zeek fields in UVA/VT datasets. These are not complete and standardized models may shift these features.
