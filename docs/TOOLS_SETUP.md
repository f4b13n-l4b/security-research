# Tools Setup Guide

Guide pour configurer l'environnement de test et les outils essentiels.

## 🛠️ Essential Tools

### Network & Reconnaissance
```bash
# Installation sur Ubuntu/Debian
sudo apt-get install nmap dnsutils whois curl wget

# nmap - Port scanning
nmap -sS -p- target.com

# dig - DNS queries
dig target.com ANY

# whois - Domain info
whois target.com
```

### Web Testing
```bash
# Burp Suite Community Edition
# https://portswigger.net/burp/communitydownload

# ZAP - OWASP Zed Attack Proxy
sudo apt-get install zaproxy

# curl - HTTP requests
curl -X GET https://target.com
```

### Subdomain Enumeration
```bash
# Subfinder - Fast subdomain finder
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest

# Amass - In-depth enumeration
go install -v github.com/OWASP/Amass/v3/...@master

# Using crt.sh
curl -s "https://crt.sh/?q=%.target.com&output=json" | jq
```

### Directory/Parameter Fuzzing
```bash
# ffuf - Fast web fuzzer
go install -v github.com/ffuf/ffuf@latest

# gobuster - Directory brute force
go install github.com/OJ/gobuster/v3@latest

# wfuzz - Web application fuzzer
pip3 install wfuzz
```

### Vulnerability Scanning
```bash
# Nuclei - Vulnerability templates
go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest

# Nikto - Web server scanner
sudo apt-get install nikto

# SQLMap - SQL injection testing
sudo apt-get install sqlmap
```

### Utility Tools
```bash
# jq - JSON processor
sudo apt-get install jq

# httpx - HTTP toolkit
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest

# anew - Unique values
go install github.com/tomnomnom/anew@latest

# sort & uniq for data processing
```

## 📋 Complete Setup Script

```bash
#!/bin/bash

echo "[*] Installing system packages..."
sudo apt-get update
sudo apt-get install -y \
    nmap dnsutils whois curl wget jq \
    python3 python3-pip git golang-go

echo "[*] Setting up Go environment..."
export PATH=$PATH:$(go env GOPATH)/bin

echo "[*] Installing Go-based tools..."
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install -v github.com/OWASP/Amass/v3/...@master
go install -v github.com/ffuf/ffuf@latest
go install github.com/OJ/gobuster/v3@latest
go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
go install github.com/tomnomnom/anew@latest

echo "[*] Installing Python tools..."
pip3 install wfuzz sqlmap

echo "[*] Setup complete!"
```

## 🔧 Tool Workflow

### Reconnaissance Phase
```bash
# 1. Subdomains
subfinder -d target.com -o subdomains.txt

# 2. Probe for alive hosts
cat subdomains.txt | httpx -status-code -title -o alive-hosts.txt

# 3. Port scanning on interesting hosts
nmap -sV -p 80,443,8080 target.com
```

### Testing Phase
```bash
# 1. Directory enumeration
ffuf -w wordlist.txt -u https://target.com/FUZZ -o dirs.json

# 2. Parameter discovery
ffuf -w params.txt -u https://target.com/?FUZZ=test

# 3. Vulnerability scanning
nuclei -u https://target.com -t ~/nuclei-templates/
```

### Exploitation Phase
```bash
# 1. SQL Injection
sqlmap -u "https://target.com/page?id=1" --dbs

# 2. XSS Validation
# Manual with Burp Suite or automated with XSStrike

# 3. Custom exploitation
# Scripts in scripts/ directory
```

## 📚 Wordlists & Dictionaries

### Common Locations
```bash
# SecLists
git clone https://github.com/danielmiessler/SecLists.git

# PayloadAllTheThings
git clone https://github.com/swisskyrepo/PayloadsAllTheThings.git

# FuxSocy
git clone https://github.com/Xib1t/FuxSocy.git
```

### Essential Lists
- `subdomains-top1million-5000.txt` - Top subdomains
- `common.txt` - Common paths
- `parameters.txt` - Common parameters
- `api-endpoints.txt` - API endpoints

## 🎯 Quick Tips

1. **Always use `-v` flag** for verbose output
2. **Save outputs** with unique names including date
3. **Test with smaller wordlists first** to validate setup
4. **Use `anew` to deduplicate** results across tests
5. **Document findings immediately** with screenshots

## 📱 Mobile Setup (Burp Suite)

```bash
# Configure proxy
IP: 127.0.0.1
Port: 8080

# Export CA certificate
Burp → Settings → Network → SSL/TLS
Generate CA certificate
```

---

**Dernière mise à jour:** 2026-06-04
