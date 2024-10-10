# TP1 
## Quel type de cloud pour quels besoins ?

> Cas n°1: Eldo est une start-up qui développe un logiciel qui a pour objectif la mise en relation de professionnels du BTP avec des prospects qui souhaitent faire des travaux chez eux. En plus d’un module de mise en relation, Eldo développe un CRM pour les professionnels du BTP.

Pour le cas d'Eldo, la solution la plus adaptée serait du PaaS.
Le PaaS car la société est jeune, possède assez peu d'employé et developpe une solution logiciel.
La gestion d'un PaaS est réduit si managé et offre un coup réduit par rapport a une equipe Cloud.
Je conseil un EKS, AKS ou GKE si les developpers sont commun de la conteneurisation et un ROSA ou ARO si ce genre de transition est a venir ou est en cours.

Price: 500$ - 15000$

> MySecureProtect est une entreprise qui développe et exploite des objets connectés en lien avec la sécurité des habitations des particuliers. Plus d’un million d’objets connectés sont en liaison constante avec les serveurs de l’entreprise. Une application mobile permet de gérer son système de sécurité et de recevoir des notifications en cas d’anomalies. La spécificité de ce système est qu’il sollicite les serveurs dans 3 cas bien précis. Le matin lorsque les personnes quittent le domicile pour activer l’alarme, le soir pour désactiver l’alarme et enfin dans de rare cas lorsqu’une anomalie de sécurité est détectée.

Pour cette société, je pense que le IaaS est adapté, cependant j'y ajouterai un forme de FaaS afin d'ajuster les actions effectuées. 
Le IaaS supporte la majorité des options sous l'egide d'un pool manager (gestion horizontale de la charge) et le FaaS pour le declanchement de reponse aux anomalies (alerting etc...)

Si l'entreprise souhaite apporter de la transportabilité a sa solution, la conteneurisation peut etre pertinente; tout en y ajoutant de la reponse aux evennements. Je pense a de l'EKS (ou autre) avec du KubeEdge, du KEDA et une Stack d'obeservabiliter pour l'alerting. Certe cela demande de la compétence et de l'investissement mais l'entreprise peut changer de plateforme simplement ou evoluer a la volée si besoin (HPA, VPA, CA). Une fois le processus mit en place, du GitOps permet de gérer de facon automatique les deploiements des outils en cas de changement de provider

Price: 500$ - 25000$

> Cas n°3: Paul est un particulier de 37 ans qui souhaite reprendre le contrôle de ses données. Il fait beaucoup de photos et apprécie pouvoir les stocker à un seul endroit mais y accéder depuis de nombreux appareils. Il dispose d’environ 800 Go de données et son besoin en stockage évolue relativement peu. Les compétences en informatique de Paul sont limitées

Je propose à Paul de passer sur un SaaS, tel que DropBox ou Kdrive. 
Pour une somme assez faible il pourra avec un simple accéder à toutes ses photos. Cependant il n'aura jamais vraiment le controle de ses données, il peut evisager de repasser on-prem (un nas Synology) mais limitera la resilience de ses photos

Price: 5$ - 1500$

> Cas n°4: Une grande entreprise française de soutien aux armées du pays, accréditée par le ministère des armées et dont le nom est confidentiel, a besoin de moderniser ses infrastructures informatiques.Les besoins en termes de diversité de service, de quantité de serveurs, stockages et réseaux évoluent très rapidement.

Je proposerai d'avoir un Cloud Hybrid, et un melange des trois niveaux de responsabilité (IaaS, PaaS et SaaS). Je pense à de l'Openstack ou du NSX dans pour du Cloud Privé, qui contiendra l'ensemble des services dit critique (notamment le stockage -> Ceph <3) et une utilisation limitée et controlée d'un cloud provider publique certifié SecNumCloud pour la partie Elastique de l'infrastructure.

Price: 10.000$ - 500.000$

> Cas n°5: TheFoodStore est une petite entreprise qui cherche à publier un site e-commerce rapidement afin de générer ses premières ventes en ligne

Un SaaS. La seule soolution pertinente en terme de prix et de charge.
Shopify est un bon example.

Price: 40$ - 400$

> Cas n°6: DeliverEats est une plateforme permettant de commander et se faire livrer des repas. Elle dispose d’une application mobile et d’un site internet pour passer commande. Les livreurs de commandes disposent d’une application mobile qui les guide dans leurs livraisons,tandis que les restaurateurs reçoivent les commandes à préparer sur une application pour tablette.

Je propose un ensemble de IaaS, PaaS et SaaS.
IaaS pour les besoin d'infrastructure de support (CMDB, ELK...) ou des besoins de calcul spécific (eGPU, Baremetal...), PaaS pour l'Applicatif principale notammentau travers de K8s (microservice) et du SaaS pour les service a haut potentiel de de changement de charge ou avec des exigences de performance (DynamoDB, Lambda...).
On peut envisager un Backup sur un second provider suivant les besoins.

Price: 500$ - 1.500.000

L'avantage c'est l'adaptabilité et l'evolutivité.
les inconvénients sont le prix, la complexité et la dificulté de transportabilité entre les providers.


> Cas n°7 : L’entreprise de télévendeurs Onenveutpa a besoin d’un nouveau système pour la gestion des informations de ses potentiels futurs clients. Les télévendeurs travaillent partout dans le monde.

Un SaaS. Disponible partout tout le temps et clé en main.

Price: ~2000$