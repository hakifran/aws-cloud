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
## Conteneurs sur AWS
1. **AWS ECS: Elastic Container Service**: Il faut savoir qu'une fois les conteneurs créés, il faut des outils de gestion et d'orchestration de ces derniers. AWS ECS est un service de AWS entièrement géné qui permet à la fois de d'orchestrer et de mettre à l'échelle les conteneurs en fonction de la demande en capacité.**ECS** s'integrer avec d'autres services AWS tel que **EC2, Fargate, Auto scaling, AWS IAM**
2. **AWS EKS: Elastic Kubernetes Service**: EKS est un autre service de gestion d'orchestration des conteneurs DOCKER à la seule difference avec ECS est que EKS crée des **clusters kubernetes** dans lequels il gére les conteneurs DOCKER.
3. **AWS Fargate**: Il faut savoir que les services d'orchestration vont gérer des conteneurs qui tourne sur de l'infrastructure qui est soit gérer par l'**EC2** ou par **Fargate**. Donc **Fargate** permet la gestion de l'infrastructure sur lequel tourne les conteneurs. Fargate étant **Serveless** on n'a pas besoin de provisionner et gérer quoi que ce soit, **Fargate** s'en n'occupe à notre place.
4. **AWS ECR: Elastic Container Register**: Les conteneurs sont créés à partir des **Images** et les images sont stockés, versionnés et gérés dans un registre à partir duquel on peut avoir une image. Donc ECR permet de stocker, versionner et gérer les images comme **Docker hub**.

## Serverless & AWS Lambda:
1. **Serverless(Sans serveur en francais)**: est un concept de développement et de déploiement d'application qui se fait sans géstion directe des serveurs.
2. **AWS Lambda**: est service AWS qui est serverless mais il faut s'avoir qu'il y a d'autres services AWS tel que AWS lambda, AWS S3, AWS API Gateway(pour la création des API HTTP). AWS Lambda est constitué de **fonctions** qui répondent à des évenements(**Appel HTTP, l'upload d'un fichier dans AWS, etc...**). Lorque AWS lambda reçoit un évenement il crée automatiquement un conteneur dans lequel il va éxecuté la fonction invoqué, une fois l'éxecution terminé il detruit le conteneur. 
4. Voici une explication plus détaillée de ce que signifie le serverless sur AWS :
   - **Absence de gestion de l'infrastructure**: Avec serverless vous n'avez plus à vous soucier de la gestion de l'infrastructure sous-jacente. AWS s'occuper automatiquement de gérer, faire des mises à jour, mettre à l'échelle, faire des correctifs. On n'a plus qu'à se concentre sur le développement de nos applications
   - **Évolutivité automatique**: Avec les services Serverless, ils adaptent automatiquement les ressources à la charge sans qu'il y ait intervention de l'humain. Quand la charge augmente le Serverless décider d'augmenter les ressources et quand il diminue il reduit les ressources.
   - **Paiement à l'utilisation**: Il faut savoir que le paiement pour les services Serverless se fait par invocation et la durée de l'éxecution du code et cela par millesecond
   - **Diversité des services Serverless**: Il existe d'autre type de services serverless notamment AWS S3, AWS SQS(Simple Queu Servive), AWS Lambda, AWS API Gateway...
   - **Facilité de développement**: On n'est plus soucié de l'infrastrure sur lequel va tourner nos applications mais plutot on se concentre sur le code et son évolution.
  
## AWS lightsail:
 - **LightSail** est un service AWS qui permet de déployer des applications d'une façon simpliflié(en quelques clics) via des **VPS(Virtual Private Server)
 - **LightSail** permet de déployer:
   - Des **applications**: Wordpress, Drupal, Joomla, Magento, prestashop ...
   - Des **ressources**: Des Serveurs Linux/windows, Base de données, conteneurs stockage, stack Lamp(Linux Apache, mysql et PHP)
 - **LigthSail** est déstiné:
   - Au utilisateur non techniques ou qui débute sur AWS
   - Au utilisateur qui ne veulent pas gérer l'infrastructure
   - Au utilisateur qui veulent déployer des applis en quelques clics
   - Au petit entreprise
 - La tarification **LightSail** est horaire et abordable selon des forfaits(sur la capacité(CPU, RAM, réseau)
