# Crypotgraphie - Final 2018 

### Midterm 2018 Bad HMAC

#### 1. SSL/TLS 

###### 1.

On reçoit le certificat de _www.debian.org_ notre navigateur vérifie qu'il est conforme en vérifiant entre autres la date de validité, la chaine de certification et la signature. Ensuite le handshake est fait avec Diffie-Hellman en utilisant les courbes eliptiques. L'encryption se fait avec AES en mode GCM et le hash pour authentifier les messages avec SHA256.

###### 2.

La vérification du certificat (dans son ensemble) permet d'authentifer le site. Ainsi l'on sait avec qui l'on communique. Comme la communication est signée on sait que les échanges proviennent bien du site cela empêche un MITM actif. Mais HTTPS garantit aussi que la communication est chiffré (symmétrique) donc cela empêche aussi un MITM passif (il ne peut pas comprendre l'échange).

###### 3. 

Comme l'app ne vérifie pas le sujet il est possible de faire une attaque de type MITM. Il suffit d'avoir un certificat valide avec lequel on s'authentifie a l'utilisateur de l'app et au site. On fait ensuite le lien entre les deux. 

#### 2. Fault Attack sur les signatures RSA

###### 1. 

Pour signer un message $ m $ on doit faire $m^d$ mod $N$ or comme $N$ est un grand nombre on peut accélèrer grandement les calculs en calculant en deux fois, une fois $s_p = m^d \pmod p$ et une fois $s_q = m^d \pmod q$ puis calculer $s$ avec le theorème des restes chinois. $s \equiv s_p (q^{-1} \pmod p )q + s_q (p^{-1} \pmod q )p \mod N $

###### 2. 

-- A completer

###### 3. 

On choisit $s$ une signature , $s^e = m$ donc on a une signature valide correspondant à un message (qui ne veut rien dire). On prends une signature tronquée lors du calcul de p grâce au device en entrant $m$ comme message, ce qui nous donne $s'$. Ensuite comme dans le labo on prends $gcd(s'-s,N) = q$

###### 4.

Pour rappel 

* black box accès à un oracle de chiffrement par exemple
* grey box droit en plus à des infos sur l'implémentation
* whitebox accès à tout 

Donc c'est entre grey et white box ? Pas sur de cette réponse. 



#### 3 Chiffrement d'El Gamal

####  4 CBC-MAC

###### 1 CBC-MAC fonctionne 

On utilise CBC avec un algorithme de hashage ($E_k$) , un message $m$ est découpé en bloc de taille fixe ($m_0,m_1,...m_n$) le hash produit vaut $E_k(...E_k(E_k(m_0) \oplus  m_1) \oplus m_2...\oplus m_n)$ 

Il faut faire attention car étant donné un message $m$ et un hash $\tau$ on peut trouver une collision avec les message $m || m \oplus \tau $ 

ou bien utiliser un padding ou l'on ajoute la taille du message au début du premier bloc. 

(Il faut faire attention a utiliser un IV à l'entrée et ne **jamais** réutiliser un IV.)

#### 6 PRNG

###### 1.  

* Efficacité : Fonction de hashage sûre implique répartition uniforme sur la sortie, sauf qu'on se fixe aucune condition pour le nomre à tester et qu'il y'a une forte chance qu'aucun soit premier. Donc autant tirer directement un nombre de 512 bits.
* Sécurité : Keylenght recommende 2048 bit donc faible, en plus on est pas sur que le premier trouvé fasse partie des "premiers sûr". (pas de la forme 2p + 1 ou p est premier) (valable pour tous).

###### 2

* Efficacité : Si la dernière pièce de monnaie vaut 0 on a tiré 512 pièces pour rien. Donc pas efficace. Et cribe pas efficace du tout. 

* Sécurité : 512 trop court, sinon c'est mieux si c'est un nombre premier sur. 

###### 3 

* Efficacité : c'est pareil que 1 donc nul. (encore pire que 1)
* Sécurtité : entre deux nombre premier c'est toujours les mêmes nombres generé donc très très mauvais. (exemple si entre 1800 et 2000 on a un seul hash valide, on a pendant 200 ans le même nombre premier)

###### 4 

Une idée serait de génèrer aléatoirement un nombre n bit, mettre le LSB et le MSB à un puis tester avec miller-rabin. 

#### 7 Choix de Primitives

###### 1. 

Il faut utiliser HTTPS (SSL/TLS 1.3) (certificat et chiffrement) comme ca il ne peut pas y avoir de MITM attaque.

###### 2. 

Elles doivent envoyer les données ainsi que le hash des données, et aussi s'authentifier (on a besoin de CIA ) donc utilisez une certificat signé à l'aide du certificat de l'entreprise par exemple des deux côté et il faut envoyer un hash des données. 

###### 3. 

Il faut qu'il fasse signer un certificat par une autorité de certification avec lequel il signe ses emails. 

###### 4. 

Il faut qu'ils utilisent une tierce personne de confiance (une ROOT CA par exemple) pour faire une ECDH ensuite et avoir un secret partagé.