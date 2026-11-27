Traduction en Français plus bas

Have a look to the wiki https://wiki.freecad.org/Macro_Spreadsheet_Dependency_Inspector

The macro shows, as an expandable tree, the dependencies between spreadsheet cells, object properties and sketch constraints: what each item uses, and what uses it. It also shows the items in error, and where the error comes from.

The macro is multilingual, currently supporting English and French.
The language used is the one you selected in your FreeCAD preferences.
<img width="872" height="536" alt="image" src="https://github.com/user-attachments/assets/a840730c-19a2-40df-8f37-89d8a917a505" />


**Usage:**

Select the starting point, then run the macro:
- one or several cells in an open spreadsheet;
- one or several properties in the property view (e.g. Length of a Pad);
- one or several constraints in a sketch being edited (in the 3D view or the constraint list), or elements of the sketch (line, circle, point, axis...): all the constraints on these elements are then selected in the sketch, including those without a value (perpendicular...), and the tree starts from them; a constraint without a name is shown as `Sketch.Constraints[5]  (Constraint6)`: the index of the expression starts at 0, the number in the FreeCAD list at 1;
- one or several objects in the tree or the 3D view (Body, Sketch, Pad...): their properties and cells that have an expression, are used or are in error, including the content of a Body, Part or group;
- the document, at the top of the tree, to analyse the whole project.

**Lines shown:**
- *Uses* / *Used by*: the two branches of each line.
- *Cells*, *Constraints*, *Others*: the kinds of lines shown.
- *Errors*: when checked, the lines in error are always shown, with what they use. When unchecked, it does not prevent the lines in error from being shown. With *Errors* alone, you only see the errors and their causes.
- *Empty*: when checked, the selected starting points without any link are also shown (e.g. a cell that uses nothing and that nothing uses, an empty cell, a constraint without expression). The lines with links are shown as usual.

**Columns:** Label/alias, Expression, Result and constraint Type can be shown or hidden.

**Double-click:** *Zoom on constraint* checked, double-clicking a constraint also frames the 3D view on it: the elements it links and its dimension take about 1/3 of the window, to see around; unchecked, the view does not move (useful when you have set your zoom precisely).

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

**Using the macro to understand the errors of the project:**

When a recompute fails (object marked with an exclamation mark, a Pad that no longer builds, a sketch that no longer solves), the macro helps you go back to the cause:

1. **List the errors**: select the document at the top of the FreeCAD tree, run the macro, then keep only *Errors* checked in the *Lines* panel. Only the lines in error and their causes remain.
2. **Find where the error starts**: a **bold red** line is the origin of an error: it is the one FreeCAD reports. A red line without bold only inherits it, and its tooltip says from which line. Start with the bold lines: one origin often explains all the others. For example, a Pad in error because its sketch no longer solves says in its tooltip that the error comes from the sketch.
3. **Read the cause**: the tooltip of the line in error gives the message (cell error, expression that fails, value refused by FreeCAD, constraint refused by the solver as conflicting, redundant or malformed...). In its *Uses* branch, some lines may appear:
   - in **orange**: the value that causes the error, e.g. a cell containing text where a number is expected;
   - in **orange italic**: when the macro does not know which value is involved (division by zero, length zero...), it shows all the values used; one of them causes the error, check them one by one.
4. **Go to the source**: double-click the orange or bold red line to open the cell in its spreadsheet, the property, or the constraint in its sketch. If *Zoom on constraint* is checked, the view frames the constraint in its surroundings. Double-clicking the expression of a line selects what it uses.
5. **Fix**: in FreeCAD as usual (spreadsheet, property view, sketch), or directly in the tree of the macro (Expression column). If you make the change in the tree of the macro and it results in a FreeCAD error, the macro warns you and offers to cancel the change.
6. **Check**: click the refresh button. When no line is red any more, the errors are solved.

**Sketch that no longer solves:** open the sketch, select the line, circle or point concerned, then run the macro (or click refresh). All the constraints of these elements are selected in the sketch, and the tree shows which cells and properties drive each of them: you quickly see which value of the spreadsheet has changed. The constraints refused by the solver are in bold red.


**Français**

Voir le wiki : https://wiki.freecad.org/Macro_Spreadsheet_Dependency_Inspector

La macro affiche sous forme d'arbre dépliable les dépendances entre les cellules des tableurs, les propriétés des objets et les contraintes des esquisses : ce que chaque élément utilise, et ce qui l'utilise. Elle montre aussi les éléments en erreur, et d'où vient l'erreur.

La macro est multilingue, pour l'instant anglais / français.
La langue est celle que vous avez choisie dans les préférences de FreeCAD.
<img width="868" height="540" alt="image" src="https://github.com/user-attachments/assets/133c5d25-64ae-4dc8-8332-8f2463e750e6" />



**Mode d'utilisation :**

