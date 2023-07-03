# ASN TABLE
```
| Number | Bits | Description                                     | Reference       |
|--------|------|-------------------------------------------------|-----------------|
| 0      | 16   | Reserved                                        | RFC 1930, RFC 7607 |
| 1–23455| 16   | Public ASNs                                    |                   |
| 23456  | 16   | Reserved for AS Pool Transition                | RFC 6793        |
| 23457–64495 | 16 | Public ASNs                                 |                   |
| 64496–64511 | 16 | Reserved for use in documentation/sample code | RFC 5398        |
| 64512–65534 | 16 | Reserved for private use                       | RFC 1930, RFC 6996 |
| 65535  | 16   | Reserved                                        | RFC 7300        |
| 65536–65551 | 32 | Reserved for use in documentation/sample code | RFC 4893, RFC 5398 |
| 65552–131071 | 32 | Reserved                                      |                   |
| 131072–4199999999 | 32 | Public 32-bit ASNs                         |                   |
| 4200000000–4294967294 | 32 | Reserved for private use                  | RFC 6996        |
| 4294967295 | 32 | Reserved                                        | RFC 7300        |

```