# Problème
C'est chiant de chercher une machine à café ou une machine à canette qui fonctionne et qui a du stock.

# Solution
Application communautaire qui permet de dire si telle ou telle
machine à café/canette fonctionne ou a tellle ou telle boisson.

Chaque utilisateur peut changer le statut d'une machine à l'aide d'une appli
pour dire si elle a encore du café/du coca/est éteinte, etc...

# Idées
- l'utilisateur voit la liste des machines :
    - par bâtiment
    - par type
    - par dispo/pas dispo
- l'utilisateur met à jour l'état d'une machine en:
    - scanant un qrcode/machin code posé sur la machine
    - choisissant dans une liste l'état de la machine

# Liste des machines
    - STPI
        - deux cafés
        - une canette
    - GM
        - une café
        - une canette
    - GEI
        - une café
    - CSH
        - une café
        - une canette
    - GMM
        - une café
    - GC
        - ????
    - GB
        - ????
    - GP
        - ????

# Technique
    - serveur avec mini bdd :
        - en nodejs : c'est rapide et simple à faire
        - sqlite : pas besoin de plus, quelques tables avec la liste des machines et leur état
    - appli android :
        - scanner les qrcode
        - liste des machines par:
            - batiment
            - dispo
            - type
        - bouton pour actualiser l'état (actualisation auto en option?)

# BDD
## Cahier des charges
    Une machine est dans un batiment de l'INSA. Il existe plusieurs types de machine : boisson chaude et boisson froide.
    On doit pouvoir avoir le détail des boissons dispo pour chaque machine à boisson froide : coca, icetea, fanta, etc...
    On doit pouvoir savoir si la machine marche ou non

## Proposition
Batiments(#idBatiment, nom)
Machines(#idMachine, batiment#Batiments(idBatiment), qrcode, type, status)
Boissons(#idBoisson, nom)
MachinesBoissons(#machine#Machines(idMachine), #boisson#Boissons(idBoisson), reste)

qrcode: valeur que renvois le qrcode quand on le scan (token unique pour chaque machine)
type: chaud, froid
status: on, off
reste: oui, non
