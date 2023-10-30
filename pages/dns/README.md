### [Home](/README.md)

# Comprehensive Guide to DNS (Domain Name System)

## Introduction to DNS

DNS, which stands for Domain Name System, is a critical component of the internet that translates human-readable domain names (e.g., www.example.com) into IP addresses (e.g., 192.0.2.1). This system is essential for navigating the web and accessing various online resources.

![DNS](/assets/dns.png)

### History of DNS

DNS has a rich history dating back to the early days of the internet. It was developed to address the need for a decentralized system to manage domain names and simplify the process of locating resources on the web.

### Working of DNS
The Domain Name System (DNS) is a crucial part of the internet that translates human-readable domain names, such as `www.example.com`, into IP addresses that computers use to locate each other on the network. Here's a simplified overview of how DNS works:

![DNS Wroking](/assets/dnsRecordSequence.png)

1. **User Request**: When you enter a URL (e.g., `www.example.com`) into your web browser, it needs to find the corresponding IP address to connect to the webserver.

2. **Local DNS Cache**: Your device checks its local DNS cache first. This cache stores recently resolved domain names and their corresponding IP addresses. If the URL is found in the cache and hasn't expired, the IP address is retrieved directly.

3. **Recursive DNS Server**: If the IP address isn't in the local cache or has expired, your device sends a request to a recursive DNS server provided by your internet service provider (ISP). This server is responsible for handling DNS requests on your behalf.

4. **Root Name Servers**: The recursive DNS server may not have the IP address either, so it starts by contacting one of the 13 root name servers that exist worldwide. These servers maintain a list of authoritative DNS servers for top-level domains (TLDs) like ".com," ".org," and country codes like ".uk."

5. **TLD DNS Server**: The root name server provides the address of the TLD DNS server responsible for the specific TLD of the requested domain, such as ".com" in the case of "www.example.com."

6. **Authoritative DNS Server**: The TLD DNS server provides the IP address of the authoritative DNS server for the domain "example.com." The authoritative DNS server is the final source of information for that domain.

7. **IP Address Resolution**: Your recursive DNS server contacts the authoritative DNS server for "example.com" to obtain the IP address for "www.example.com."

8. **Response to Client**: The recursive DNS server receives the IP address from the authoritative server and stores it in its cache. It then responds to your device with the IP address.

9. **Accessing the Website**: Your device now uses the obtained IP address to connect to the webserver hosting `www.example.com`, and the webpage is loaded in your browser.

![DNS Lookup](/assets/dnsLookup.png)


### Domain Levels in DNS

#### DNS Hierarchy

The DNS system is organized hierarchically, with each level contributing to the complete domain name. The levels are separated by dots, and they represent various parts of the domain name, from right to left.

![DNS Heirarchy](/assets/dnsHeirarchy.webp)

For example:
- `www.example.com`
  - `com` is the top-level domain (TLD).
  - `example` is the second-level domain.
  - `www` is a subdomain.

#### Top-Level Domain (TLD)

The TLD is the highest level of the DNS hierarchy and typically represents the type or purpose of the domain. Examples include `.com`, `.org`, `.net`, and country-code TLDs like `.uk` for the United Kingdom.

![TLD trust ratings](/assets/tldTrustRatings.png)

### DNS Resolution

DNS resolution is the process of converting a domain name into an IP address, allowing communication with the desired resource. There are two primary types of DNS resolution:

![DNS Resolution](/assets/dnsLookup.png)

#### Query Types

DNS supports various query types, each serving a specific purpose. Common query types include:
- A (IPv4 Address) records.
  ```
  example.com.   IN  A    192.0.2.1
  ```
- AAAA (IPv6 Address) records.
  ```
  example.com.   IN  AAAA    2001:0db8:85a3:0000:0000:8a2e:0370:7334
  ```
- CNAME (Canonical Name) records.
  ```
  www      IN  CNAME   example.com.
  ```
- MX (Mail Exchange) records.
  ```
  example.com.   IN  MX  10  mail.example.com.
  ```
