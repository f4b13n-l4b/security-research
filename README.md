# Security Research & Bug Bounty Testing

Tests, essais et recherches en sécurité informatique. Ce dépôt regroupe tous mes explorations, findings et méthodologies de bug bounty.

## 📋 Structure du Projet

```
security-research/
├── docs/                      # Documentation et guides
├── payloads/                  # Payloads et wordlists
├── scripts/                   # Scripts d'automatisation
├── findings/                  # Findings et rapports
├── tools-config/              # Configuration des outils
└── methodology/               # Méthodologie de test
```

## 📂 Répertoires

### `docs/`
- Guides de reconnaissance
- Méthodologie de test
- Documentations techniques
- Notes d'apprentissage

### `payloads/`
- Wordlists (subdomains, paths, etc.)
- Payloads XSS, SQLi, SSRF
- Templates d'exploitation
- Configurations spécifiques

### `scripts/`
- Scripts d'automatisation
- Tools wrapper/helpers
- Scanning scripts
- Utilitaires custom

### `findings/`
- Rapport de tests
- Vulnérabilités découvertes
- Proof of Concepts
- Templates de rapports

### `tools-config/`
- Configuration Burp Suite
- Config Nuclei
- Config autres outils
- Templates personnalisés

### `methodology/`
- Reconnaissance
- Scanning
- Exploitation
- Post-exploitation

## 🔧 Outils Principaux

- **Reconnaissance** : nmap, whois, host, dig
- **Web Testing** : Burp Suite, ZAP, curl
- **Scanning** : Nuclei, Subfinder, Aquatone
- **Fuzzing** : ffuf, wfuzz, gobuster
- **Exploitation** : sqlmap, XSStrike
- **Utilities** : jq, sed, awk, Python

## 📌 Conventions

### Nommage des fichiers
- Dates : `YYYYMMDD_description`
- Domains : `domain.com_findings`
- Templates : `template_[type]_[version]`

### Issues & Milestones
- `type:recon` - Reconnaissance
- `type:scanning` - Scanning & enumeration
- `type:vuln` - Vulnerability testing
- `type:exploit` - Exploitation
- `type:tool` - Tool development
- `status:in-progress` - En cours
- `status:completed` - Terminé

## 🚀 Getting Started

1. **Clone le repo**
   ```bash
   git clone https://github.com/f4b13n-l4b/security-research.git
   cd security-research
   ```

2. **Explore les répertoires**
   - Commence par `methodology/` pour comprendre l'approche
   - Consulte `docs/` pour les guides

3. **Ajoute tes findings**
   - Crée des issues pour tracker les tests
   - Documente tes découvertes dans `findings/`

## 📝 Disclaimer

Ce dépôt est à usage **éducatif et personnel** uniquement. Utilisé uniquement sur les programmes de bug bounty autorisés et dans un cadre légal. Toute utilisation malveillante est interdite.

## 📧 Contact

Pour toute question ou suggestion, ouvre une issue !

---

**Last Updated:** 2026-06-04
