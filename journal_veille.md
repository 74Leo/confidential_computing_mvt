# Journal de Veille - MVT Confidential Computing

**1. Entrée du 10 avril 2026**
* **Ce que nous avons lu :** Whitepaper "Confidential Computing" v1.3 par le Confidential Computing Consortium (Linux Foundation).
* **Ce que nous avons compris :** Le document définit officiellement les trois états de la donnée (au repos, en transit, et en cours d'utilisation). Nous avons assimilé comment les environnements d'exécution de confiance (TEE) utilisent une isolation matérielle pour protéger spécifiquement la donnée en mémoire, même contre l'administrateur du système ou le fournisseur cloud.
* **Ce que ça change dans notre MVT :** Cela a posé les fondations de notre état de l'art (section 2.1) et nous a permis de définir collectivement le périmètre exact de la technologie pour notre problématique.

**2. Entrée du 18 avril 2026**
* **Ce que nous avons lu :** Documentation officielle "Azure Confidential Computing" (Microsoft Docs).
* **Ce que nous avons compris :** Nous avons découvert comment un fournisseur cloud majeur implémente concrètement les TEE avec des machines virtuelles basées sur AMD SEV-SNP. Nous avons aussi pris connaissance des cas d'usage mis en avant par Azure, notamment dans le domaine médical et le calcul multi-parties.
* **Ce que ça change dans notre MVT :** Le groupe a décidé d'utiliser Azure pour nos propres tests de benchmark (ce qui a motivé notre ADR 001) et cela a servi de base pour formuler notre hypothèse H1 sur l'adoption métier.

**3. Entrée du 26 avril 2026**
* **Ce que nous avons lu :** Documentation officielle du projet Gramine (LibOS pour SGX).
* **Ce que nous avons compris :** Gramine est un "Library OS" conçu pour exécuter des applications non modifiées directement dans des enclaves SGX. Il gère la complexité technique des transitions de mémoire à la place du développeur.
* **Ce que ça change dans notre MVT :** La découverte de cet outil nous a aidés à relativiser la complexité d'intégration (H2). Cela a directement motivé notre décision d'équipe d'utiliser Gramine pour nos propres tests de compatibilité sans avoir à réécrire notre code (ADR 002).

**4. Entrée du 15 mai 2026**
* **Ce que nous avons lu :** Fiche de vulnérabilité sur la faille Foreshadow (CVE-2018-3615) ciblant Intel SGX.
* **Ce que nous avons compris :** Nous avons compris qu'il s'agit d'une attaque de type "side-channel" sur le processeur, qui permettait à un attaquant d'extraire des clés cryptographiques directement depuis une enclave SGX active. 
* **Ce que ça change dans notre MVT :** Même si patchée, cette faille démontre que le matériel lui-même fait partie de la surface d'attaque. Cela a directement nourri notre hypothèse H3 (section 4.3) pour prouver que les TEE déplacent la surface d'attaque mais ne la suppriment pas.

**5. Entrée du 25 mai 2026**
* **Ce que nous avons lu :** Étude scientifique "Benchmarking Confidential Computing on Cloud" par Misono et al. (ACM SIGMETRICS 2024).
* **Ce que nous avons compris :** Cette étude quantifie l'impact des TEE sur les performances. Elle prouve que la perte de performance (overhead) est presque nulle sur des calculs CPU purs, mais grimpe entre 30 % et 50 % sur des opérations nécessitant beaucoup d'entrées/sorties (I/O).
* **Ce que ça change dans notre MVT :** Cette donnée a validé une partie de notre hypothèse H2 et a fondé notre stratégie de test (ADR 004), nous poussant à créer deux scripts distincts (CPU et I/O) pour le benchmark.

**6. Entrée du 2 juin 2026**
* **Ce que nous avons lu :** Interview et préparation du podcast avec Anès Ayad, CEO & Fondateur de Net Protect.
* **Ce que nous avons compris :** Ses retours du terrain nous ont appris que le vrai frein à l'adoption n'est pas la performance, mais la complexité d'intégration (portage, maintenance). Il a souligné que l'erreur la plus fréquente en production est une attestation mal vérifiée.
* **Ce que ça change dans notre MVT :** Son témoignage a validé nos hypothèses H2 et H3, confirmant que le coût de portage est dissuasif et qu'une mauvaise implémentation crée une fausse confiance.

**7. Entrée du 5 juin 2026**
* **Ce que nous avons lu :** Publication sur la vulnérabilité SGAxe (CVE-2020-0551) "How SGX Fails in Practice".
* **Ce que nous avons compris :** Cette faille permettait l'extraction de la clé de signature d'attestation d'Intel, donnant la possibilité de forger des rapports d'attestation valides et forçant le renouvellement des clés.
* **Ce que ça change dans notre MVT :** Cela prouve que le mécanisme d'attestation peut être compromis. Cet argument a été intégré dans notre analyse H3 pour démontrer les risques résiduels en production.

**8. Entrée du 9 juin 2026**
* **Ce que nous avons lu :** Article de recherche sur l'attaque CacheOut (CVE-2020-0549) par Van Schaik et al. (IEEE S&P 2021).
* **Ce que nous avons compris :** Nous avons appris qu'il était possible de lire des données directement depuis le cache du processeur d'une enclave SGX active, en passant par l'OS hôte.
* **Ce que ça change dans notre MVT :** Cela illustre concrètement que la surface d'attaque s'étend aux composants bas niveau du CPU (cache, microcode), complétant notre inventaire des vulnérabilités pour la H3.

**9. Entrée du 16 juin 2026**
* **Ce que nous avons lu :** Documentation du framework open-source Veraison (Confidential Computing Consortium).
* **Ce que nous avons compris :** Veraison documente les architectures d'attestation. Nous avons compris que l'attestation prouve uniquement l'environnement d'exécution, mais ne garantit en rien que le code applicatif embarqué est exempt de failles.
* **Ce que ça change dans notre MVT :** Cette lecture a orienté notre ADR 005 pour aligner notre modèle de vérification sur ce standard ouvert. Cela a aussi renforcé notre recommandation Lead Dev d'imposer des audits d'implémentation.

**10. Entrée du 19 juin 2026**
* **Ce que nous avons lu :** L'étude "Survey on TEE Security" de Feng et al. (IET 2024).
* **Ce que nous avons compris :** Cette revue académique confirme que le coût de portage applicatif reste un frein massif, particulièrement à cause des limitations historiques de mémoire (EPC de 128 Mo sur les premières générations SGX).
* **Ce que ça change dans notre MVT :** Croisée avec le témoignage d'Anès Ayad, cette source académique assoit définitivement la conclusion de notre hypothèse H2 en montrant que la réalité du terrain reflète la littérature scientifique.
