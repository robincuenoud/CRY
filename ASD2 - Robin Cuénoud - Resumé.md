# ASD2 - Robin Cuénoud - Resumé

### Terminologie 

Pour un graphe composé de $E$ arêtes et de $V$ sommets

* Taille = $E$ 
* Ordre = $V$
* Graphe simple - pas de boucle pas plus d’une arête par pair de somets
* Multi-graphe - Graphe pas simple..
* Partiel - on supprime quelques arêtes , Sous-graphe - quelques sommets (et arrêtes)
* Complet - tous les sommets sont connectés à tous les autres
* Adjacence si une arête entre deux sommets

### Représentation 

* liste d’arêtes : ajout $O(1)$ nombre de sommets $O(1)$ sommets adjacents en $O(E)$ Pas efficace

* matrice d’adj : ajout $O(1)$ nombre de sommets $O(1)$ sommets adjacents en $O(V)$ Pas efficace si creux

* liste d’adj : ajout $O(1)$ nombre de sommets $O(1)$ sommets adjacents en $O(degré(V))$ (souvent $d(V) < V$)

  

### Parcours







### B-ARBREEEES

jusqu'à $2m$ éléments dans une page , chaque page peut être racine d’au max $2m + 1$ éléments. Complexité d’accès est pour $n$ éléments $O(log_m(n))$, nombre max d’éléments $n = 2 \cdot m \cdot \sum_{i=1}^{h} (2 \cdot m + 1)^{i-1} $ 

Propriétés : toutes les pages contiennent au plus $2m$ éléments, au moins $m$ éléments sauf la racine qui contient au moins un. Une page est soit internet et possède au plus $2m+1$ fils soit une feuille. Un page interne contenant k éléments possède $k+1$ fils. Les éléments d’une page sont triés selon leur clé. 

##### Insertion d’un élément:

Toujours dans une feuille (jamais page interne car feuille tjr au même lvl)

Si non pleine on la mets dedans, si pleine exploser la feuille et remonter la médiane comme clef. Si racine pleine éclatement de la racine et la médiane remonte. 

##### Suppression d’un élément:

* Consolidation si suppression laisse moins de m éléments dans une page (déficitaire).

  Pour ca soit rotation (droite ou gauche) soit fusion (droite ou gauche) de la page déficitaire et d’une page voisine. (élément paire impliqué)

  Chaque rotation transfère un élément père de la page mère dans la page déficitaire, puis un élément d’une page voisine (gauche ou droite selon la rotation) de la page déficitaire dans la page mère, à la place de l’élément père.

  Chaque fusion réunit la page déficitaire avec un élément père et une page voisine (gauche ou droite selon la fusion) et décale les éléments de la page mère. :warning:  possible que page mère soit **déficitaire** donc on doit consolider et ainsi de suite.  