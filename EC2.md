# Démarrer avec Amazon EC2
## Amazon EC2 (Elastic Computer Cloud). C'est une instance(serveur de calcul) EC2:
- C'est un service permettant de louer des serveurs virtuels
- C'est EC2 qui permet de créer des serveurs virtuels qui s'execute sur des serveurs physique
- Avec EC2 on paie uniquement le temps(en Secondes) que l'on utilise l'instance
- Avec EC2 on peut choisir:
  - Le système d'exploitation
  - Le processeur: Intel, AMD, Graviton(Arm)
  - La facturation est à la seconde ou à l'heure par défaut
- Les cas d'usage de EC2:
  - Héberge un site web
  - Héberge des applications: CRM, ERP, base de données
  - Stockage et traitement des données.
## Les caractéristiques d'une instance EC2:
1. **Balises(Tags)**:
   - Les tags sont des metadatas qui permettent de classe et d'identifier une instance EC2
   - Par exemple le tag **name** pour donner le nom à l'instance ou **environnement** qui peut être dev ou production
   - Les tags sont en key/value c'est à dire clé et une valeur.
   - Les tags peuvent être utilisés pour une instance EC2 donnée de suivre l'évolution des montants pour son usage
2. **AMI (Amazon Machine Image)**:
   - Un AMI est un template à partir duquel on peut lancer une instance EC2
   - Un AMI est produit à partir d'une instance EC2 déjà existante et cet AMI peut être utilisé pour lancer plusieur autre Instance EC2 qui seront toute simulaire
   - Un AMI peut être fourni par AWS, par des contributeurs ou peut être vendu
   - UN AMI peut être privé si c'est un utilisateur qui la crée à partir de son instance EC2 et peut être public quand il est publié pour achat ou gratuitement obtenu auprès de AWS(les contributeurs)
3. **Type d'instance**:
   - Les types d'instance permettent de définir, le nombre vCPU, la taille de la RAM, le type de stockage et la performance réseau
   - Toutes ces caracteristiques sont regroupés dans des packages qu'on appelle des types d'instance
   - Un type d'instance est choisi selon la taille des calculs que l'instance aura à executé. Il faut faire attention parce que selon la taille du vCPU, RAM etc...les prix augmentent
   - Il faut aussi savoir que le prix des type d'instance varie selon les régions sur AWS
   - **Il est possible de change le type d'instance selon que les besoins en capacités ont augmentés ou diminué. Pour cela il faut le stop imperativement et le redemarrer après le changement du type**
4. **Adresse IP**:
   - Il faut savoir qu'une instance EC2 sur un serveur virtuel se trouve dans un subnet(sous-réseau), et le subnet se trouve dans un VPC(Virtual Private Cloud)
   - A l'interieur du VPC-subnet le EC2 est identifier par une adresse IP privée qui ne change pas et qui permet à ce dernier de communiquer avec les autres EC2 se trouvant dans le même VPC.
   - Cette adresse privée ne permet en aucun cas au EC2 de communiquer avec l'exterieur(internet). Pour communiquer avec l'exterieur(internet) une adresse publique lui est alloué mais ce dernier change si par exemple l'instance EC2 est redemarrée. Pour éviter que cette IP publique ne change pas à chaque fois une **Elastic IP adress** lui est alloué et ce dernier ne change pas.
5. **Paire de clés(Key pair)**:
   - Pour pouvoir accèder à une instance EC2 via **SSH(Secure Shell)** pour linux ou **RDP(Remote Desktop Protocol)** une paire de clé est nécessaire pour l'authentification:
     - Clé privée que l'utilisateur va sauvegarde jalousement car elle est très sensible en terme de sécurité pour l'instance EC2
     - Clé public qui est sauvegardé dans l'instance EC2
     - Pour linux, l'utilisateur fourni la clé privé à la commande SSH et l'instance EC2 se charge de vérifier si la clé privé correspond à la clé publique dans l'instance EC2
     - Pour windows, le clé privée est fourni par l'utilisateur et avec le clé publique ça permet de déchiffre le mot de passe pour pouvoir accèder à l'EC2
