# DnsRecon
## Summary

dnsrecon - A powerful DNS enumeration sript

| =============== | =============== |  
| :------------ |:---------------:| 
| Author        | Carlos Perez |
| Source        | true        |
| Homepage      | https://github.com/darkoperator/dnsrecon     |   
| Kalirepo      | http://git.kali.org/gitweb/?p=packages/dnsrecon.git;a=summary       | 


## Description

**DNSRecon provides the ability to perform:**

* Check all NS Records for Zone Transfers
* Enumerate General DNS Records for a given Domain (MX, SOA, NS, A, AAAA, SPF and TXT)
* Perform common SRV Record Enumeration. Top Level Domain (TLD) Expansion
* Check for Wildcard Resolution
* Brute Force subdomain and host A and AAAA records given a domain and a wordlist
* Perform a PTR Record lookup for a given IP Range or CIDR
* Check a DNS Server Cached records for A, AAAA and CNAME Records provided a list of host records in a text file to check
* Enumerate Common mDNS records in the Local Network Enumerate Hosts and Subdomains using Google

## Projcet info
```
# dnsrecon -h
Version: 0.8.7
Usage: dnsrecon.py <options>

Options:
   -h, --help                  Show this help message and exit
   -d, --domain      <domain>  Domain to Target for enumeration.
   -r, --range       <range>   IP Range for reverse look-up brute force in formats (first-last)
                               or in (range/bitmask).
   -n, --name_server <name>    Domain server to use, if none is given the SOA of the
                               target will be used
   -D, --dictionary  <file>    Dictionary file of sub-domain and hostnames to use for
                               brute force.
   -f                          Filter out of Brute Force Domain lookup records that resolve to
                               the wildcard defined IP Address when saving records.
   -t, --type        <types>   Specify the type of enumeration to perform:
                               std      To Enumerate general record types, enumerates.
                                        SOA, NS, A, AAAA, MX and SRV if AXRF on the
                                        NS Servers fail.

                               rvl      To Reverse Look Up a given CIDR IP range.

                               brt      To Brute force Domains and Hosts using a given
                                        dictionary.

                               srv      To Enumerate common SRV Records for a given

                                        domain.

                               axfr     Test all NS Servers in a domain for misconfigured
                                        zone transfers.

                               goo      Perform Google search for sub-domains and hosts.

                               snoop    To Perform a Cache Snooping against all NS
                                        servers for a given domain, testing all with
                                        file containing the domains, file given with -D
                                        option.

                               tld      Will remove the TLD of given domain and test against
                                        all TLD's registered in IANA

                               zonewalk Will perform a DNSSEC Zone Walk using NSEC Records.

   -a                          Perform AXFR with the standard enumeration.
   -s                          Perform Reverse Look-up of ipv4 ranges in the SPF Record of the
                               targeted domain with the standard enumeration.
   -g                          Perform Google enumeration with the standard enumeration.
   -w                          Do deep whois record analysis and reverse look-up of IP
                               ranges found thru whois when doing standard query.
   -z                          Performs a DNSSEC Zone Walk with the standard enumeration.
   --threads          <number> Number of threads to use in Range Reverse Look-up, Forward
                               Look-up Brute force and SRV Record Enumeration
   --lifetime         <number> Time to wait for a server to response to a query.
   --db               <file>   SQLite 3 file to save found records.
   --xml              <file>   XML File to save found records.
   --iw                        Continua bruteforcing a domain even if a wildcard record resolution is discovered.
   -c, --csv          <file>   Comma separated value file.
   -v                          Show attempts in the bruteforce modes.
```

## Usage
```
# dnsrecon -d example.com -D /usr/share/wordlists/dnsmap.txt -t std --xml dnsrecon.xml
```
