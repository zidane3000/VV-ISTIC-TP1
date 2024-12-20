# Practical Session #1: Introduction

1. Find in news sources a general public article reporting the discovery of a software bug. Describe the bug. If possible, say whether the bug is local or global and describe the failure that manifested its presence. Explain the repercussions of the bug for clients/consumers and the company or entity behind the faulty program. Speculate whether, in your opinion, testing the right scenario would have helped to discover the fault.

2. Apache Commons projects are known for the quality of their code and development practices. They use dedicated issue tracking systems to discuss and follow the evolution of bugs and new features. The following link https://issues.apache.org/jira/projects/COLLECTIONS/issues/COLLECTIONS-794?filter=doneissues points to the issues considered as solved for the Apache Commons Collections project. Among those issues find one that corresponds to a bug that has been solved. Classify the bug as local or global. Explain the bug and the solution. Did the contributors of the project add new tests to ensure that the bug is detected if it reappears in the future?

3. Netflix is famous, among other things we love, for the popularization of *Chaos Engineering*, a fault-tolerance verification technique. The company has implemented protocols to test their entire system in production by simulating faults such as a server shutdown. During these experiments they evaluate the system's capabilities of delivering content under different conditions. The technique was described in [a paper](https://arxiv.org/ftp/arxiv/papers/1702/1702.05843.pdf) published in 2016. Read the paper and briefly explain what are the concrete experiments they perform, what are the requirements for these experiments, what are the variables they observe and what are the main results they obtained. Is Netflix the only company performing these experiments? Speculate how these experiments could be carried in other organizations in terms of the kind of experiment that could be performed and the system variables to observe during the experiments.

4. [WebAssembly](https://webassembly.org/) has become the fourth official language supported by web browsers. The language was born from a joint effort of the major players in the Web. Its creators presented their design decisions and the formal specification in [a scientific paper](https://people.mpi-sws.org/~rossberg/papers/Haas,%20Rossberg,%20Schuff,%20Titzer,%20Gohman,%20Wagner,%20Zakai,%20Bastien,%20Holman%20-%20Bringing%20the%20Web%20up%20to%20Speed%20with%20WebAssembly.pdf) published in 2018. The goal of the language is to be a low level, safe and portable compilation target for the Web and other embedding environments. The authors say that it is the first industrial strength language designed with formal semantics from the start. This evidences the feasibility of constructive approaches in this area. Read the paper and explain what are the main advantages of having a formal specification for WebAssembly. In your opinion, does this mean that WebAssembly implementations should not be tested? 

5.  Shortly after the appearance of WebAssembly another paper proposed a mechanized specification of the language using Isabelle. The paper can be consulted here: https://www.cl.cam.ac.uk/~caw77/papers/mechanising-and-verifying-the-webassembly-specification.pdf. This mechanized specification complements the first formalization attempt from the paper. According to the author of this second paper, what are the main advantages of the mechanized specification? Did it help improving the original formal specification of the language? What other artifacts were derived from this mechanized specification? How did the author verify the specification? Does this new specification removes the need for testing?

## Answers

1. **Bug : Problème d'enregistrement de fichiers dans Microsoft Word.** [source](https://www.lemonde.fr/pixels/article/2024/10/08/microsoft-word-decouverte-d-un-bug-qui-supprime-un-document-au-lieu-de-le-sauvegarder_6346684_4408996.html?utm_source=chatgpt.com)

- Certains utilisateurs de Microsoft Word ont rencontré un problème où leurs documents ne pouvaient pas être sauvegardés correctement, entraînant la perte de données. Ce bug était souvent lié à des conflits avec des emplacements réseau ou des paramètres de sauvegarde automatique.
- Manifestation de la panne : Fichiers corrompus ou non enregistrés, entraînant des pertes de travail importantes.
Répercussions :
- Clients/consommateurs : Perte de documents importants, frustrations accrues.
- Entreprise : Impact négatif sur la confiance envers Microsoft et des retours fréquents au support technique.
- Tests possibles : Simuler différents scénarios d'enregistrement, notamment avec des interruptions réseau ou des configurations atypiques, aurait pu aider à identifier ce problème avant sa propagation.

2. **Bug corrigé dans Apache Commons Collections**

Exemple de bug :
*COLLECTIONS-794* : Comportement incorrect de CollectionUtils.retainAll avec des éléments nuls.

Classification du bug : Local (lié à un comportement spécifique de méthode).
Description : La méthode ne gérait pas correctement les éléments nuls, provoquant des résultats erronés.
Solution : Amélioration de la logique de la méthode et ajout de tests unitaires pour vérifier la gestion des valeurs nulles.
Ajout de tests : Oui, des tests de régression ont été ajoutés pour éviter la réapparition du bug.

3. **Chaos Engineering Netflix**

Netflix utilise *Chaos Engineerin*g pour tester la résilience de ses systèmes en simulant des pannes en production. 
Les expériences menées incluent :
- Arrêt de serveurs aléatoires pour évaluer l’impact sur la disponibilité.
- Injection d’erreurs comme des interruptions réseau ou des pannes de disque.
- Tests de surcharge pour analyser le comportement sous forte demande.

Variables observées
- Disponibilité des services.
- Temps de réponse et taux d’erreurs.
- Capacité de récupération après une dégradation progressive.
  
Résultats principaux
- Détection et correction proactive de failles.
- Renforcement de la résilience et de la fiabilité des systèmes.
- Développement d’outils comme Chaos Monkey pour automatiser ces tests.

Netflix et autres entreprises
D’autres organisations comme Amazon et Google adoptent des techniques similaires, adaptées à leurs besoins. Par exemple, une entreprise bancaire pourrait simuler des pannes de bases de données ou des systèmes IoT des interruptions réseau, tout en surveillant continuité de service et performance.

4. **Spécification formelle de WebAssembly**
   
Avantages d’une spécification formelle :
Garantit la correction du design pour un code sécurisé et fiable.
Aide au débogage et à la compréhension grâce à un cadre mathématique clair.
Supprime-t-elle la nécessité de tests ?
Non, les tests restent nécessaires pour valider la conformité des implémentations à la spécification et détecter des problèmes pratiques.

5. **Spécification mécanisée de WebAssembly**

Avantages de la spécification mécanisée (via Isabelle) :
Fournit une spécification exécutable pour validation.
Offre des preuves de correction qui complètent la formalisation manuelle.
Améliorations apportées à la spécification originale :
Oui, elle a corrigé des ambiguïtés et renforcé la formalisation.

Artifacts dérivés :
Preuves vérifiables par machine et interpréteur validé pour WebAssembly.
Processus de vérification :
Les auteurs ont utilisé des preuves automatisées pour vérifier les propriétés de la spécification.

Supprime-t-elle la nécessité de tests ?
Non, les tests restent essentiels pour couvrir des scénarios non inclus dans les preuves formelles.
