# Spécification de Cap Web

1. Quand on envoie 251 caractères, Cap Web refuse et l’erreur cite 250. Vérifié par : test « accepte 250 caractères et refuse 251 » ; essai de 30 s : coller 251 lettres « a », le statut contient « 250 ».
2. Quand on envoie un message vide ou des espaces seuls, Cap Web refuse. Vérifié par : test « refuse le vide et les espaces seuls » ; essai de 30 s : Envoyer sans texte, aucune ligne n’est ajoutée.
3. Quand on envoie «   SALUT » ou « Aide », Cap Web répond comme à « salut » et « aide ». Vérifié par : test « ignore la casse et les espaces autour ».
4. Quand on envoie « cerise » ou « prairie », quelle que soit la casse et les espaces autour, Cap Web donne une réponse propre, distincte du repli. Vérifié par : test « reconnaît les deux mots du cahier personnel, quelles que soient la casse et les espaces autour ».
5. Quand on envoie une phrase inconnue, Cap Web répond par un repli distinct de « salut », « aide » et « test ». Vérifié par : test « répond à une phrase inconnue par un repli distinct » ; essai de 30 s : envoyer « parle-moi de la météo ».
