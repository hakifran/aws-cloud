# Le Cloud Computing
- Le cloud computing a une mise à la disposition des resources et services informatiques à la demande via internet, avec un paiement à l'usage(pay as you go).
- Modèle de déploiement:
  #### - Cloud public(aws, azure ou GCP)
  #### - Cloud privé(une entreprise qui possède ses propres resources(data center) qu'il ne loue pas. Il faut anticiper la capacité dont l'entreprise aura besoin dans le futur)
  #### - Cloud hybrid(une entreprise qui possède ses propres resources mais qui a un certain moment il n'a plus la capacité dont il a besoin et donc il décide d'utiliser le cloud public pour par exemple deployer certaines de ses applications). Dans certain cas une entreprise utilisant le cloud hybrid il aura besoin du VPN ou de la connexion direct pour que ses applications puissent communique(c'est-à-dire celle qui sont sur le privé et celle qui sont sur le public)
# Modèles et types de Cloud
  ## On premises(sur site):
    - Tous est géré par l'entreprise:
      - Gérer le materiel
      - Gérer l'installation du SE
      - Gérer la virtualization 
      - Runtime
      - Middleware
      - Gérer les applications
      - Gérer le réseau de ses serveurs
      - Gérer le stockage
  ## Infrastructure As A Service(IaaS)
    - L'entreprise gère seulement:
      - SE
      - Data
      - Middleware
      - Application
  ## Plateform As A Service(PaaS)
    - L'entreprise gère seulement:
      - Les Applications
      - Les Data
  ## Software As A Service(SaaS):
    - L'entreprise ne fait que s'enregistrer sur la SaaS seulement et l'utilise.

# Les avantages du Cloud
  ## Payement à l'usage(CAPEX(CAPital EXpenditure ---to--> OPEX(OPeration EXpenditure):
  - Remplace le CAPEX par l'OPEX en payant simplement ce que vous utilisez avec le cloud, au lieu d’investir massivement dans des centres de données.
  ## L'économie d'échelle: 
  - Les fournisseurs cloud(AWS) qui ont des centaines de milliers de clients, cela à une impact sur les prix qui diminuent grâces à la réalisation des économies plus importantes et favorise des prix   inferieurs **Pay-As-You-Go**.
  ## L'Elasticité:
  - On n'a plus besoin de deviner les resources nécessaires et avoir des capacités non exploités. Avec le cloud on utilise les resources dont on a besoin et on peut les reduires ou les agrandir selon le besoin
  ## Agilité et Flexibilité:
  - Avec le onpromise, pour créer ou ajouter une resource ça prend énormement de temps alors que avec le cloud c'est avec un seul click. Donc avec le cloud le délai pour ça est de quelques minutes alors qu'avec l'onPromise c'est une question de nombreux semaines
  ## L'Innovation: 
  - Avec le cloud on arrete de dépense de l'argent et du temps sur l'infrastrure, plutot on se concentre plus sur nos projets ce qui permet d'innover nos projet parce qu'on a plus de temps.
  ## Déploiement mondial en quelques minutes: 
  - Les fournisseurs cloud ont des serveurs partout dans le monde(Dans toutes les regions), ce qui permet d'avoir une visibilité rapide au niveau mondiale et vous permettent de déployer facilement vos applications dans plusieurs régions d’un simple clic.

# Introduction au cloud AWS
  ## Présentation d’AWS
  - **AWS(Amazon Web Service)** est une plateforme de service du cloud computing offert par **AMAZON** et permet de payer uniquement les services que l'on utilise
  - Cette plateforme offre une game de services du cloud computing:
    - Stockage des données
    - Traitement des données
    - La securité
    - La mise en réseau
    - La livraison de contenu
    - L'Intelligence Artificielle
    - Les outils de développement et de déploiement d'applications
  ## L’Infrastructure globale
  - Il faut savoir que AWS possede des centres de données qui regroupe dans des **régions**.
  - **Une région** est un emplacement physique sur lequel on peut déployer des applications ou stoquer des données.
  - AWS possède plusieurs régions sur toutes l'étendu du globe.
  - Une région est composé de **zones de disponibilités(Avaibility Zone)**, dans la plus part des cas elles(AZ) sont au nombre de 3(minimum) pour une région
  - Une **Zone de disponibilité(Aivability zone)** est un centre de donnée(Data Center) à part et independant. Les zones de disponibilités dans une même région sont éloignés les uns des autres pour question de sécurité. Pour que si une d'entre elles a un soucis pour que les autres prennent la releve
  - AWS a aussi des **Edges Locations** qui jouent le rôle de cache pour diminuer le temps de latence. Les Edge Location sont placé partout dans le monde pour permettre de faire du caching des applications déployées dans les régions.
  - Il existe aussi des **zones locales**. Les zones locales sont de mini-data-center qui sont placées tout près des métropoles(Zones très habitées et où il y a de forte activité économiques) pour permettre à ces métropoles d'avoir accès au services offertes par AWS avec moin de latence.
  - **Les critères à prendre en compte pour choisir une région**:
    - **Latence**: Il faut choisir la région qui soit la plus proche de la population cible pour réduire au maximum le temps de latence
    - **Prix**: Les prix des services offerte par AWS varient selon les régions
    - **Disponibilités des services**: Les services ne sont pas disponibles dans toutes les régions. Pour un service donnée, elle peut être disponible dans la région A et ne pas l'être dans la région B.
    - **Conformité**: la réglementation peut vous obliger à localiser vos données dans une zone géographique précise
     

    
      