- NS (NameServer) records.
  ```
  example.com.   IN  NS  ns1.example.com.
  ```
- PTR (Reverse DNS Lookup) records.
  ```
  1.2.0.192.in-addr.arpa.   IN  PTR  mail.example.com.
  ```
- SRV (Service) records.
  ```
  _sip._tcp.example.com.  IN  SRV  10  60  5060  sipserver.example.com.
  ```

#### Recursive Resolution

Recursive resolution involves the DNS resolver (usually provided by the internet service provider or a third-party DNS server) making requests to other DNS servers to find the IP address for a given domain name. The resolver queries multiple DNS servers until it finds the authoritative DNS server for the domain.

#### Iterative Resolution

In iterative resolution, the DNS resolver queries DNS servers in a step-by-step manner, starting from the root nameservers and working its way down to find the authoritative DNS server responsible for the domain. This approach places more responsibility on the resolver.

### DNS Nameservers

Nameservers are essential components of the DNS infrastructure. They play a crucial role in managing and resolving domain names.

#### What are Nameservers?

Nameservers are specialized servers that store DNS records and provide responses to DNS queries. They are responsible for mapping domain names to IP addresses.

#### Types of Nameservers

There are several types of nameservers, each serving a distinct role:

![Nameservers](/assets/dnsNameServers.png)

1. ##### DNS Recursive Resolvers

Recursive resolvers are used by client devices to send DNS queries. These servers recursively query other nameservers until they obtain a final answer for the client.

2. ##### Root Nameservers

Root nameservers are the top of the DNS hierarchy. There are 13 sets of root nameservers distributed worldwide. They provide information about top-level domains.

3. ##### TLD Nameservers

Top-level domain nameservers are responsible for TLDs like .com, .org, and .net. They direct queries to authoritative nameservers for second-level domains within their TLD.

4. ##### Authoritative Nameservers

Authoritative nameservers hold DNS records for specific domains. They provide the final answer to DNS queries for those domains.

### DNS Records

DNS records are pieces of information stored in authoritative nameservers. They contain data that maps domain names to IP addresses and other resources.

![DNS Record](/assets/dnsRecord.png)

#### What is a DNS Record?

A DNS record is a structured format that contains various types of information about a domain, such as its IP address, mail server details, or authoritative nameservers.

#### Types of DNS Records

DNS supports various record types, each serving a unique purpose:

1. **SOA (Start of Authority Record):** Specifies authoritative information about a DNS zone, including the primary authoritative nameserver and contact details.
2. **A (IPv4 Record):** Maps a domain name to an IPv4 address.
3. **AAAA (IPv6 Record):** Maps a domain name to an IPv6 address.
4. **CNAME (Alias):** Creates an alias or nickname for a domain, allowing one domain to point to another.
5. **MX (Mail Exchange Record):** Specifies the mail servers responsible for receiving email for a domain.
6. **NS (NameServer Record):** Lists authoritative nameservers for a domain.
7. **PTR (Reverse DNS Lookup):** Resolves an IP address back to a domain name.
8. **SRV (Service Record):** Specifies information about services available within a domain.

```
; Start of Authority (SOA) Record
example.com.   IN  SOA   ns1.example.com. hostmaster.example.com. (
                 2023103001 ; Serial
                 3600       ; Refresh
                 1800       ; Retry
                 604800     ; Expire
                 86400 )    ; Minimum TTL

; A (IPv4 Address) Record
example.com.   IN  A    192.0.2.1

; AAAA (IPv6 Address) Record
ipv6.example.com.   IN  AAAA    2001:0db8:85a3:0000:0000:8a2e:0370:7334

; CNAME (Alias) Record
www      IN  CNAME   example.com.

; MX (Mail Exchange) Record
example.com.   IN  MX  10  mail.example.com.

; NS (NameServer) Record
example.com.   IN  NS  ns1.example.com.

; PTR (Reverse DNS Lookup) Record
1.2.0.192.in-addr.arpa.   IN  PTR  mail.example.com.

; SRV (Service) Record
_sip._tcp.example.com.  IN  SRV  10  60  5060  sipserver.example.com.
```

