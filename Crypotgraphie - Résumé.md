# Crypotgraphie - Résumé 

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





Note : Dessiner échange de clef DH avec certificat

