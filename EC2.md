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
5. **