### DNS Zones

![DNS Zones](/assets/dnsZones.webp)

#### What is a DNS Zone?  
A DNS zone is a contiguous portion of the DNS namespace managed by a specific set of authoritative nameservers. It typically represents a single domain or subdomain.

#### Need for DNS Zones

DNS zones help in managing and organizing DNS records for specific domains. They facilitate efficient administration of DNS data.

#### Zone File

A zone file is a text file that contains DNS records for a specific zone. It provides information about the domain's authoritative nameservers and the associated resource records.

![Zone File](/assets/dnsZoneFile.png)

#### Zone Transfer

Zone transfer is a DNS (Domain Name System) operation that allows a secondary DNS server to copy the DNS records and data from a primary DNS server. Zone transfers are a critical part of maintaining consistency and redundancy in the DNS infrastructure. Here's a simplified overview of zone transfers:

![Zone Transfer](/assets/dnsZoneTransfer.png)

  1. **Primary and Secondary Servers**: In a DNS setup, there are primary (master) and secondary (slave) servers. The primary server is the authoritative source for a DNS zone, while the secondary servers replicate data from the primary server to provide redundancy and improve performance.

  2. **DNS Zone**: A DNS zone is a portion of a domain for which a specific DNS server is responsible. For example, "example.com" is a DNS zone, and it may have one primary DNS server and multiple secondary servers.

  3. **Updating DNS Records**: When DNS records in a zone change on the primary server, the secondary servers need to be updated to reflect these changes.

  4. **Zone Transfer**: Zone transfer is the process of copying the entire DNS zone from the primary server to a secondary server. The secondary server periodically requests updates from the primary server to synchronize its data.

  5. **Incremental Zone Transfer**: Some DNS systems support incremental zone transfers, where only the changed or new DNS records are transferred, reducing the data transfer load.

  6. **DNS NOTIFY**: To initiate a zone transfer, the primary server sends a DNS NOTIFY message to the secondary servers, informing them that changes have occurred in the DNS zone.

  7. **AXFR and IXFR**: There are two primary types of zone transfer: AXFR (full transfer) and IXFR (incremental transfer). AXFR transfers the entire zone, while IXFR transfers only the changes since the last transfer, making it more efficient.

  8. **Redundancy and Load Balancing**: Secondary servers help distribute the load, improve query response times, and ensure DNS service availability in case the primary server experiences issues.


### Authoritative Server

An authoritative server is a DNS server that has the final say on the DNS records for a specific domain. It holds authoritative information and provides responses for queries related to that domain.

### Dynamic DNS (DDNS)

![DDNS Action](/assets/ddnsAction.png)

Dynamic DNS (DDNS) is a service that allows dynamic updates to DNS records. It is commonly used when the IP address of a resource changes frequently, ensuring that the domain name always points to the correct IP address.

![DDNS Home](/assets/ddnsHome.jpg)

### Attacks on DNS

DNS is vulnerable to various attacks that can compromise its integrity and security. Some common attacks include:

![DNS Attacks](/assets/dnsAttacks.webp)

#### DNS Spoofing / Cache Poisoning

DNS spoofing involves manipulating DNS data to redirect users to malicious websites. Cache poisoning attacks exploit vulnerabilities in DNS resolvers to inject incorrect information into the cache.

![DNS Poisoning](/assets/dnsPoisioning.png)

#### DNS Hijacking

DNS hijacking involves redirecting DNS queries to rogue DNS servers controlled by attackers. This allows attackers to control and monitor user traffic.
![DNS Hijacking](/assets/dnsHijacking.webp)

#### DNS Tunnels

DNS tunnels are used to bypass network security measures by encapsulating non-DNS traffic within DNS packets. This method can be exploited for malicious purposes.
![DNS Tunnels](/assets/dnsTunneling.png)
