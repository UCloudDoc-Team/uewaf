# Glossary

## CNAME Protection Domain

After adding a domain, the CNAME domain that UWAF assigns to customers, with the primary domain being uewaf.com and the subdomain being a random 8 characters.

## Protection IP

The IP that the CNAME protection domain assigned by UWAF to the domain directly resolves to when business back-to-source is not enabled. By default, the same primary domain and its subdomains share one IP.

## Exclusive IP

An exclusive protection IP is assigned to a specific domain. Compared to domains with shared protection IPs, this domain will not be affected when domains with shared protection IPs are under DDoS attack, and it also has better concurrent performance.