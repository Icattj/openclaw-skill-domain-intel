---
name: domain-intel
description: Passive domain reconnaissance using Python stdlib only. Subdomain discovery, SSL certificate inspection, WHOIS lookups, DNS records, domain availability checks, and bulk multi-domain analysis. No API keys needed, no dependencies. Use when researching domains, checking competitors, verifying SSL certs, finding subdomains, or checking if a domain is available.
---

# Domain Intelligence — Passive OSINT

Zero dependencies. Zero API keys. Pure Python stdlib.

## Usage

```bash
# Subdomain discovery via Certificate Transparency logs
python3 SKILL_DIR/scripts/domain_intel.py subdomains example.com

# SSL certificate inspection (expiry, cipher, SANs, issuer)
python3 SKILL_DIR/scripts/domain_intel.py ssl example.com

# WHOIS lookup (registrar, dates, name servers — 100+ TLDs)
python3 SKILL_DIR/scripts/domain_intel.py whois example.com

# DNS records (A, AAAA, MX, NS, TXT, CNAME)
python3 SKILL_DIR/scripts/domain_intel.py dns example.com

# Domain availability check (passive: DNS + WHOIS + SSL signals)
python3 SKILL_DIR/scripts/domain_intel.py available coolstartup.io

# Bulk analysis — multiple domains at once
python3 SKILL_DIR/scripts/domain_intel.py bulk example.com github.com google.com
python3 SKILL_DIR/scripts/domain_intel.py bulk example.com github.com --checks ssl,dns
```

All output is structured JSON.

## Commands

| Command | What It Does | Data Source |
|---------|-------------|-------------|
| `subdomains` | Find subdomains | crt.sh Certificate Transparency |
| `ssl` | Inspect SSL cert | Direct TLS connection |
| `whois` | Domain registration | WHOIS protocol (port 43) |
| `dns` | DNS records | System resolver |
| `available` | Check availability | DNS + WHOIS + SSL signals |
| `bulk` | Multi-domain scan | All sources combined |

## Use Cases

- **Competitor research:** Find all subdomains of a competitor (reveals their infrastructure)
- **Security audit:** Check SSL expiry, cipher strength, certificate chain
- **Domain shopping:** Bulk-check if domain names are available
- **Due diligence:** WHOIS lookup on a domain before doing business
- **Infrastructure mapping:** DNS records reveal email providers, CDNs, hosting
