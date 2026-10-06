# Conventions du projet

Ce fichier est lu par un nouvel arrivant et par l’agent. Ce qui n’y est pas écrit, personne ne le sait.

## Nommage

- Une fonction porte un verbe qui dit ce qu’elle fait, comme `validateMessage`, `replyTo` ou `renderMessages`.
- Une constante est en majuscules, comme `LIMITE`, `MOTS`, `REPONSES` ou `CLE`.
- Un fichier porte le rôle du module : `brain.js` (règles), `view.js` (affichage), `app.js` (câblage). Pas de fichier fourre-tout du type `chatbot.js`.
- Un message de commit commence par un type, puis dit ce qui change, en français : `fix:`, `docs:`, `feat:`, `refactor:`, `test:`. Exemple : `fix: la limite de caractères suit LIMITE`.

## Interdits

- Ne modifie jamais `tests/contrat/` ni `browser/contrat.spec.js` ni `cahier-personnel.json`. Si un test te semble faux, arrête-toi et explique pourquoi.
- N’utilise jamais `innerHTML`, `outerHTML` ou `insertAdjacentHTML` : le texte tapé reste du texte (`textContent`).
- Ne mélange pas les rôles : `brain.js` ne touche pas à la page ; `view.js` ne décide pas des réponses et ne stocke rien ; `app.js` ne crée pas les `li`.
- Ne mets jamais de clé, de jeton, de mot de passe ou de donnée personnelle dans un fichier, un commit ou un prompt.
- N’accepte aucun changement de l’agent sans avoir relu le diff. Une ligne que tu ne sais pas expliquer se refuse.
- Ne fais pas `git add -A`. Ajoute seulement les fichiers de l’étape, par exemple `git add -- public/js`.
