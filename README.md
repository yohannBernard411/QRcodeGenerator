# QR code Generator

1 Pourquoi ?
===========

Un jour une amie assisante commerciale me dit qu'elle doit créer des QR codes pour chaque employé dans son entreprise, un QR code contenant le nom, prénom, poste, numéro de telephone, Email, Adresse web entreprise.

Je lui demande alors si elle compte créer tout ces QRcode à la main sachant que son entreprise compte pas moins de 100 salariés?

Elle me reponds "oui puisque mon chef me l'a demandé!" :smile:

Je ne peux pas laisser faire une telle chose!!!

Ce n'est pas parce que l'on vous confie une tache merdique que vous devez l'executer comme un merdeux!

2 Execution
===========

Alors le premier but pour moi sera de trouver une api qui renvoi des QRcode aprés une requéte contenant les données.

Et le troisiéme resultat de Google qui m'interpéle est le site ![QRcode generator](https://www.qr-code-generator.com)

Je génére une clef API.

Puis je me connecte sur ![Colab](https://colab.research.google.com/#) pour créer le code nécessaire.

Quel langage??? Si il s'agit de traiter des données, le python me semble le plus sûr, ce n'est pas pour rien que les sites de big data fontionnent en python.

Donc on importe les deux librairies nécessaires à mon projet:
```py
pip install pandas
```
Et
```py
pip install requests
```
Ensuite on charge les librairies:
```py
import pandas as pd
import requests
```






