# Reconnaissance Methodology

Guide complet pour la phase de reconnaissance passive et active.

## 🔍 Phase Passive

### 1. Domain Enumeration
```bash
# WHOIS Lookup
whois target.com

# DNS Records
dig target.com ANY
nslookup target.com
host target.com

# Subdomains (passive)
curl -s "https://crt.sh/?q=%.target.com&output=json" | jq
```

### 2. IP Intelligence
```bash
# IP ranges
whois 192.168.1.1

# Port scanning (nmap)
nmap -sL 192.168.1.0/24
```

### 3. Web Technologies
- **Wappalyzer** : Détect tech stack
- **BuiltWith** : Tech profiling
- **SecurityTrails** : DNS history
- **Shodan/Censys** : Public data

### 4. Archive & History
- **Wayback Machine** : Archive.org
- **DNSDumpster** : DNS history
- **Google Dorking** : site: inurl: intitle:

## 🎯 Phase Active

### 1. Subdomain Enumeration
```bash
# Subfinder
subfinder -d target.com -o subs.txt

# Amass
amass enum -d target.com -o subs.txt

# Bruteforce
ffuf -w wordlist.txt -u https://FUZZ.target.com -o subs.json
```

### 2. Port Scanning
```bash
# TCP SYN scan
nmap -sS -p- target.com

# Version detection
nmap -sV -p 80,443,8080 target.com

# OS detection
nmap -O target.com
```

### 3. Vulnerability Scanning
```bash
# Nuclei templates
nuclei -u https://target.com -t ~/nuclei-templates/

# OWASP ZAP
zaproxy -cmd -quickurl https://target.com
```

### 4. Web Enumeration
```bash
# Directory bruteforce
gobuster dir -u https://target.com -w wordlist.txt

# Parameter discovery
ffuf -w params.txt -u https://target.com/?FUZZ=test
```

## 📊 Data Organization

| Technique | Tool | Output | Status |
|-----------|------|--------|--------|
| WHOIS | whois | target.com.whois | ⬜ |
| DNS | dig | dns-records.txt | ⬜ |
| Subdomains | subfinder | subdomains.txt | ⬜ |
| Ports | nmap | ports-scan.nmap | ⬜ |
| Tech Stack | wappalyzer | tech-stack.json | ⬜ |

## 🎓 Checklist Reconnaissance

- [ ] WHOIS lookup complète
- [ ] Enumération de tous les subdomains
- [ ] Scan des ports principaux
- [ ] Identification des technologies
- [ ] Recherche d'endpoints publics
- [ ] Analyse des réponses d'erreur
- [ ] Vérification des fichiers publics (robots.txt, sitemap.xml)
- [ ] Recherche DNS history
- [ ] Scan de vulnérabilités connues
- [ ] Analyse des certificats SSL/TLS

## 📚 Ressources

- [OWASP Reconnaissance](https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/01-Information_Gathering/README)
- [HackTricks Recon](https://book.hacktricks.xyz/generic-methodologies-and-resources/pentesting-methodology)
- [IppSec OSCP Course](https://www.youtube.com/c/IppSec)

---

**Mise à jour:** 2026-06-04