6. **Groupe de Sécurité(Security Group)**:
   - Pour des raisons de sécutité pour l'instance EC2, une sorte de parefeux(Firewall) est obligatoire pour gérer les flux(**Inbound**) qui entrent et les flux(**OutBound**) qui sortent
   - Pour ce faire une liste de règles(**Rules**) est établi afin de controller au mieux les flux entrant et les flux sortant de l'instance EC2
   - Les Rules sont composés:
     - Type: SSH, HTTP, HTTPS, etc...
     - Protocol: TCP, UDP, etc...
     - Ports
     - Source: Les adresses IP, si cette valeur est 0.0.0.0 cela signifie que toutes les adresses sont permises d'envoyer des requettes
   - Les groupes de securités ne supportent que les règles **ALLOw** alors que **Deny** est implicite
   - **Il possible de modifier un groupe de sécurité(enlever ou ajouter) sans toute fois stop et redemarrer l'instance EC2**
7. **USER DATA**:
   - Les user data est un inscript qui est défini avant la création d'un EC2 pour que ce script soit executé au lancement de l'instance EC2
   - Le script peut être pour l'installation d'une librairie, d'un server etc...
## Tarifications:
 1. **Offre gratuits**:
    - AWS met à la disposition certains services gratuits à un nouveau abonné pour une durée de 12 mois
    - Il faut savoir que la limite de la gratuite est de 750 heures par mois, une fois les 750 heures gratuits utilisés, AWS commence à facture l'excédent
    - Après les 12 mois AWS commence à facturer tous ses services une fois utilisé
    - Cas d'utilisation:
      - Pour tester les services
 2. **On demand(Pay as you Go)**:
    - Pour ce genre de tarification l'abonné ne s'engage en rien, il utilise les services de AWS sans engagement
    - Et AWS facture l'utilisation des ses services par sec ou par heures(paiement à la seconde ou à l'heure)
    - Cas d'utilisation:
      - Pour des projets dont l'utilisateur ne veut pas s'engage avec AWS
      - Les charges de travail à court terme ou imprévisible
      - Les applications développées ou testées pour la 1ere fois.
 3. **Savings plans**:
    - Pour ce genre de tarification l'abonné s'engage et signe un contrat avec AWS pour l'utilisation de ses services
    - Avec ce dernier une reduction de 72% par rapport à **on demand**
    - L'engagement se fait sur 1 ou 3 ans
    - L'engagement est mesuré en $/heure
    - Les options de paiement sont: No Upfront(pas de paiement du tout à l'avance), partial upfront(une partie à l'avance et l'autre durant l'utilisation), all upfront(paiement tout à l'avance)
    - Recommandé pour:
      - application en production avec une utilisation stable
      - Base de donnée avec usage constant
  4. **Dedicated hosts**:
     - Les dedicated hosts permettent de louer un serveur physique qui soit exclusivement dédié à un compte AWS
     - Les dedicated hosts permettent d'avoir le contrôle sur le placement des instances EC2 sur le serveur
     - ça permet aussi d'avoir la visibilité sur nombre de sockets et de coeurs physiques
     - Recommandé pour:
       - Utilisation de licences logicielles existantes par socket, core ...(Windows Server, SQL server, RHEL, ...)
       - (Conformité) charges de travail qui requièrent des serveurs physiques dédiés.
  5. **Instances spot**:
     - Sur les serveurs AWS il advient qu'il y a de l'espace non utilisé d'instances EC2 non utilisé
     - Alors AWS les mets au enchère pour l'utilisation de cette espace(charge non utilisé) et les clients de AWS peuvent proposer les prix pour les loués pendant une certain temps.
     - Les prix sont réduits à plus de 90% par rapport au tarif de l'on-demand
     - Mais ça une inconvenient car à tout moment AWS peut décider de reprendre l'espace(Spot) loués et un temps de 2min de notification est donné au client avant de remprendre l'espace spot alloué
     - Recommandé pour:
       - Les applications tolérantes aux interruptions / pannes
       - Applications non critiques: Big Data, CI/CD, environnements de tests
## EC2 AutoScaling & Elastic Load Balancer:
  1. **Scalability(mise à l'échelle)**:
     - La mise à l'échelle(Scalability) est la capacité d'un système, d'un logiciel à s'adapter à l'augmention ou à la diminution de la charge de travail sans interruption ou panne.En d’autres termes, la scalabilité est la capacité d’un système à évoluer de manière transparente pour répondre aux besoins croissants de ses utilisateurs sans subir de perte de performance ou d’interruption de service.
     - Il existe deux sorte de mise à l'échelle(scalability):
       - **Scalability verticale**: on augmente la taille(capacité) d'une instance
       - **Scalability horizontale**: On ajouter les instances pour gérer des charges de travail plus importantes.
  2. **Haute disponibilité**:
     - La haute disponibilité est la capacité qu'a un système à rester disponible et à fonctionner normalement même en cas de défaillance matérielle ou logicielle
  3. **EC2 AUTO scaling Group**:
     - L'EC2 Auto Scaling Group est un outil de AWS qui permet d'ajuster automatiquement le nombre de serveurs en fonction de la charge de travail. Il permet d'ajouter ou de supprimer des serveurs selon que la charge de travail est accrue ou réduit
     - La configuration de l'EC2 auto scaling se base sur trois nombre:
       - **La capacité souhaité**: c'est le nombre de serveur dont on pense qu'il va permettre à un site web de bien fonctionner
       - **La capacité maximale**: C'est le nombre de serveurs maximale qu'il faudra avoir en cas d'accroissement de la charge
       - **La capacité minimale**: C'est le nombre de serveurs minimal qu'il faut garder en cas de réduction de la charge de travail
       - L'auto scaling group peut aussi parametre un nombre fix de serveurs qu'il faut toujours garder c'est à dire que dans un cas où un serveur est en panne l'auto scaling group est capable de détecter ça et de remplacer automatiquement le serveur
     - **Les stratégies auto scaling**:
       - **Stratégie dynamique**: On définit une règle qui une fois rempli va déclenche l'augmentation ou la diminution du nombre de serveur par l'auto scaling groug. Par exemple augmenter le nombre de serveurs une fois que l'utilisation du CPU > 90% ou diminuer le nombre de serveurs si le traffic réseau < 20 %
       - **Stratégie prédictif**: L'augmentation ou la diminution des serveurs se base sur des modèles du machine learning qui se basent sur les données historiques de l'utilisation du site web par exemple
 4. **Elastic Load Balancer**:
    - Une fois qu'il y a plusieurs serveurs via l'auta scaling Group, il faut qu'il y est un mécanisme pour repartir la charge de travail entre ces serveurs.
    - L'**Elastic Load Balancer** est un outil mise en place par AWS pour crée des répartiteur de charge entre les instances EC2
    - Il existe 4 type de repartiteur de charge:
      - **Application Load Balancer(Couche 7)**: Http, https. Utilisé plus pour le web
      - **Network Load Balancer(Couche 3)**: TCP/UDP. Utiliser pour répartir rapidement avec une grande capacité
      - **Gateway Load Balancer**: Ils vous permettent de déployer, de mettre à l’échelle et de gérer des appliances virtuelles, telles que des pare-feu, des systèmes de détection et de prévention des intrusions et des systèmes d’inspection approfondie des paquets
      - **Clasic Load Balancer(Couche 4 et couche 7)**:  Il s’agit de la version précédente des load balancers dans AWS, offrant une distribution de charge au niveau de la couche 4 et de la couche 7. Le Classic Load Balancer est déprécié par AWS, qui recommande de plutôt utiliser les autres types.

## Architecture Multi-AZ(Availability Zone):
 - L'architecture Multi-AZ permet d'assurer la **haute disponibilité** d'un système.
 - Le Multi-AZ va y arriver en jouant sur la **redondance** des instances sur differentes **AZ**
 - L'**Auto Scaling Group** a l'intelligence que quand il crée des instances il les places dans des AZ differentes
 - Et l'**Elastic Load Balancer** s'occupe de distribuer la charge entre les differentes instances EC2 se trouvant dans differentes AZ

# Autres services de calcul
## Conteneurs 101
### Qu'est ce qu'un conteneur:
1. Un **conteneur informatique** est similaire à un conteneur physique dans lequel on met tout ce qu'on veut.
2. Les **Conteneurs informatique** permettent de regrouper ensemble du code, des dépendances, des librairies et des fichiers de configuration dans un seul conteneur qui peut être déplacé et executé dans n'importe quel environnement.
3. Contrairement aux machines virtuelles les conteneurs ne duplique pas les resources du système d'exploitation invité mais n'inclue que ce qui est nécessaire pour l'execution de l'application
4. **Machine virtuelle:** Applications ---> binaire/libraries ---> Systeme d'exploitation ---> hyperviseur ---> Infrastructures
5. **Conteneur:** Applications ---> Binaire/libraries ---> logiciel de conteneurisation ---> Infrastructure
### Les Avantages des conteneurs:
1. **Isolation des applications:** Les containers permettent d’isoler les applications les unes des autres, ce qui évite les conflits de dépendances et les problèmes de compatibilité. Chaque application s’exécute dans son propre environnement logiciel, ce qui permet de garantir que les modifications apportées à une application ne vont pas affecter les autres applications.
2. **Portabilité:** Les containers sont portables et peuvent être exécutés sur n’importe quel système d’exploitation qui prend en charge les containers, ce qui facilite la migration des applications entre différents environnements. Les containers sont également plus légers que les machines virtuelles, ce qui permet de les déployer plus rapidement et plus facilement.
3. **L'évolutivité:** Les containers permettent de mettre à l’échelle les applications horizontalement, ce qui permet de gérer les charges de travail élevées de manière plus efficace. Les nouvelles instances de l’application peuvent être ajoutées rapidement et facilement, en fonction des besoins.
4. **Facilité de déploiement:** Les containers permettent de déployer des applications plus rapidement et plus facilement que les serveurs traditionnels. Les containers sont créés à partir d’images, qui contiennent toutes les informations nécessaires pour exécuter l’application. Cela permet de garantir la cohérence entre les environnements de développement, de test et de production.
5. **Facilité de Gestion:** Les containers peuvent être gérés de manière centralisée à l’aide d’outils de gestion de containers tels que Docker, Kubernetes ou Amazon ECS. Cela permet de simplifier la gestion des applications et de garantir la cohérence des environnements.
### Docker
1. **Docker** est une plateforme open source permettant de créer, distribué et executé des applications dans des conteneurs isolés.
2. **Docker** utilise un système de fichiers en couches pour créer des images de conteneurs. Les images de conteneurs sont des modèles qui contiennent toutes les informations nécessaires pour créer un conteneur. Une fois qu’une image de conteneur est créée, elle peut être utilisée pour créer un ou plusieurs conteneurs.
#### CREER UN CONTENEUR DOCKER
1. Un fichier **Dockerfile** qui contient les instructions de comment l'imade docker est formé
2. A partir du fichier **Dockerfile** une **image docker** est créé
3. L'**image docker** est publié sur un registre publique ou privé
4. Et c'est à partir de là que l'image est téléchargé et puis executé en **conteneur docker**
5. **Docker file** ---**build**--> **Docker image** ---**Run**--> **Docker conteneur**
 

      
