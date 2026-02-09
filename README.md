# cisco-configs
Un guide pour configurer vos anciens téléphones IP Cisco en SIP

Les anciens téléphones Cisco comme la série 79xx sont un peu compliqués à enregistrer sur des systèmes basés sur SIP.
Il est important d’avoir un fichier de configuration valide, d’utiliser les bons ports avec les bons protocoles pour éviter les problèmes...

## Protocoles

Ces anciens téléphones Cisco préfèrent largement le protocole TCP. UDP est à éviter.
De mon côté, impossible d'enregistrer un téléphone en utilisant le protocole UDP.

## Ports

J’utilise le port 5160 pour le SIP en TCP.
Vous pouvez choisir n’importe quel port, mais je recommande le 5160 car c’est un port couramment utilisé.

## Fichiers de configuration et mise en place

Vous aurez besoin d’un serveur TFTP, afin que votre téléphone puisse récupérer le fichier de configuration.
Le fichier de configuration doit être nommé de la manière suivante :

`SEPMAC.cnf.xml`

où MAC correspond à l’adresse MAC de votre téléphone.
Si mon téléphone a l’adresse MAC 00:37:6C:E2:EB:62, le nom du fichier sera :

`SEP00376CE2EB62.cnf.xml`

J’ai fourni quelques modèles de configuration pouvant être utilisés pour des téléphones spécifiques.
Ils fonctionnent très bien. Ces modèles ont été récupérés depuis cette repository :

`https://github.com/staskobzar/cisco_prov`

## Points importants dans le fichier de confguration 

Dans le paramétrage de "Line 1", le proxy doit être défini sur *USECALLMANAGER* pour utiliser les paramètres IP mis plus haut, au début du fichier. Sinon, ça ne marchera pas.
Le "TransportLayerProtocol" doit être défini sur 1 pour utiliser TCP.
Toutes les références a 5060 doivent être changées pour utiliser le bon port SIP si ce n'est pas le même (dans mon cas j'ai changé en 5160)
