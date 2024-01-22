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

Et le troisiéme resultat de Google qui m'interpéle est le site [QRcode generator](https://www.qr-code-generator.com)

Je génére une clef API.

Puis je me connecte sur mon [Colab](https://colab.research.google.com/#) pour créer le code nécessaire.


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
On ajouter le dossier de sortie XxxxxxxxQR
Ajouter le dossier employees.csv dans la partie dossier.
Vérification du CSV:
```py
all_employees = pd.read_csv("Xxxxxxxx.csv", sep=',', encoding='latin-1')
all_employees
```
Bouclage pour chaque element de la liste
```py
# On charge le dossier avec Pandas
df = pd.DataFrame(all_employees)
# On creer la variable de sortie
output = []
# Pour chaque ligne:
for index, row in df.iterrows():
    # On ajoute la ligne retravaillée au dossier de sortie
    output.append((row['Nom'], row['Prénom'], row['Poste'], str(0)+str(row['Telephone']), row['Email'], row['AdressProlians']))
print("Le dossier de sortie contient: "+str(len(output)))
# variables fixes pour la requéte:
clef = "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
url = "https://api.qr-code-generator.com/v1/create?access-token="+clef
rank = 0
# pour chaque employé
for employe in output:
  print("boucle n°"+str(rank+1)+" contenant: "+str(employe))
  # adaptation du corps de la requete
  corp = {
      "frame_name": "no-frame",
      "qr_code_text": str(employe[1])+" "+str(employe[0])+"\n"+str(employe[2])+"\n"+str(employe[3])+"\n"+str(employe[4])+"\n"+str(employe[5]),
      "image_format": "SVG",
      "qr_code_logo": "scan-me-square"}
  rank += 1
  print("Requéte n°"+str(rank))
  # envoi de la requete
  reponse = requests.post(url, corp)
  # creation du fichier (prénom-nom.svg)
  fichier = open("ProliansQR/"+employe[1]+"-"+employe[0]+".svg", "a")
  # enregistrement du fichier dans le dossier
  fichier.write(reponse.text)
  #fermeture du fichier
  fichier.close()
#signal de fin
print(" **********************")
print("*                      *")
print("*   Traitement finit   *")
print("*                      *")
print(" **********************")
print("Toutes les données employées sont converties en QR codes")
print("il y a "+str(rank)+" employées")
```
Et voila tout les QRcodes sont enregistré dans le dossier, avec pour identifiant "prénom-nom".
En quelques minutes, nous venons de réaliser une tache en l'automatisant, une tache qui aurait pris des heures sinon.
Ce qui prouve encore une fois la puissance du code.








