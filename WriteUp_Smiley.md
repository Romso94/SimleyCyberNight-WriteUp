# Smiley😃 - WriteUp
## Cybernight 2021
#### Categorie : Cryptographie
#### Points : 50
#### Difficulté : Facile/Moyen
#### Auteur : Langley
Challenge : [Smiley😃](https://challenges.cybernight-c.tf/challenges#Smiley😃-53)
#

## Description      
    🤣 🤣 🤣 🤣 et tu brute 🤣 🤣 🤣 🤣
#
Pour démarrer le challenge, on télécharge le fichier flag.crypt qui contient une suite de smileys : 
![image](Smiley.png)

 Dans un premier temps j'ai cherché à trouver une chaine de caractères qui commence par C Y B N comme tous les flags de l'event et donc j'ai essayé de prendre la première lettre de chaque nom de chaque smiley. J'ai obtenu cette suite : C-P-C-O etc... J'ai donc changé de stratégie car c'était une fausse piste.

Ensuite je me suis interessé à la façon dont les smileys étaient gérés par mon navigateur internet (la façon dont ils étaient encodés pour pouvoir être affichés). J'ai utilisé [Cyberchef](https://gchq.github.io/CyberChef/#recipe=To_HTML_Entity(false,'Named%20entities')&input=8J%2BQt/CfkY3wn5C28J%2BRgvCfka/wvqii8J%2BRk/CfkKjwn5GK8J%2BQp/CfkZPwn5Gp8J%2BRovCfkKXwn5GX8J%2BQpPCfkZjwn5Cn8J%2BRk/C%2Bt6Lwn5GxCg) et donc obtenu leur entité HTML en hexadecimal et en décimal  :

|Smiley|  Hexadecimal |  Decimal |
|-------|--------------|---------------|    
|🐷| 1F437 | 128055 |
|👍| 1F44D |128077|
|🐶| 1F436 | 128054|
|👂| 1F442 |128066|
|👯| 1F46F |128111|
|𾷢| 3EA22 |256546|
|👓| 1F453 |128083|
|🐨| 1F428 |128040|
|👊| 1F44A |128074|
|🐧| 1F427 |128039|
|👓| 1F453 |128083|
|👩| 1F469 |128105|
|👢| 1F462 |128098|
|🐥| 1F425 |128037|
|👗| 1F457 |128087|
|🐤| 1F424 |128036|
|👘| 1F458 |128088|
|🐧| 1F427 |128039|
|👓| 1F453 |128083|
|𾷢| 3EDE2 |257506|
|👱| 1F471 |128113 |

Après ça, j'ai cherché à faire un lien entre le premier code Hexadecimal/Decimal que j'avais avec la lettre C 

J'ai commencé par prendre le code ASCII de la lettre C qui est 67 en décimal, donc j'ai essayé :

    128055 + un_nombre = 67

Donc : 
    
    un_nombre = 128055 - 67 = -127988

J'ai essayé ce nombre ensuite sur le deuxième code décimal et j'ai obtenu :
    128077 - 127988 = 89 

La lettre Y étant  89 en décimal en ASCII j'ai creusé cette piste et donc avec un petit script python j'ai appliqué ça à tous les nombres :
```Python
List_Code_Decimal = [128055,128077,128054,128066,128111,256546,128083,128040,128074,128039,128083,128105,128098,128037,128087,128036,128088,128039,128083,257506,128113]

Flag = ''

for i in List_Code_Decimal:
    Flag += chr(i-127988)
print(Flag)
```

Et le flag a été trouvé : 

    CYBN{😮_4V3_un1c0d3_🧮}
    




@SuperSo6  -  @Noct


    




















 
