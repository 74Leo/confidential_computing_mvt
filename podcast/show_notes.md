# 🔐 Sécuriser les données sensibles avec les Trusted Execution Environments

| | |
|---|---|
| **Invité** | Monsieur Ayad, CEO de Net Protect |
| **Date d'enregistrement** | 15 juin 2026 |
| **Durée** | 18:00 |

---

## 🎯 5 Takeaways clés

### 1. Une adoption guidée par la nécessité métier
Les TEE sont actuellement déployés pour répondre à des contraintes opérationnelles concrètes — finance, santé — plutôt qu'à des obligations réglementaires encore absentes.

### 2. L'autonomie vis-à-vis du cloud
L'utilisation d'enclaves permet une authentification locale sécurisée, évitant les interruptions de service liées aux coupures de flux vers des fournisseurs tiers.

### 3. Un impact matériel et de performance significatif
La technologie exige l'acquisition d'ordinateurs de dernière génération et provoque une perte de puissance CPU générant de la latence sur les postes de travail.

### 4. Une protection ciblée sur l'infrastructure
Les enclaves comme SGX protègent efficacement contre un hyperviseur hostile mais **ne corrigent en aucun cas** les vulnérabilités applicatives ou les bugs du code interne.

### 5. L'importance cruciale de l'attestation
La réussite d'un projet repose sur la vérification systématique des attestations et la mise à jour rigoureuse du TCB pour éviter une fausse sécurité générée par le marketing.

---

## ⏱️ Timestamps

| Temps | Contenu |
|-------|---------|
| `02:00` | Discussion sur la première hypothèse concernant l'adoption des TEE par besoin métier et les cas d'usage en finance |
| `05:46` | Analyse du cas concret Windows Hello et du passage d'une authentification dépendante du cloud à une authentification locale sécurisée |
| `09:30` | Explication technique sur le déplacement du périmètre de confiance et les limites de l'enclave face aux vulnérabilités logicielles |

---

## 🔗 Liens utiles

- 📄 **[Documentation officielle Intel sur SGX](https://www.intel.com/content/www/us/en/architecture-and-technology/software-guard-extensions.html)** — Source primaire
- 📄 **[Guide Microsoft — Windows Hello for Business et les enclaves](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/)** — Source primaire
- ☁️ **[Azure Confidential Computing par Microsoft](https://azure.microsoft.com/en-us/solutions/confidential-computing/)** — Présentation de la solution cloud
- 🤝 **[Confidential Computing Consortium](https://confidentialcomputing.io/)** — Standards et ressources de l'industrie
- 🛡️ **[Base de données CVE — MITRE](https://cve.mitre.org/)** — Suivi des failles et vulnérabilités logicielles

---

## ✅ Validation des hypothèses

### H1 — Adoption motivée par les contraintes métiers
> **CONFIRMÉE** — L'entretien démontre que l'adoption des TEE est motivée par des contraintes métiers réelles, comme la manipulation sécurisée de données de santé ou financières, et non par une réglementation.

### H2 — Complexité et coûts élevés
> **CONFIRMÉE** — Monsieur Ayad valide la complexité et les coûts élevés en précisant qu'un projet TEE est **trois fois plus long** à porter qu'un projet classique et nécessite du matériel coûteux de dernière génération.

### H3 — Risque de fausse confiance
> **CONFIRMÉE** — L'invité souligne que les enclaves créent une fausse confiance si elles sont mal implémentées, rappelant qu'elles protègent contre l'infrastructure mais **pas contre les vulnérabilités internes au code**.