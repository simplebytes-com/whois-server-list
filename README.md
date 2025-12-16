# WHOIS Server List - Complete TLD WHOIS Servers JSON Database

![Last Updated](https://img.shields.io/badge/Last%20Updated-2025--12--16-blue)
![TLDs](https://img.shields.io/badge/TLDs-877+-green)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Auto Sync](https://img.shields.io/badge/Auto%20Sync-2x%20Weekly-orange)

**The most comprehensive, up-to-date JSON list of WHOIS servers for all TLDs** - Automatically synced with [IANA Root Zone Database](https://www.iana.org/domains/root/db).

## 🚀 Quick Access

### Direct JSON URLs (for API/GET requests):

**Primary endpoints** (via whoislist.org):
```
https://whoislist.org/whois_servers.json
https://whoislist.org/data.json
```

*Note: Also available at whois-list.org (alternative domain)*

**GitHub Raw URL** (alternative):
```
https://raw.githubusercontent.com/simplebytes-com/whois-server-list/main/whois_servers.json
```

### Usage:
```bash
# cURL (recommended - custom domain)
curl https://whoislist.org/whois_servers.json

# cURL (alternative endpoint)
curl https://whoislist.org/data.json

# cURL (GitHub raw)
curl https://raw.githubusercontent.com/simplebytes-com/whois-server-list/main/whois_servers.json

# JavaScript/Node.js
const response = await fetch('https://whoislist.org/whois_servers.json');
const whoisServers = await response.json();

# Python
import requests
whois_servers = requests.get('https://whoislist.org/whois_servers.json').json()
```

## 📊 What's Included

- **1,260+ TLD WHOIS Servers** - Covers all major generic and country-code TLDs
- **Auto-Updated** - Syncs with IANA twice weekly (Tuesday & Friday at 2 AM UTC)
- **JSON Format** - Easy to parse and integrate
- **Production Ready** - Used by [DomainDetails.com](https://domaindetails.com?ref=whoislist)

## 📋 Data Format

```json
{
  "com": "whois.verisign-grs.com",
  "net": "whois.verisign-grs.com",
  "org": "whois.pir.org",
  "io": "whois.nic.io",
  "ai": "whois.nic.ai",
  "gg": "whois.gg",
  "jp": "whois.jprs.jp",
  "uk": "whois.nic.uk",
  ...
}
```

**Format**: `{ "tld": "whois.server.hostname" }`

## 🎯 Use Cases

- **Domain Lookup Tools** - Get WHOIS server for any TLD
- **WHOIS Clients** - Route queries to correct servers
- **Domain Monitoring** - Track domain registrations across TLDs
- **DNS Tools** - Integrate WHOIS data into DNS utilities
- **API Development** - Build domain information APIs
- **Research** - Analyze TLD infrastructure

## 🔄 Data Source & Updates

### Official Source
All data is sourced from the **IANA Root Zone Database**:
- TLD List: https://data.iana.org/TLD/tlds-alpha-by-domain.txt
- WHOIS Servers: https://www.iana.org/domains/root/db/{tld}.html

### Update Frequency
- **Automated**: Twice weekly (Tuesday & Friday at 2 AM UTC)
- **Manual**: Can be triggered anytime via GitHub Actions
- **On Changes**: Automatically committed when IANA updates are detected

### Coverage
- ✅ **Generic TLDs**: .com, .net, .org, .io, .ai, etc.
- ✅ **Country-code TLDs**: .uk, .de, .jp, .kr, .fr, etc.
- ✅ **New gTLDs**: .app, .dev, .cloud, .tech, etc.
- ✅ **Internationalized TLDs**: .中国, .рф, .بھارت, etc.
- ⚠️ **Brand TLDs**: Some don't have public WHOIS servers

## 🛠️ Keywords & Search Terms

This repository provides data for:
- WHOIS server list
- TLD WHOIS servers
- WHOIS server database
- Domain WHOIS servers JSON
- IANA WHOIS servers
- ccTLD WHOIS servers
- gTLD WHOIS servers
- WHOIS hostname list
- Top-level domain WHOIS
- WHOIS server directory
- DNS WHOIS servers
- Domain registry WHOIS

## 📖 Related Projects

- [whois-parser](https://github.com/simplebytes-com/whois-parser) - Comprehensive WHOIS data parser
- [DomainDetails.com](https://domaindetails.com?ref=whoislist) - Free domain lookup tool using this data

## 💻 Integration Examples

### Node.js
```javascript
import fetch from 'node-fetch';

async function getWhoisServer(tld) {
  const url = 'https://raw.githubusercontent.com/simplebytes-com/whois-server-list/main/whois_servers.json';
  const servers = await fetch(url).then(r => r.json());
  return servers[tld.toLowerCase()];
}

// Usage
const server = await getWhoisServer('com');
console.log(server); // 'whois.verisign-grs.com'
```

### Python
```python
import requests

def get_whois_server(tld):
    url = 'https://raw.githubusercontent.com/simplebytes-com/whois-server-list/main/whois_servers.json'
    servers = requests.get(url).json()
    return servers.get(tld.lower())

# Usage
server = get_whois_server('com')
print(server)  # 'whois.verisign-grs.com'
```

### PHP
```php
<?php
$url = 'https://raw.githubusercontent.com/simplebytes-com/whois-server-list/main/whois_servers.json';
$servers = json_decode(file_get_contents($url), true);

function getWhoisServer($tld, $servers) {
    return $servers[strtolower($tld)] ?? null;
}

// Usage
$server = getWhoisServer('com', $servers);
echo $server; // 'whois.verisign-grs.com'
?>
```

### Bash/cURL
```bash
#!/bin/bash
TLD="com"
SERVER=$(curl -s https://raw.githubusercontent.com/simplebytes-com/whois-server-list/main/whois_servers.json | \
  jq -r ".[\"$TLD\"]")
echo $SERVER  # 'whois.verisign-grs.com'
```

## 📈 Stats

- **Total TLDs**: 1,260+ (growing)
- **TLDs with WHOIS**: ~88%
- **Update Frequency**: 2x per week
- **Data Freshness**: <3 days
- **Uptime**: 99.9%+ (GitHub reliability)

## 🤝 Contributing

Found an issue or have a suggestion?

1. Check if the TLD exists in IANA: https://www.iana.org/domains/root/db
2. Open an issue with details
3. We'll sync with IANA on next update

**Note**: We don't manually maintain this list. All data comes from IANA's official database.

## 📜 License

MIT License - Free to use in commercial and open-source projects

## 💜 Supported By

This project is made possible by:

- **[DomainDetails.com](https://domaindetails.com?ref=whoislist)** — Project Sponsor & Primary User
- **[GitHub](https://github.com)** — Free hosting, GitHub Actions, and Pages
- **[Cloudflare](https://www.cloudflare.com)** — Global CDN and DDoS protection

## 🌟 Credits

- **Data Source**: [IANA Root Zone Database](https://www.iana.org/)
- **Maintained By**: [Simple Bytes LLC](https://simplebytes.com?ref=whoislist)
- **Built For**: [DomainDetails.com](https://domaindetails.com?ref=whoislist)

---

**Need WHOIS parsing?** Check out our [whois-parser](https://github.com/simplebytes-com/whois-parser) for comprehensive WHOIS data extraction.

**Found this useful?** Give us a ⭐ and help others discover this resource!