Sélectionnez le point de départ, puis lancez la macro :
- une ou plusieurs cellules dans un tableur ouvert ;
- une ou plusieurs propriétés dans la fenêtre des propriétés (ex : Longueur d'une protrusion) ;
- une ou plusieurs contraintes dans une esquisse en cours d'édition (vue 3D ou liste des contraintes), ou des éléments de l'esquisse (ligne, cercle, point, axe...) : toutes les contraintes de ces éléments sont alors sélectionnées dans l'esquisse, y compris celles sans valeur (perpendicularité...), et l'arbre part d'elles ; une contrainte sans nom est affichée `Sketch.Constraints[5]  (Constraint6)` : l'index de l'expression part de 0, le numéro de la liste de FreeCAD de 1 ;
- un ou plusieurs objets dans l'arbre ou la vue 3D (Body, esquisse, protrusion...) : leurs propriétés et cellules qui ont une expression, sont utilisées ou sont en erreur, y compris le contenu d'un Body, d'un Part ou d'un groupe ;
- le document, tout en haut de l'arbre, pour analyser tout le projet.

**Lignes affichées :**
- *Utilise* / *Est utilisé par* : les deux branches de chaque ligne.
- *Cellules*, *Contraintes*, *Autres* : les types de lignes affichées.
- *Erreurs* : cochée, les lignes en erreur sont toujours affichées, avec ce qu'elles utilisent. Décochée, elle n'empêche pas pour autant d'afficher les lignes en erreur. Avec *Erreurs* seule, on ne voit que les erreurs et leurs causes.
- *Vide* : cochée, les points de départ sélectionnés sans aucun lien sont aussi affichés (ex : une cellule qui n'utilise rien et que rien n'utilise, une cellule vide, une contrainte sans expression). Les lignes qui ont des liens restent affichées comme d'habitude.

**Colonnes :** Label/alias, Expression, Résultat et Type de contrainte peuvent être affichés ou masqués.

**Double-clic :** *Zoom sur contrainte* cochée, le double-clic sur une contrainte cadre aussi la vue 3D sur elle : les éléments qu'elle relie et sa cote occupent environ 1/3 de la fenêtre, pour voir autour ; décochée, la vue ne bouge pas (utile quand on a réglé son zoom précisément).

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

**Utiliser la macro pour comprendre les erreurs du projet :**

Quand un recalcul échoue (objet marqué d'un point d'exclamation, protrusion qui ne se construit plus, esquisse qui ne se résout plus), la macro aide à remonter jusqu'à la cause :

1. **Faire le tour des erreurs** : sélectionnez le document tout en haut de l'arbre FreeCAD, lancez la macro, puis ne laissez cochée que *Erreurs* dans le panneau *Lignes*. Seules restent les lignes en erreur et leurs causes.
2. **Trouver d'où part l'erreur** : une ligne en **rouge gras** est l'origine d'une erreur : c'est elle que signale FreeCAD. Une ligne rouge sans gras ne fait qu'en hériter, et son infobulle indique de quelle ligne. Commencez par les lignes en gras : une seule origine explique souvent toutes les autres. Par exemple, une protrusion en erreur parce que son esquisse ne se résout plus indique dans son infobulle que l'erreur vient de l'esquisse.
3. **Lire la cause** : l'infobulle de la ligne en erreur donne le message (erreur de cellule, expression qui échoue, valeur refusée par FreeCAD, contrainte refusée par le solveur car en conflit, redondante ou mal formée...). Dans sa branche *Utilise*, certaines lignes peuvent apparaître :
   - en **orange** : la valeur qui provoque l'erreur, par exemple une cellule qui contient du texte là où un nombre est attendu ;
   - en **orange italique** : quand la macro ne sait pas quelle valeur est en cause (division par zéro, longueur nulle...), elle affiche toutes les valeurs utilisées ; l'une d'elles provoque l'erreur, il faut les vérifier une par une.
4. **Aller à la source** : double-cliquez sur la ligne en orange ou en rouge gras pour ouvrir la cellule dans son tableur, la propriété, ou la contrainte dans son esquisse. Si *Zoom sur contrainte* est cochée, la vue cadre la contrainte dans son environnement. Un double-clic sur l'expression d'une ligne sélectionne ce qu'elle utilise.
5. **Corriger** : dans FreeCAD comme d'habitude (tableur, fenêtre des propriétés, esquisse), ou directement dans l'arbre de la macro (colonne Expression). Si vous faites la modification dans l'arbre de la macro et qu'il en résulte une erreur FreeCAD, la macro vous prévient et vous propose d'annuler la modification.
6. **Vérifier** : cliquez sur le bouton refresh. Quand plus aucune ligne n'est rouge, les erreurs sont résolues.

**Esquisse qui ne se résout plus :** ouvrez l'esquisse, sélectionnez la ligne, le cercle ou le point concerné, puis lancez la macro (ou cliquez sur refresh). Toutes les contraintes de ces éléments sont sélectionnées dans l'esquisse, et l'arbre montre de quelles cellules et propriétés dépend chacune : on voit vite quelle valeur du tableur a changé. Les contraintes refusées par le solveur sont en rouge gras.
