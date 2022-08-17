# Standardization

Standardization is needed to enable sharing across organizations and across vendor tools.

Attempts at standardization have been growing and getting better over time, such as STIX, TAXII, SIEM tooling, MISP, etc.

What is needed is a more rigid, but yet adaptable standardization model based upon small feature schemas under a loose inheritance model.

example:

an http request is made from the basic components:

>  sourceIP, destIP, host, url, verb

an http request is a superset of the basic tcp components:

>  sourceIP, destIP

so, we can build at least the following specifications:

>  IPv4 = uint8, '.', uint8, '.' uint8, '.' uint8

>  IPv6 = 4{hex}4, ':', 4{hex}4, ':', 4{hex}4, ':', 4{hex}4, ':', 4{hex}4, ':', 4{hex}4, ':', 4{hex}4, ':', 4{hex}4 

>  IP-address = ipv4 | ipv6

>  IP-connection = 'source', IP-address, 'dest', IP-address

>  HTTP-verb-common = 'GET' | 'PUT' | 'POST' | 'DELETE'

>  HTTP-verb = HTTP-verb-common | 'PATCH' | 'HEAD' | 'CONNECT' | 'OPTIONS' | 'TRACE'

>  HTTP-base-request = IP connection, 'host', host, 'verb', HTTP-verb

several of the following items are based directly on the [url](https://www.w3.org/Addressing/URL/uri-spec.html) spec.

>  URL-alpha = 'a' | 'b' | 'c' | 'd' | 'e' | 'f' | 'g' | 'h' | 'i' | 'j' | 'k' | 'l' | 'm' | 'n' | 'o' | 'p' | 'q' | 'r' | 's' | 't' | 'u' | 'v' | 'w' | 'x' | 'y' | 'z' | 'A' | 'B' | 'C' | 'D' | 'E' | 'F' | 'G' | 'H' | 'I' | 'J' | 'K' | 'L' | 'M' | 'N' | 'O' | 'P' | 'Q' | 'R' | 'S' | 'T' | 'U' | 'V' | 'W' | 'X' | 'Y' | 'Z'

>  URL-safe = '$' | '-' | '_' | '@' | '.' | '&'

>  URL-extra = '!' | '*' | '"' | "'" | '(' | ')' | ','

>  URL-escape = '%', hex, hex

>  URL-xalpha = URL-alpha | DIGIT | URL-safe | URL-extra | URL-escape

>  URL-xalphas = URL-xalpha [ URL-xalphas ]

>  URL-xpalpha = URL-xalpha | '+'

>  URL-xpalphas = URL-xpalpha [ URL-xpalpha ]

>  URL-path = NULL | URL-xpalphas [ '/' URL-path ] 

>  HTTP-resource-request = HTTP-base-request, 'url', URL-path

>  URL-search = URL-xalphas [ '+' URL-search ]

>  HTTP-extended-request = HTTP-resource-request, 'query', HTTP-search