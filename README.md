# dns
DNS (Domain Name System) is the Internet's phonebook. It translates human-friendly domain names (like www.google.com) into machine-friendly IP addresses (like 142.250.77.100), so browsers can load websites.

Without DNS, we’d need to remember IP addresses to access websites.

🏛️ DNS Architecture (High-Level Overview)
DNS follows a distributed and hierarchical architecture with the following key components:

1. Client (DNS Resolver/Stub Resolver)
The device (browser or OS) that initiates the DNS query.

Forwards queries to a Recursive Resolver (usually provided by ISPs or public DNS like Google 8.8.8.8).

2. Recursive DNS Resolver
Acts on behalf of the client.

It queries the root, TLD, and authoritative servers in sequence until it gets the answer.

Caches responses to speed up future lookups.

3. Root Name Servers
Top of the DNS hierarchy (.).

Redirects to the TLD name servers.

There are 13 logical root servers managed globally (e.g., A-root, B-root...).

4. TLD Name Servers (Top-Level Domain)
Store info for domains like .com, .org, .in, etc.

Redirects queries to the correct authoritative name server.

5. Authoritative Name Servers
Contains the actual DNS records (A, AAAA, CNAME, MX, etc.) for a domain.

Final authority to answer queries like "What is the IP of example.com?"

🧱 DNS Query Flow (Example: www.example.com)
pgsql
Copy
Edit
Client → Recursive Resolver → Root Server
       → TLD Server (.com)
       → Authoritative Server (example.com)
       → Returns IP (93.184.216.34)
🧾 Common DNS Record Types
Record Type	Purpose
A	Maps domain to IPv4 address
AAAA	Maps domain to IPv6 address
CNAME	Alias of another domain
MX	Mail server for the domain
NS	Lists authoritative name servers
TXT	Misc data like SPF, DKIM, verification
SOA	Start of Authority (zone details)

🛡️ DNS Concepts to Know
Caching: Reduces load and speeds up resolution.

TTL (Time To Live): How long records are cached.

Zone: A portion of DNS namespace managed by an org.

Forward vs Reverse DNS:

Forward: Domain → IP

Reverse: IP → Domain (uses PTR records)

🔧 Example Use Case in Real Life
You type www.google.com:

Your system checks local DNS cache.

If not found, sends request to 8.8.8.8 (Google DNS).

Google DNS does recursive lookup.

Finds and returns IP 142.250.77.100.

Browser uses this IP to contact Google’s web server.
