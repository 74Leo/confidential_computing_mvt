# Annexe IA MVT Sujet 6 : Confidential Computing / TEE
## LeadDev M1/M2I 2026


---

## 1. Structuration du document et choix de la problématique

### Prompt utilisé

> "Nous travaillons sur un MVT LeadDev sur le Confidential Computing / TEE (Sujet 6). Nos hypothèses initiales portaient sur la performance, la surface d'attaque et la complexité d'intégration. Notre podcast a été réalisé avec Anès Ayad (CEO Net Protect) autour de trois hypothèses différentes : adoption métier vs réglementaire, freins et coûts, fausse confiance si mal implémenté. Comment aligner le document MVT sur les hypothèses du podcast ? Propose une problématique cohérente avec les trois nouvelles hypothèses."

### Extrait utile retenu

Proposition de problématique :

> *"Le Confidential Computing protège-t-il vraiment les données sensibles en production, ou crée-t-il une fausse confiance à un coût d'intégration dissuasif ?"*

### Décision : **retenu avec modification**

Le mot "prohibitif" proposé initialement a été remplacé par "dissuasif".

---

## 2. Reformulation des trois hypothèses

### Prompt utilisé

> "Nos hypothèses v1 portaient sur la performance et la surface d'attaque. Notre podcast couvre : H1 adoption métier vs obligation réglementaire, H2 freins = complexité et coût pas performances, H3 fausse confiance si mal implémenté. Reformule ces trois hypothèses de façon précise, testable et falsifiable pour un MVT académique."

### Extraits utiles retenus

- H1 : *"Les TEE répondent à de vraies contraintes métier, indépendamment des seules obligations réglementaires."*
- H2 : *"Les principaux freins à l'adoption sont la complexité d'intégration et le coût, davantage que les performances."*
- H3 : *"Les enclaves mal implémentées ou non auditées créent une fausse confiance : le périmètre de menace se déplace, il ne disparaît pas."*

### Décision : **retenu avec ajustements mineurs**

Les formulations ont été légèrement retravaillées pour coller au vocabulaire de la transcription du podcast (notamment "périmètre de confiance déplacé" repris d'Anès Ayad).

---

## 3. Rédaction de la section État de l'art

### Prompt utilisé

> "Rédige une section état de l'art académique sur le Confidential Computing et les TEE pour un mémoire LeadDev M1. Couvre : historique des implémentations (SGX, SEV-SNP, TDX, ARM TrustZone), le mécanisme d'attestation à distance, et l'offre cloud actuelle (Azure, GCP, AWS). Style sobre, Times New Roman, pas de mise en forme IA visible. Sources primaires : CCC Whitepaper v1.3, Intel SGX Developer Reference, Misono et al. ACM SIGMETRICS 2024, Feng et al. IET 2024."

### Extraits utiles retenus

- Tableau comparatif des 5 implémentations TEE (SGX v1/v2, SEV-SNP, TDX, ARM TrustZone) avec années et disponibilité cloud.
- Explication du mécanisme d'attestation (génération de quote, hash du code, vérification à distance).
- Section sur l'offre cloud actuelle (Azure Confidential VMs, Google Confidential GKE, AWS Nitro Enclaves).

### Éléments rejetés

- Une description de ARM TrustZone trop longue. Réduite à une ligne dans le tableau.
- Une comparaison SGX vs SEV-SNP vs TDX sur les cas d'usage qui anticipait les résultats de H2 sans les sourcer. Remplacée par le tableau de la section 6.4 basé sur les données Misono et al.

### Décision : **partiellement retenu**

Le fond a été conservé, les formulations ont été relues et corrigées.

---

## 4. Intégration des citations du podcast

### Prompt utilisé

> "Voici la transcription du podcast avec Anès Ayad (CEO Net Protect). Identifie les citations les plus pertinentes pour chacune des trois hypothèses (H1 adoption métier, H2 freins et coûts, H3 fausse confiance). Pour chaque citation, indique à quelle question du guide elle répond et comment elle alimente l'hypothèse correspondante."

### Extraits utiles retenus

Six citations ont été sélectionnées et intégrées dans le document :

| Section | Citation | Hypothèse |
|---|---|---|
| 5.2 | "On n'a pas de réponse réglementaire aujourd'hui. C'est plus au niveau des contraintes métier." | H1 |
| 5.2 | "Avant le TEE, on utilisait une solution qui demandait de faire une ouverture de flux sur un cloud..." | H1 |
| 6.2 | "Il faut distinguer le coût one-shot [...] et le coût récurrent [...]. On peut dire qu'un TEE coûte deux à trois fois plus." | H2 |
| 6.3 | "Mon principal argument pour vendre les TEE à un DSI, c'est le retour sur investissement..." | H2 |
| 7.3 | "C'est juste le périmètre de confiance qui est déplacé. On ne le fait pas disparaître." | H3 |
| 7.4 | "Les risques les plus sous-estimés, ce sont les problèmes liés au CPU [...] et la non-vérification de l'attestation." | H3 |

### Éléments rejetés

- Plusieurs passages de la transcription concernant Windows Hello for Business ont été synthétisés plutôt que cités directement, car la transcription Whisper présentait des erreurs de reconnaissance (noms propres mal retranscrits).
- Un passage sur la gestion des budgets clients (trop spécifique à Net Protect, non généralisable) a été mentionné en contexte mais non cité directement.

### Décision : **retenu après vérification manuelle**

Chaque citation a été vérifiée contre l'enregistrement audio original. Les erreurs de transcription Whisper ont été corrigées manuellement avant intégration.

---

## 5. Rédaction des contre-arguments

### Prompt utilisé

> "Rédige trois contre-arguments sérieux à l'adoption du Confidential Computing, avec pour chacun : l'objection développée en détail, la réponse argumentée, et une condition de falsification explicite (ce qui nous ferait changer d'avis). Les objections doivent être honnêtes, pas des hommes de paille."

### Extraits utiles retenus

Structure des trois contre-arguments (CVE répétés, conformité seul moteur, TLS suffit) et les conditions de falsification associées.

### Éléments rejetés

- Un quatrième contre-argument proposé ("les TEE sont réservés aux grandes entreprises") a été écarté : trop proche de H2 et moins pertinent que les trois retenus.
- Les formulations initiales des conditions de falsification étaient trop vagues ("si de nouvelles vulnérabilités apparaissent"). Reformulées pour être précises.

### Décision : **retenu avec reformulation**

Les objections ont été jugées sérieuses.

---

## 6. Limites identifiées de l'IA sur ce sujet

- **Sources secondaires présentées comme primaires** : l'IA a proposé plusieurs articles de blog (Intel Blog, Google Cloud Blog) comme sources primaires. Remplacés par la documentation officielle et les papers peer-reviewed correspondants.
- **Optimisme sur le déploiement** : les premières rédactions tendaient à minimiser les difficultés d'intégration. Les sections H2 et H3 ont été durcies après écoute du podcast et vérification des benchmarks.

---

## 7. Ce que l'IA n'a pas fait

- Les sources primaires ont toutes été identifiées par le groupe.
- Les résultats et niveaux de confiance du tableau des hypothèses ont été établis par le groupe sur la base du podcast.
- La transcription du podcast a été réalisée via Whisper et vérifiée manuellement.
