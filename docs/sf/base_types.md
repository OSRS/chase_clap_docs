[[_TOC_]]
# Base and Primitive Type Definitions
The model for data types is founded on a few well-defined primitives that are meant to map to types supported across languages and platforms.
These types are grouped into a small set of categories:

> primitives

> simple types

> collections

> structures

## Primitives
the primitive types include:
### Integers
The integers are divided into "signed" and "unsigned", where signed values are defined by ranges that align with twos-complement encoding.

unsigned integers of size K, named "uintK" all have range of 0->(2^K - 1)
> uint8: `R(0, 255)`;  equivalent to value range of BYTE, sub-space of legal integers

> uint16: `R(0, 65535)`; sub-space of legal integers

> uint32: `R(0, 4294967295)`; sub-space of legal integers

> uint64: `R(0, 18446744073709551615)`; sub-space of legal integers

> uint128: `R(0, 2^128 - 1)`; sub-space of legal integers

> uintN: `R(0, ...)`; no limit to byte length, infinite upper bound, sub-space of legal integers

signed integers of size K, named "intK" all have the range of -2^(K-1)->(2^(K-1) - 1)

> int8: `R(-128,127)`; sub-space of legal integers

> int16: `R(-32768, 32767)`; sub-space of legal integers

> int32: `R(-2147483648, 2147483647)`; sub-space of legal integers

> int64: `R(-9223372036854775808, 9223372036854775807)`; sub-space of legal integers

> int128: `R(-2^127, 2^127 - 1)`; sub-space of legal integers

> intN: `R(..., ...)`; no limit to byte length, infinite upper and lower bound,sub-space of legal integers

### Floating Points

> f32: `R(-3.40282347E38, 3.40282347E38)`; (single) generally 8-digits of precision

> f64: `R(-1.7976931348623157E308, 1.7976931348623157E308)`; (double) generally 16-digits of precision

> f128: `R(-1.1897314953572317650857593266280070162E4932, -1.1897314953572317650857593266280070162E4932)`; (quad) generally 34-digits of precision

### Character and Others
> BOOL: `"true" | "false"`

