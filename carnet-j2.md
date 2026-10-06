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
| Fonction tirée | `synonyme` (F1) |
| Le rouge vu (message exact) | `SyntaxError: The requested module '../public/js/brain.js' does not provide an export named 'synonyme'` |
| Identifiant du commit `test:` | à remplir après `git commit -m "test: synonyme, critères C1 à C5"` |
| Identifiant du commit `feat:` | à remplir après `git commit -m "feat: synonyme"` |
| Casse volontaire : la ligne changée | le `return texte;` final de `synonyme` remplacé par `return '';` |
| Casse volontaire : le test devenu rouge | `C4 : un autre message revient en minuscules, sans les espaces autour` (`'' !== 'météo'`) |
| Pour aller plus loin : la deuxième fonction | `compterMots` (F2) |

Les critères C1 à C5 de votre fonction, recopiés de la fiche :

- C1 : `'coucou'`, `'hello'` et `'bonsoir'` donnent `'salut'`.
- C2 : `'help'` et `'sos'` donnent `'aide'`.
- C3 : la casse et les espaces autour ne comptent pas, `'  HELLO '` donne `'salut'`.
- C4 : un autre message revient en minuscules, sans les espaces autour, `'  Météo '` donne `'météo'`.
- C5 : ce qui n'est pas du texte (`undefined`, `null`, `42`) donne `''`, sans erreur.

## R4 · La revue de code

| Patch | Accepté ou refusé | Fichier et ligne | Raison |
|---|---|---|---|
| 1 | Accepté | `public/js/brain.js` L18 et L47–49 ; `tests/merci.test.js` | Description = diff : « merci » a sa réponse, casse et espaces via `trim`+`toLowerCase`. Le contrat n’est pas touché. Dans la page, `<b>gras</b>` reste du texte, les espaces seuls sont refusés, « aide » répond. `npm test` : 45/45. |
| 2 | Refusé | `tests/contrat/brain.contrat.test.js` L68–71 et L86 ; `public/js/brain.js` L37–38 | Piège : le contrat est affaibli (`'  SALUT '` devient `'SALUT'`). `normaliser` fait `toLowerCase` sans `trim`, donc `'  SALUT '` et `'  AU REVOIR '` tombent dans le repli. Les tests restent verts parce que l’assertion sur les espaces a disparu. |
| 3 | Refusé | `public/js/view.js` L4–6 et L13 | Piège : `enGras` produit du HTML et `createContextualFragment` l’injecte (comme `innerHTML`). Essai : `<b>gras</b>` s’affiche en gras, `li.innerHTML` = `<strong>Vous</strong> : <b>gras</b>`. Le contrat ne cherche que `innerHTML`, donc `npm test` reste vert. |

Pour aller plus loin : le patch que vous avez corrigé, et ce que vous avez changé.

Patch 2, dans `essai-2` puis `abordage/mon-patch.patch` : `normaliser` fait aussi `trim()` ; le fichier `tests/contrat/brain.contrat.test.js` n’est plus modifié ; le test vérifie `'  AU REVOIR '`. `npm test` : 46/46, et `'  SALUT '` égale de nouveau `'salut'`.

## Fin de journée

Chacun, une phrase : ce que vous savez faire ce soir et que vous ne saviez pas faire ce matin. Relisez votre positionnement : une notion est-elle passée de « à renforcer » à « à l'aise » ?
