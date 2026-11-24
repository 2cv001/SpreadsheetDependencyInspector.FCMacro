Traduction en Français plus bas

Have a look to the wiki https://wiki.freecad.org/Macro_Spreadsheet_Dependency_Inspector

The macro shows, as an expandable tree, the dependencies between spreadsheet cells, object properties and sketch constraints: what each item uses, and what uses it. It also shows the items in error, and where the error comes from.

The macro is multilingual, currently supporting English and French.
The language used is the one you selected in your FreeCAD preferences.
<img width="691" height="610" alt="image" src="https://github.com/user-attachments/assets/592382bf-0311-4a7f-9f5d-70d422b5e32f" />

**Usage:**

Select the starting point, then run the macro:
- one or several cells in an open spreadsheet;
- a property in the property view (e.g. Length of a Pad);
- one or several objects in the tree or the 3D view (Body, Sketch, Pad...): their properties and cells that have an expression, are used or are in error, including the content of a Body, Part or group;
- the document, at the top of the tree, to analyse the whole project.

**Lines shown:**
- *Uses* / *Used by*: the two branches of each line.
- *Cells*, *Constraints*, *Others*: the kinds of lines shown.
- *Errors*: when checked, the lines in error are always shown, with what they use. When unchecked, it does not prevent the lines in error from being shown. With *Errors* alone, you only see the errors and their causes.

**Columns:** Label/alias, Expression, Result and constraint Type can be shown or hidden.

**Error detection in the FreeCAD document:**
- **Red**: the cell or property is in error (cell error, expression that fails, value refused by FreeCAD, invalid object, sketch constraint refused by the solver).
- **Bold red**: the error starts here; a red line without bold gets its error from another line (shown in its tooltip).
- **Orange**: next to a line in error, the value that causes it, e.g. a cell containing the text `a` where a number is expected. The cell itself is not in error, so it is orange only next to that line.
- **Orange italic**: next to a line in error whose cause is unknown (division by zero, pad of length zero...), the values it uses, to check.

The tooltip of each line explains its state.

**In the tree:**
- Double-click a line to open the cell, the property or the constraint (sketch opened). In the Expression column, double-click to select the terms of the expression.
- Single click to edit a Label/Alias or an expression.

The refresh button <img width="36" height="30" alt="image" src="https://github.com/user-attachments/assets/dcc1fc5e-25ed-461c-87eb-7176b053d575" /> re-runs the analysis, for example after you modify a cell. It starts again from what you selected last (cells, property, objects or document).
The expand/collapse buttons and the level counter expand or collapse the whole tree. You can also do it branch by branch by clicking on the ▶ or ▼ symbols. Checking or unchecking a box keeps the level shown.


**Français**

Voir le wiki : https://wiki.freecad.org/Macro_Spreadsheet_Dependency_Inspector

La macro affiche sous forme d'arbre dépliable les dépendances entre les cellules des tableurs, les propriétés des objets et les contraintes des esquisses : ce que chaque élément utilise, et ce qui l'utilise. Elle montre aussi les éléments en erreur, et d'où vient l'erreur.

La macro est multilingue, pour l'instant anglais / français.
La langue est celle que vous avez choisie dans les préférences de FreeCAD.
<img width="689" height="611" alt="image" src="https://github.com/user-attachments/assets/293068e6-f5c2-4db7-b6b7-941ee4648208" />

**Mode d'utilisation :**

Sélectionnez le point de départ, puis lancez la macro :
- une ou plusieurs cellules dans un tableur ouvert ;
- une propriété dans la fenêtre des propriétés (ex : Longueur d'une protrusion) ;
- un ou plusieurs objets dans l'arbre ou la vue 3D (Body, esquisse, protrusion...) : leurs propriétés et cellules qui ont une expression, sont utilisées ou sont en erreur, y compris le contenu d'un Body, d'un Part ou d'un groupe ;
- le document, tout en haut de l'arbre, pour analyser tout le projet.

**Lignes affichées :**
- *Utilise* / *Est utilisé par* : les deux branches de chaque ligne.
- *Cellules*, *Contraintes*, *Autres* : les types de lignes affichées.
- *Erreurs* : cochée, les lignes en erreur sont toujours affichées, avec ce qu'elles utilisent. Décochée, elle n'empêche pas pour autant d'afficher les lignes en erreur. Avec *Erreurs* seule, on ne voit que les erreurs et leurs causes.

**Colonnes :** Label/alias, Expression, Résultat et Type de contrainte peuvent être affichés ou masqués.

**Détection des erreurs dans le document FreeCAD :**
- **Rouge** : la cellule ou la propriété est en erreur (erreur de cellule, expression qui échoue, valeur refusée par FreeCAD, objet invalide, contrainte d'esquisse refusée par le solveur).
- **Rouge gras** : l'erreur part d'ici ; une ligne rouge sans gras tient son erreur d'une autre ligne (indiquée dans son infobulle).
- **Orange** : à côté d'une ligne en erreur, la valeur qui la provoque, par exemple une cellule qui contient le texte `a` là où un nombre est attendu. La cellule elle-même n'est pas en erreur : elle n'est en orange qu'à côté de cette ligne.
- **Orange italique** : à côté d'une ligne en erreur dont la cause est inconnue (division par zéro, protrusion de longueur nulle...), les valeurs qu'elle utilise, à vérifier.

L'infobulle de chaque ligne explique son état.

**Dans l'arbre :**
- Double clic sur une ligne : ouvre la cellule, la propriété ou la contrainte (esquisse ouverte). Dans la colonne Expression, le double clic sélectionne les termes de l'expression.
- Simple clic pour modifier un Label/Alias ou une expression.

Le bouton refresh <img width="36" height="30" alt="image" src="https://github.com/user-attachments/assets/131cef95-d078-475c-a95c-97890e5dc68f" /> relance l'analyse, par exemple après la modification d'une cellule. Il repart de ce que vous avez sélectionné en dernier (cellules, propriété, objets ou document).
Les boutons déplier / replier et le compteur de niveau déplient ou replient tout l'arbre. Il est aussi possible de le faire branche par branche en cliquant sur les ▶ ou ▼. Cocher ou décocher une case garde le niveau affiché.