Characters are based upon legal UTF-8, with the standard exchange format being strictly [UTF-8](https://tools.ietf.org/html/rfc3629) unless the format cannot support that encoding.
As such, the rules for a character, which is a single element within a string type conform to the UTF-8 rules.

A UTF-8 string is a sequence of octets representing a sequence of UCS
   characters.  An octet sequence is valid UTF-8 only if it matches the
   following syntax, which is derived from the rules for encoding UTF-8
   and is expressed in the ABNF of [RFC2234](https://tools.ietf.org/html/rfc2234).

> UTF8-octets: `*{ UTF8-char }`

> UTF8-char: `UTF8-1 | UTF8-2 | UTF8-3 | UTF8-4`

> UTF8-1: `%x00-7F`

> UTF8-2: `%xC2-DF UTF8-tail`

> UTF8-3: `%xE0 %xA0-BF UTF8-tail | %xE1-EC 2( UTF8-tail ) | %xED %x80-9F UTF8-tail | %xEE-EF 2( UTF8-tail )`

> UTF8-4: `%xF0 %x90-BF 2( UTF8-tail ) | %xF1-F3 3( UTF8-tail ) | %xF4 %x80-8F 2( UTF8-tail )`

> UTF8-tail: `%x80-BF`

NOTE -- The authoritative definition of UTF-8 is in [UNICODE](https://tools.ietf.org/html/rfc3629#ref-UNICODE).  This grammar is believed to describe the same thing Unicode describes, but does not claim to be authoritative.  Implementors are urged to rely on the authoritative source, rather than on this ABNF.

> CHAR: `UTF8-char`

#### ASCII Table Reference
![ascii table](asciifull.gif)

## Simple Types
Simple types are "extended primitives", generally values that are considered a singular atomic value which is immutable.  Some simple types can be "split" into other types that are "virtual fields".  Example: a date is a simple type represented as an integer value, but it can be split into year, month, day, hour, minute, second relative to the UTC epoch.

> STRING: `NULL | UTF8-octets`; a string is generally implemented as a "reference type" in languages and should have a well-defined binding - (std::string or std::u32string in C++)

> STD-date: `int64`; a standard date is a date-time unix-epoch offset using 0 for the epoch (01/01/1970T00:00:00.0Z) and must be for the UTC zone. This ensures all dates can be converted to other time zones by the recipient and MUST be converted to UTC by the sender for full portability.  
*alias: datetime*

> UUID: `uint128`; a UUID based on [rfc4122](https://tools.ietf.org/html/rfc4122), where the core representation is the 128-bits of data the UUID is made of. This does not specify specific encodings of the UUID, which is instead specific to each encoding, but MUST be handled in every encoding.

### Enumerations
Enumerations are simple types that provide a fixed set of values to be used. Generally, enumerations (enums) are represented dually as an unsigned integer value and a string equivalent. In encodings based on an enum, the integer representation should be presented for exchange.

> NETWORK-DIRECTION: `byte`;
  - 0: `Unknown`
  - 1: `Inbound`
  - 2: `Outbound`
  - 3: `Local`
  - 4: `External`

> VALUE_TYPE: `byte`;
  - 0: `Unknown`
  - 1: `UInt8`
  - 2: `UInt16`
  - 3: `UInt32`
  - 4: `UInt64`
  - 5: `UInt128`
  - 6: `UIntN`
  - 7: `Int8`
  - 8: `Int16`
  - 9: `Int32`
  - 10: `Int64`
  - 11: `Int128`
  - 12: `IntN`
  - 13: `Single`
  - 14: `Double`
  - 15: `Bool`
  - 16: `Char`
  - 17: `UUID`
  - 18: `Uri`
  - 19: `String`
  - 20: `Date`
  - 21: `Set`
  - 22: `Bag`
  - 23: `Dictionary`
  - 24: `Element`

## Collections

> COLLECTION: `{ANY}`; a collection of items, the standard type for exchange or encoding of data.

> SET: `{ANY}`; a collection of items with no duplicates, the standard set type for exchange or encoding of data.

> COLL-BAG: `{ANY}`; no implied ordering, multiple passes may have different orderings - specific sub-type of iterable with implications in language implementations

> COLL-ARRAY: `{ANY}`; implied ordering, accessible by index - specific sub-type of iterable with implications in language implementations  
*alias: array, array<t>, t[]* for typed arrays

**NOTE: _'COLL-' types are mostly for detailed language binding reference, not encodings - several more of these will be defined over time_**

> KEY-NAME: `STRING`

> KVP: `KEY-NAME, ANY`

> DICT: `{KVP}`  
*alias: dictionary<k, v>, dictionary<v>*

## Structures
Structures are building blocks that group other types together into a representation of an entity. Structures are built out using the capability of an implementing language, such as via classes or structs.

The specification of structures here are meant to provide a mechanism for standardization which will enable implementers to have a simple approach to create a compliant language-specific implementation.

### X500 Name (rfc1485)
String representation of an X500 Distinguished Name as used in LDAP and X.509 certificates.

Type is a single string with formatting rules as follows:

> X500Name: `X500Name-Component X500Spaced-Separator | X500Name-Component X500Spaced-Separator X500Name`

> X500Spaced-Separator: `X500Optional-Space X500Separator X500Optional-Space`

> X500Separator: `, | ;`

> X500Optional-Space: `CR | *(' ')`

> X500Name-Component: `X500Attribute | X500Attribute X500Optional-Space + X500Optional-Space X500Name-Component`

> X500Attribute: `X500String | X500Key X500Optional-Space = X500Optional-Space X500String`

> X500Key: `1*X500KeyChar | OID. X500OID`

> X500OID: `X500DigitString | X500DigitString . X500OID`

> X500DigitString: `1*X500Digit`

> X500Digit: `0-9`

> X500String: `*X500StringChar | X500Pair | " *(X500StringChar | X500Special | X500Pair) "`

> X500Special: `, | = | " | CR | + | < | > | # | ;`

> X500Pair: `"`

> X500StringChar: `UTF-8 except X500Special or "`

> X500Hex: 2*X500HexChar

> X500HexChar: `0-9 | a-f | A-F`

X520 Keys:

| Key | Value |
| ---- | ---- |
| CN | CommonName |
| L | LocalityName |
| ST | StateOrProvinceName |
| O | OrganizationName |
| OU | OrganizationalUnitName |
| C | CountryName |

X500Name Examples:

`CN=Marshall T. Rose, O=Dover Beach Consulting, L=Santa Clara, ST=California, C=US`

`CN=FTAM Service, CN=Bells, OU=Computer Science, O=University College London, C=GB`

`CN=Steve Hardcastle-Kille, OU=Computer Science, O=University College London, C=GB`

`CN=Steve Hardcastle-Kille, OU=Computer Science, O=University College London, C=GB`

`CN=Christian Huitema; O=INRIA; C=FR`

`OU=Sales + CN=J. Smith, O=Widget Inc., C=US`

`CN=L. Eagle, O="Sue, Grabbit and Runn", C=GB`