![1.1](1.1.png)

Ce sont les clés publiques qui doivent être authentifiées. Les éléments principaux sont la date de validé, un sujet correct ainsi qu'une signature valide (et la chaîne de signature).

![image-20200202212835642](image-20200202212835642.png)

// un dessin

![image-20200202212849717](image-20200202212849717.png)

L'attaquant peut se faire passer pour s auprès de c, et signer une nouvelle clé symétrique. Cela n'implique cependant rien pour les échanges précédents s'ils ont été enregistrés.

![1.4](1.4.PNG)

Il doit faire révoquer le précédent certificat (au plus vite) puis ré-établir un canal asymétrique garantissant l'authenticité.



![2.1](2.1.PNG)

On sait que `vk / vs = format(mk) / format(sg)` et on connaît la fonction format ainsi que *sg* donc on peut simplement déduire `mk = vk / (format(sg) * vs)` et on a récupéré la clé.

![2.2](2.2.PNG)

On a simplement incrémenté *a* donc on peut faire `mk = vk / (vs * format(sg) * Yg)`

![2.3](2.3.PNG)

Le chiffrement d'El Gamal est **non déterministe** donc on ne peut absolument rien en dire (chouette !)



![3.1](3.1.PNG)

Ici la connexion est en HTTP donc il n'y a pas de sécurité, le site peut très bien avoir été modifié. Ici il faudrait une connexion HTTPs qui permettrait d'établir de la sécurité basée sur un tier de confiance.

![3.2](3.2.PNG)

Les points sont O, (0;2), (0;3), (1;0), (3;1) et (3;4)

![3.3](3.3.PNG)

On calcule les coordonnées via la formule, on trouve le point (3; 1)

Dès qu'on trouve X = 3, on peut en déduire Y = 1 car on part déjà du point (3;4).

![3.4](3.4.PNG)

Si la clé privée vaut 4 alors la clé publique vaut 4 * G, puisque G à un ordre de 6 alors on sait que 6 * G = G et que 5 * G = O

On peut donc trouver la clé publique en faisant O - G, soit -G, soit (3;1) 

![4.1](4.1.PNG)

![4.2](4.2.PNG)

![4.3](4.3.PNG)

![4.4](4.4.PNG)

![5.1](5.1.PNG)

Le plus simple me semble de chiffrer le disque dur du serveur.

![5.2](5.2.PNG)

On implémente un système de signatures, par exemple on pourrait stoquer un MAC qui serait un hash du nom d'utilisateur ou quelque chose du genre pour pas être trop lourd.

![5.3](5.3.PNG)

On fait simplement un formulaire d'enregistrement web (bien sûr implémentant HTTPS pour que la connexion soit chiffrée) et on stoque le hash du mot de passse utilisateur dans la base de données avec le username de ce dernier. Pour la connexion, on hash le mot de passe qu'il envoie et on compare avec la valeur dans la base de données.

Je pense que SHA256 ça suffit pour le hash et on utilise X.509 pour le certificat.

![6.1](6.1.PNG)

![6.2](6.2.PNG)

![7.1](7.1.PNG)

![7.2](7.2.PNG)