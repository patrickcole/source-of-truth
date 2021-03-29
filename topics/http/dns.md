# DNS

- Domain Name System (lookup)
- Translates domain names (such as google.com) into their appropriate IP (internet protocal) addresses
- Useful as humans cannot remember numeric entries (such as 92.492.282.821) but can remember alphanumeric entries (google.com)
- Any device that is connected to the internet will have an IP address
- each device holds a small storage cache (memory) of commonly visited addresses, this is the local DNS cache; this saves lengthy calls to DNS services on the internet
- if a record is not found inside the local cache, the browser will request an ISP for their DNS services to locate the address record
- if the ISP DNS service does not have a record, it will request the Top Level Domain Service DNS nameserver for the record

-----

## Sources

- [What you need to know about DNS](https://www.freecodecamp.org/news/what-is-dns-anyway/)
