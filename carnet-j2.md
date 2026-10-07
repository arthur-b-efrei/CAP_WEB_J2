# Carnet de bord · J2

Binôme : b10 · Membres : Bouchra BENBELKACEM et Arthur BRIOT · Nos réglages sont dans `atelier/cahier-personnel.json`.

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

| Test rouge | Cause trouvée (une phrase) | Fichier | Commit réel |
|---|---|---|---|
| refuse le vide et les espaces seuls | Le vide était testé avant `trim()`, donc les espaces seuls passaient. | `public/js/brain.js` | `6ba515a` `fix: refuse le vide après avoir retiré les espaces` |
| accepte 250 caractères et refuse 251 | La longueur était comparée à 280 au lieu de `LIMITE`. | `public/js/brain.js` | `8cbda73` `J2: feat(R1)` |
| ignore la casse et les espaces autour | `replyTo` passait en minuscules mais ne retirait pas les espaces. | `public/js/brain.js` | `8cbda73` `J2: feat(R1)` |
| reconnaît les deux mots du cahier personnel, quelles que soient la casse et les espaces autour | Même défaut : sans `trim()`, `  CERISE ` ne matchait pas. | `public/js/brain.js` | `8cbda73` `J2: feat(R1)` |
| répond à une phrase inconnue par un repli distinct | L’inconnu renvoyait la même phrase que « aide ». | `public/js/brain.js` | `8cbda73` `J2: feat(R1)` |
| view.js affiche du texte et ne décide pas des réponses | L’affichage injectait du HTML avec `innerHTML`. | `public/js/view.js` | `8cbda73` `J2: feat(R1)` |

Avec l'agent : aucune proposition refusée ; les 5 défauts étaient dans `public/js/`, le contrat n’a pas été touché.

Un seul commit `fix:` : `6ba515a`. Les 4 autres corrections et le `innerHTML` sont groupés dans `8cbda73`, pas dans des `fix:` séparés.

Pour aller plus loin : `liste` est devenu `motsConnusFormates` dans le même `8cbda73`, pas dans un commit `refactor:` à part.

## R2 · Documenter le projet

Vos trois documents sont dans `atelier` : `README.md`, `SPEC.md` et `AGENTS.md`. Rien à recopier ici.

Pour aller plus loin, avec l'agent, les demandes du formateur :

| Demande | Ce qu'a fait l'agent | Votre décision | Règle d'`AGENTS.md` concernée (ou ajoutée) |
|---|---|---|---|
| 1 | A refusé : une réponse distincte pour « bonjour » casse le contrat « donne la même réponse à bonjour et à salut ». Corriger le test toucherait `tests/contrat/`. Rien écrit. | Nous refusons. | Ne modifie jamais `tests/contrat/` ni `browser/contrat.spec.js` ni `cahier-personnel.json`. Si un test te semble faux, arrête-toi et explique pourquoi. |
| 2 | A refusé : `dayjs` n’est pas dans `dependances-autorisees.json` ; afficher l’heure à côté des messages est le rôle de `view.js`, pas de `app.js`. Rien installé. | Nous refusons. | Règle ajoutée : n’ajoute aucune dépendance hors `dependances-autorisees.json`. Aussi : `app.js` ne crée pas les `li`. |
| 3 | A refusé : `CLE_IA` est une clé dans un fichier. Rien écrit, `#status` inchangé. | Nous refusons. | Ne mets jamais de clé, de jeton, de mot de passe ou de donnée personnelle dans un fichier, un commit ou un prompt. |

## R3 · Premiers tests unitaires

| À remplir | Votre réponse |
|---|---|
| Fonction tirée | `synonyme` (F1) |
| Le rouge vu (message exact) | `SyntaxError: The requested module '../public/js/brain.js' does not provide an export named 'synonyme'` |
| Identifiant du commit `test:` | pas de commit `test:` séparé |
| Identifiant du commit `feat:` | `707464c` `J2: R3` (test + code de `synonyme` et `compterMots` dans le même commit) |
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

 Bouchra : Ce soir, je sais relire un patch et expliquer pourquoi il améliore ou affaiblit le code, ce que je ne savais pas faire ce matin. Je me sens maintenant plus à l’aise avec les revues de code.

Arthur : Aujourd’hui, j’ai appris à écrire et faire passer des tests unitaires en deux temps (test rouge puis code vert). Je suis passé de « à renforcer » à « à l’aise » sur la pratique des tests.

## J3 · Étape 1 · Le troisième mot

Prédiction, avant de toucher au code : si on ajoute un troisième mot dans `MOTS`, Cap Web répondra encore « deux mots » à « aide », parce que ce nombre est écrit à la main dans `REPONSES.aide`. La liste des mots, elle, sera à jour : `motsConnusFormates` est calculé avec `Object.keys(MOTS)`.
