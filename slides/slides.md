<style>
.reveal section[data-background-image] h1:not(:empty) {
  background: rgba(0, 0, 0, 0.6);
  padding: 20px 40px;
  border-radius: 10px;
  display: inline-block;
  color: AliceBlue;
}
</style>

# C'est quoi une bonne PR ?

-v-

## Présentation

Julien Lenormand

<img src="./julien_lenormand_logo.png" alt="" width="786" style="margin-top: 200px" />

---

# Une pull request ?

* aussi appellé "merge request"  <!-- .element: class="fragment" -->
* jeu à 2 joueurs pour merger du code  <!-- .element: class="fragment" -->
* ma vision  <!-- .element: class="fragment" -->

-v-

## L'ampleur du problème

* TODO anecdotes  <!-- .element: class="fragment" -->
* TODO stats  <!-- .element: class="fragment" -->

---

## Comment ouvrir une bonne PR ? (côté reviewé)

Les 4 **C**

* **Courte**  <!-- .element: class="fragment" -->
  * (si possible)  <!-- .element: class="fragment" -->
  * trunk-based ?  <!-- .element: class="fragment" -->
  * focus  <!-- .element: class="fragment" -->

-v-

* **Claire**
  * description de PR  <!-- .element: class="fragment" -->
    * résumé  <!-- .element: class="fragment" -->
    * instructions de setup/test/repro  <!-- .element: class="fragment" -->
    * images  <!-- .element: class="fragment" -->
  * nom de branche  <!-- .element: class="fragment" -->
  * messages de commit  <!-- .element: class="fragment" -->
    * conventional commit  <!-- .element: class="fragment" -->
  * rebase (interactif)  <!-- .element: class="fragment" -->
    * philosophies divergentes  <!-- .element: class="fragment" -->
  * auto-relecture  <!-- .element: class="fragment" -->
    * (aidé par l'IA)  <!-- .element: class="fragment" -->
  * "make the change easy, then make the easy change"  <!-- .element: class="fragment" -->
  * “Programs must be written for people to read, and only incidentally for machines to execute.” - SICP  <!-- .element: class="fragment" -->

-v-

* **Contextualisée**
  * lien vers le ticket, la doc, les ADRs, ...  <!-- .element: class="fragment" -->
  * commentaires d'auto-relecture  <!-- .element: class="fragment" -->
  * smart commit / issue linking  <!-- .element: class="fragment" -->

-v-

* **Complète**
  * inclut les tests (auto-validée)  <!-- .element: class="fragment" -->
  * la doc, l'infra ...  <!-- .element: class="fragment" -->
  * CI verte (formatter, linter, tests, security checks, ...)  <!-- .element: class="fragment" -->
  * cf Definition of Done/Ready  <!-- .element: class="fragment" -->

-v-

En bonus :

* pas d'AI slop  <!-- .element: class="fragment" -->

---

## Comment bien relire une PR ? (côté reviewer)

Une relecture n'est pas juste une "lecture".

* prendre du recul sur la manière dont la solution répond au besoin  <!-- .element: class="fragment" -->
* voir ce qu'il manque, pas juste ce qui est présent  <!-- .element: class="fragment" -->
  * évaluer tous les angles (ISO/IEC 25002:2024)  <!-- .element: class="fragment" -->
  * maintenabilité  <!-- .element: class="fragment" -->
  * voir ce qu'il y a en trop (merci les IAs)  <!-- .element: class="fragment" -->
* discuter collectivement  <!-- .element: class="fragment" -->
  * conventions  <!-- .element: class="fragment" -->
  * dette technique  <!-- .element: class="fragment" -->

Notes:
* maintenabilité
* testabilité
* sécurité
* performance
* adéquation fonctionnelle (suitability)
* compatibilité
* fiabilité
* cohérence

-v-

* apprendre le projet
  * no hierarchy  <!-- .element: class="fragment" -->
  * tout le monde peut apprendre  <!-- .element: class="fragment" -->
  * "ask dumb questions"  <!-- .element: class="fragment" -->
  * rester informé des évolutions  <!-- .element: class="fragment" -->
* déléguer c'est accepter que ce soit fait différemment  <!-- .element: class="fragment" -->
* conventional comment  <!-- .element: class="fragment" -->
  * actionnable feedback  <!-- .element: class="fragment" -->
  * clarté de l'attendu  <!-- .element: class="fragment" -->

-v-

* choisir ses batailles
  * disagree and commit  <!-- .element: class="fragment" -->
  * "je peux vivre avec"  <!-- .element: class="fragment" -->
  * "good enough"  <!-- .element: class="fragment" -->
  * LGTM si c'est pertinent  <!-- .element: class="fragment" -->
  * un-pedantic  <!-- .element: class="fragment" -->
* "On est gentils avec les humains, mais impitoyables avec le code" - le Permacodeur  <!-- .element: class="fragment" -->


---

## Et si on dézoome ?

* garde-fou pour éviter de balancer de la daube aux QAs
  * voire directement en prod
* effet Hawtorne : savoir qu'il y aura une relecture, on s'applique +
* Management de la connaissance et de la responsabilité
  * co-ownership : transfert du code d'une personne au groupe
* dérives
  * Rubber-stamping : LGTM + Approve sans relire (*Goal displacement*)
    * liability laundering / compliance theater
  * Pointillisme
* prise de recul
  * question avant : bonne chose à faire ?
  * question après : bonne chose faite ? chose bien faite ?

-v-

* vision LEAN:
  * la pull request est le livrable d'une des étapes de la production logicielle
  * la review, puis la validation de la pull request, sont les suivantes
  * chaque commentaire de review, et de surcroit changement à faire, est un défaut, et devrait cherché à être éliminé
  * autrement dit :
    > une PR avec + que 3 commentaires est un échec de process
  * des problèmes à régler en amont :
    * problèmes de design
    * conventions non suivies
    * absence de definition of ready/done
    * CI et tooling insuffisants
    * critères d'acceptance flous
    * manque de confiance

-v-

* améliorer la DX de la pull request :
  * temps d'attente + délai de livraison (cf DORA)
  * goulot d'étranglement (cf Kanban)
  * context switch forcé
  * outillage et process

* à problème socio-technique, solution pas que technique
  * "don't blame the player, blame the game"
  * everybody's problem

---

## Sources

* Mon court talk sur l'acte de code review lui-même : https://lenormju.github.io/talk-code-review/index.html
* TODO

---

## Bonus : autres conseils pour les PR

* code review full sync : on la fait ensemble côte-à-côte
* code review full async : chacun travaille quand il veut/peut dans sa timezone et selon ses disponibilités
* hybride : la review est surtout async, mais la discussion se fait sync
* ship/show/ask : selon la nature de la PR, soit on merge sans review, soit mon montre pour merger, soit on demande du feedback
  * 3 tiers : confiance, feedback et douane/bureaucratie ("red tape")
  * comment savoir ? nombre de lignes modifiées, complexité cyclomatique des lignes modifiées ou du fichier modifié, ajout de commentaires pour faire taire le linter, refactoring sans couverture de tests, etc.
* pas de code review : confiance mutuelle
* code review après le merge (non-bloquante)
* pair-prog : code relu pendant son écriture, pas besoin avant de merge
* pair-conception, pair-testing, ... en amont

-v-

* code review pendant le WIP
* bots (IA) de code review
* CI-centric : du moment que la CI passe, on peut merger
* Coding guide + Contributing (exemple : https://rfc.zeromq.org/spec/42/)
* tooling : stacked PRs, Git-compatible local alternatives (jujutsu, Sapling, ...)
* Google readability review (https://abseil.io/resources/swe-book/html/ch03.html#readability_standardized_mentorship_thr) vs code review (https://abseil.io/resources/swe-book/html/ch09.html#code_review-id00002)
* règles d'attribution des PRs : tournant, pour favoriser l'apprentissage, code ownership

---

## Abstract

**C'est quoi une bonne PR ?**

Quelle taille ? Quelle quantité de commits ? Quelle quantité de commentaires ?
Quel genre de commentaires ? Quel lien avec l'outil de ticketing ? 
uel genre d'approbation ? Quel mode de prise en compte des retours ?
Pour quelle durée de développement ? Et quelle durée de relecture ?

Bref, beaucoup de question. Je vais essayer de vous apporter une réponse, et pas seulement "ça dépend". 
