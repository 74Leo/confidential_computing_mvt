# Annexe : Utilisation de l'Intelligence Artificielle

Dans le cadre de ce Mémoire de Veille Technologique, l'IA a été utilisée non pas comme un générateur de contenu final, mais comme un assistant de recherche, un outil d'aide au développement de nos tests, et un "sparring partner" technique. Nous avons systématiquement vérifié les affirmations techniques avec nos sources primaires (ex: documentation du Confidential Computing Consortium).

---

## Cas d'usage 1 : Compréhension approfondie et vulgarisation technique
*   **Prompt utilisé :** "Agis comme un expert en cybersécurité cloud. Je dois expliquer la différence d'architecture entre Intel SGX et AMD SEV-SNP dans mon mémoire. Peux-tu me résumer les différences au niveau de la surface d'attaque, en te basant sur des données techniques réelles ?"
*   **Extrait utile :** L'explication claire sur la différence de granularité (Intel SGX isole au niveau du processus/enclave, tandis qu'AMD SEV-SNP chiffre la VM entière).
*   **Décision (gardé/jeté + pourquoi) :** 
    *   **Gardé :** L'analogie sur la granularité qui nous a aidés à mieux structurer la partie 2.2 de notre état de l'art.
    *   **Jeté :** Les conclusions de l'IA sur la supériorité d'une technologie sur l'autre, car notre but est de rester neutres, factuels et dépendants du cas d'usage (Threat Model).
*   **Limites et risques identifiés :** L'IA a tendance à simplifier à l'extrême les vulnérabilités matérielles. Elle omettait certaines conditions préalables complexes pour exploiter des failles comme Foreshadow ou CacheOut, ce qui a nécessité de vérifier les documentations de CVE manuellement.

---

## Cas d'usage 2 : Aide à la préparation des benchmarks de performance
*   **Prompt utilisé :** "Je dois créer un script Bash pour stresser le CPU et les I/O d'une VM Azure Confidential afin de mesurer l'overhead. Propose-moi une structure de script utilisant `sysbench` pour séparer clairement les deux types de charges."
*   **Extrait utile :** La syntaxe exacte des commandes `sysbench` pour isoler la charge de calcul pur de la charge d'écriture en mémoire.
*   **Décision (gardé/jeté + pourquoi) :**
    *   **Gardé :** La base de la boucle du script Bash et les commandes de test.
    *   **Modifié :** Nous avons dû ajuster manuellement les paramètres de threads et de taille de RAM dans le script pour qu'ils correspondent exactement à la configuration de notre VM de test, car l'IA avait proposé des valeurs génériques inadaptées à notre environnement de démonstration.
*   **Limites et risques identifiés :** Générer du code d'infrastructure via l'IA sans comprendre les métriques mesurées risque de fausser complètement les résultats empiriques du benchmark. Une revue critique ligne par ligne a été obligatoire.

---

## Cas d'usage 3 : Challenger nos propres hypothèses (Sparring Partner)
*   **Prompt utilisé :** "Voici les hypothèses H1, H2 et H3 de notre mémoire sur le Confidential Computing [insertion du texte]. Joue le rôle d'un Lead Dev ou d'un DSI très sceptique et donne-moi 3 contre-arguments techniques solides pour démonter notre hypothèse H3 sur la fausse confiance."
*   **Extrait utile :** L'argument selon lequel la complexité d'intégration (H2) est en réalité la cause directe des mauvaises implémentations qui créent les failles (H3).
*   **Décision (gardé/jeté + pourquoi) :**
    *   **Gardé :** Cet angle de réflexion nous a permis d'étoffer la partie 6 "Contre-arguments" de notre document de synthèse et de mieux préparer notre soutenance orale face aux questions potentielles du jury.
*   **Limites et risques identifiés :** L'IA peut parfois inventer des faux dilemmes d'entreprise ou des problèmes hors sujet. Il a fallu filtrer pour ne garder que les objections techniquement réalistes en production réelle.
