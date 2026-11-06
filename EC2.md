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
7. **USER DATA**:
   - Les user data est un inscript qui est défini avant la création d'un EC2 pour que ce script soit executé au lancement de l'instance EC2
   - Le script peut être pour l'installation d'une librairie, d'un server etc...
