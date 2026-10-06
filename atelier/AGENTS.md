# Conventions du projet

## 1. Nommage

- Une fonction porte un verbe qui décrit clairement ce qu'elle fait, par exemple `validateMessage`.
- Une constante est écrite en majuscules avec des underscores, par exemple `MAX_MESSAGE_LENGTH`.
- Un fichier porte un nom court et descriptif, par exemple `chatbot.js`.
- Un message de commit est court et décrit clairement la modification, par exemple `feat: add chatbot buttons`.

## 2. Interdits

- Ne modifie jamais `tests/contrat/`.
- Ne modifie jamais `cahier-personnel.json`.
- Ne supprime jamais un fichier existant sans autorisation.
- Ne modifie pas plusieurs fonctionnalités différentes dans le même changement.
- Si un test semble faux, arrête-toi et explique le problème au lieu de modifier le test.