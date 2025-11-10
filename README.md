# Palantir : Plugin QGis de filtre par date et thématique

 
Le plugin Palantir, développé pour une utilisation sous Qgis, est un outil de filtre qui s’applique sur une couche vecteur. Le filtre peut se faire par datation et/ou par thématique. Il a été développé dans le cadre de l’archéologie préventive, mais peut être appliqué à toutes données présentant des champs à filtrer par date ou thématique.
 
SELECTION DE LA COUCHE A FILTRER

Un widget de type combo box liste toutes les couches vecteurs du projet dans lequel le plugin est lancé. Celui-ci permet la recherche en tapant les premières lettres de la couche.
Un bouton « suppression des filtres existant » est présent à droite de la combo box. Sa mise en action supprime tous les filtres présents sur la couche sélectionnée dans la combo box.

 
FILTRE PAR DATATION

> Méthode de datation

Dans un premier temps il faut choisir la méthode de datation utilisée en cochant la check box correspondante :
-	Quatre dates, avec date haute de création, date basse de création, date haute de destruction et date basse de destruction.
-	Deux dates, avec date de création et date de destruction.
Une fois la check box cochée, les champs deviennent accessibles. Chaque date est associée à une combo box listant les champs de la couche sélectionnée pour y appliquer le filtre. On peut alors sélectionner les champs sur lesquels le filtre va s’appliquer.
Le filtre ne pourra être actionné que si tous les champs associés à la check box cochée sont renseignés. Le filtre est annulé quand la check box est décochée.

> Rendu par date ou par période

On choisit ensuite si l’on veut filtrer par date ou par période. Par date, toutes les entités dont les dates de créations sont inférieures et les dates de destruction supérieures sont affichées. Pour la période, toutes les entités dont les dates de créations sont inférieures à la date min et les dates de destruction supérieures à la date max sont affichées.
Ces rendus ne sont disponibles qu’une fois la check box correspondante cochée. On peut fixer la date soit par la/les spinBox soit par le slider. 
Le filtre est annulé quand la check box est décochée.
Le rendu est dynamique et mis à jour quand le slider bouge.


FILTRE PAR THEMATIQUE

La combo box de gauche permet de sélectionner le champ de la couche contenant les thématiques sur lesquelles on souhaite appliquer le filtre.
Une fois le champ sélectionné, la combo box de droite est peuplée par les entrées présentes dans ce champ, à l’exception des entrée nulles ou vides. Il peut être nécessaire de scroller pour accéder aux entrées du bas de la liste. C’est une checkable combobox donc plusieurs éléments peuvent être coché pour une même requête.
Pour que la requête soit prise en compte il est nécessaire d’appuyer sur « Appliquer »


RESULTAT

Les filtres établis s’appliquent à la couche sélectionnée (« T_ECF » dans l’exemple) par une expression de filtrage. Ici la couche est filtrée :
-	Par période entre l’année 0 et 1377, avec date haute de création (« ECF_DHC »), date basse de création (« ECF_DBC »), date haute de destruction (« ECF_DHD »), date basse de destruction (« ECF_DBD »). 
-	Par thématique, sur les valeurs 2, 4 et 6 du champs donnant les références de la rubrique (« ECF_Rf_Rub »)
("ECF_DHC" <=1377 OR "ECF_DBC" <=1377) AND ("ECF_DHD" >= 0 OR "ECF_DBD" >=0) AND  (("ECF_Rf_Rub" = '2')  OR ("ECF_Rf_Rub" = '4')  OR ("ECF_Rf_Rub" = '6') )
L’expression générée est accessible en cliquant sur l’icône « Filtre » présent à droite de la couche concernée.
La zone de visualisation de Qgis affiche alors la couche filtrée.
