# Palantir : Plugin QGis de filtre par date et thématique <img width="281" height="281" alt="image" src="https://github.com/user-attachments/assets/35d09e8c-bc84-40d4-a549-bcec4437066a" />


 
Le plugin Palantir, développé pour une utilisation sous Qgis, est un outil de filtre qui s’applique sur une couche vecteur. Le filtre peut se faire par datation et/ou par thématique. Il a été développé dans le cadre de l’archéologie préventive, mais peut être appliqué à toutes données présentant des champs à filtrer par date ou thématique.
<img width="945" height="553" alt="image" src="https://github.com/user-attachments/assets/1191521b-7fc6-4dc1-a12d-7647a381294a" />

<i>Figure 1 : Fenêtre du plugin à son ouverture</i>
 
<br><strong>SELECTION DE LA COUCHE A FILTRER</strong>

Un widget de type combo box liste toutes les couches vecteurs du projet dans lequel le plugin est lancé. Celui-ci permet la recherche en tapant les premières lettres de la couche.
Un bouton « suppression des filtres existant » est présent à droite de la combo box. Sa mise en action supprime tous les filtres présents sur la couche sélectionnée dans la combo box.
<img width="945" height="52" alt="image" src="https://github.com/user-attachments/assets/d5152d46-8c3c-4c8d-a1a1-d40dfc1361d1" />

<i>Figure 2 : Zone de sélection de la couche à filtrer</i>

<img width="758" height="985" alt="image" src="https://github.com/user-attachments/assets/8348c1f9-4fa5-4ba0-b7dd-ed4a49f3d6ae" />

<i>Figure 3 : Recherche de la couche dans la combo box</i>

 
<br><strong>FILTRE PAR DATATION</strong>

> Méthode de datation

Dans un premier temps il faut choisir la méthode de datation utilisée en cochant la check box correspondante :
-	Quatre dates, avec date haute de création, date basse de création, date haute de destruction et date basse de destruction.
-	Deux dates, avec date de création et date de destruction.
Une fois la check box cochée, les champs deviennent accessibles. Chaque date est associée à une combo box listant les champs de la couche sélectionnée pour y appliquer le filtre. On peut alors sélectionner les champs sur lesquels le filtre va s’appliquer.
<img width="945" height="170" alt="image" src="https://github.com/user-attachments/assets/eee6fe97-ded1-4eb4-8012-078e1449ea1f" />

<i>Figure 4 : Datation par 4 dates</i>

Le filtre ne pourra être actionné que si tous les champs associés à la check box cochée sont renseignés. Le filtre est annulé quand la check box est décochée.


> Rendu par date ou par période

On choisit ensuite si l’on veut filtrer par date ou par période. Par date, toutes les entités dont les dates de créations sont inférieures et les dates de destruction supérieures sont affichées. Pour la période, toutes les entités dont les dates de créations sont inférieures à la date min et les dates de destruction supérieures à la date max sont affichées.
Ces rendus ne sont disponibles qu’une fois la check box correspondante cochée. On peut fixer la date soit par la/les spinBox soit par le slider. 
Le filtre est annulé quand la check box est décochée.
Le rendu est dynamique et mis à jour quand le slider bouge.
<img width="945" height="158" alt="image" src="https://github.com/user-attachments/assets/5578f9c0-7fb5-4247-8afe-1f5184833e90" />

<i>Figure 5 : Filtre par période activé</i>


<br><strong>FILTRE PAR THEMATIQUE</strong>

La combo box de gauche permet de sélectionner le champ de la couche contenant les thématiques sur lesquelles on souhaite appliquer le filtre.
Une fois le champ sélectionné, la combo box de droite est peuplée par les entrées présentes dans ce champ, à l’exception des entrée nulles ou vides. Il peut être nécessaire de scroller pour accéder aux entrées du bas de la liste. C’est une checkable combobox donc plusieurs éléments peuvent être coché pour une même requête.
Pour que la requête soit prise en compte il est nécessaire d’appuyer sur « Appliquer ».
<img width="945" height="179" alt="image" src="https://github.com/user-attachments/assets/6bc868c7-cd85-4bce-9b63-7b259caa5a9e" />

<i>Figure 6 : Filtre par thématique</i>



<br><strong>RESULTAT</strong>

Les filtres établis s’appliquent à la couche sélectionnée (« T_ECF » dans l’exemple) par une expression de filtrage. Ici la couche est filtrée :
-	Par période entre l’année 0 et 1377, avec date haute de création (« ECF_DHC »), date basse de création (« ECF_DBC »), date haute de destruction (« ECF_DHD »), date basse de destruction (« ECF_DBD »). 
-	Par thématique, sur les valeurs 2, 4 et 6 du champs donnant les références de la rubrique (« ECF_Rf_Rub »)
("ECF_DHC" <=1377 OR "ECF_DBC" <=1377) AND ("ECF_DHD" >= 0 OR "ECF_DBD" >=0) AND  (("ECF_Rf_Rub" = '2')  OR ("ECF_Rf_Rub" = '4')  OR ("ECF_Rf_Rub" = '6') )
L’expression générée est accessible en cliquant sur l’icône « Filtre » présent à droite de la couche concernée.
<img width="492" height="28" alt="image" src="https://github.com/user-attachments/assets/b5847a6a-566a-42e6-9bf8-d24ec8091407" />

<i>Figure 7 : Icône présent quand un filtre est appliqué sur la couche</i>

La zone de visualisation de Qgis affiche alors la couche filtrée.
