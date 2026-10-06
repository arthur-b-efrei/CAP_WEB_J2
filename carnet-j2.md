# Carnet de bord · J2

Binôme : b10 · Membres : Bouchra BENBELKACEM et Arthur BRIOT · Nos réglages sont dans `atelier/cahier-personnel.json'

## Mon positionnement (chacun de vous deux)

Pour chaque notion, chacun écrit « à l'aise » ou « à renforcer ». Ce n'est ni évalué ni classé : c'est votre point de départ pour le bilan individuel de fin de module.

| Notion | Membre 1 : Bouchra BENBELKACEM | Membre 2 : Arthur BRIOT |
|---|---|---|
| Structure HTML |à l'aise | à l'aise |
| CSS et responsive |à l'aise | à l'aise|
| JavaScript |à l'aise | à renforcer|
| DOM et événements |à renforcer |à l'aise |
| Git |à l'aise | à l'aise|
| Tests |à l'aise | à renforcer |

Chacun, en une phrase, son objectif personnel pour J2 et J3.

Membre 1 : Pour J2 et J3, mon objectif est de renforcer mes compétences dans la gestion du DOM et des événements, afin d'être plus autonome sur les futurs projets.

Membre 2 : Mon objectif est de renforcer mes compétences en JavaScript et en test afin d'être plus autonome sur les futurs projets.

## R1 · Les tests automatisés

Les tests rouges du départ, et ce que vous en avez fait :

| Test rouge | Cause trouvée (une phrase) | Fichier | Message du commit `fix:` |
|---|---|---|---|
| refuse le vide et les espaces seuls | Le vide était testé avant `trim()`, donc les espaces seuls passaient. | `public/js/brain.js` | `fix: refuse le vide après avoir retiré les espaces` |
| accepte 250 caractères et refuse 251 | La longueur était comparée à 280 au lieu de `LIMITE`. | `public/js/brain.js` | `fix: la limite de caractères suit LIMITE` |
| ignore la casse et les espaces autour | `replyTo` passait en minuscules mais ne retirait pas les espaces. | `public/js/brain.js` | `fix: replyTo ignore aussi les espaces autour` |
| reconnaît les deux mots du cahier personnel, quelles que soient la casse et les espaces autour | Même défaut : sans `trim()`, `  CERISE ` ne matchait pas. | `public/js/brain.js` | `fix: replyTo ignore aussi les espaces autour` |
| répond à une phrase inconnue par un repli distinct | L’inconnu renvoyait la même phrase que « aide ». | `public/js/brain.js` | `fix: repli distinct pour une phrase inconnue` |
| view.js affiche du texte et ne décide pas des réponses | L’affichage injectait du HTML avec `innerHTML`. | `public/js/view.js` | `fix: view.js affiche avec textContent` |

Avec l'agent : aucune proposition refusée ; les 5 défauts étaient dans `public/js/`, le contrat n’a pas été touché.

Pour aller plus loin : `liste` est devenu `motsConnusFormates`, pour dire que ce sont les mots du cahier, déjà mis en forme pour la réponse « aide ».

## R2 · Documenter le projet

Vos trois documents sont dans `atelier` : `README.md`, `SPEC.md` et `AGENTS.md`. Rien à recopier ici.

Pour aller plus loin, avec l'agent, les demandes du formateur :

| Demande | Ce qu'a fait l'agent | Votre décision | Règle d'`AGENTS.md` concernée (ou ajoutée) |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

## R3 · Premiers tests unitaires

| À remplir | Votre réponse |
|---|---|
| Fonction tirée | |
| Le rouge vu (message exact) | |
| Identifiant du commit `test:` | |
| Identifiant du commit `feat:` | |
| Casse volontaire : la ligne changée | |
| Casse volontaire : le test devenu rouge | |
| Pour aller plus loin : la deuxième fonction | |

Les critères C1 à C5 de votre fonction, recopiés de la fiche :

## R4 · La revue de code

| Patch | Accepté ou refusé | Fichier et ligne | Raison |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

Pour aller plus loin : le patch que vous avez corrigé, et ce que vous avez changé.

## Fin de journée

Chacun, une phrase : ce que vous savez faire ce soir et que vous ne saviez pas faire ce matin. Relisez votre positionnement : une notion est-elle passée de « à renforcer » à « à l'aise » ?
