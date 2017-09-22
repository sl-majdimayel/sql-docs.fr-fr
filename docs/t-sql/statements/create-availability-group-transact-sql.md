---
title: "CRÉER le groupe de disponibilité (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AVAILABILITY GROUP
- CREATE_AVAILABILITY_TSQL
- CREATE_AVAILABILITY_GROUP_TSQL
- CREATE AVAILABILITY GROUP
- CREATE AVAILABILITY
- AVAILABILITY_GROUP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- CREATE AVAILABILITY GROUP statement
- Availability Groups [SQL Server], creating
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: a3d55df7-b4e4-43f3-a14b-056cba36ab98
caps.latest.revision: 196
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cebeb43402be1762021738096b9a0e959082d986
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-availability-group-transact-sql"></a>CREATE AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crée un nouveau groupe de disponibilité, si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est activée pour la fonctionnalité [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
> [!IMPORTANT]  
>  Exécutez CREATE AVAILABILITY GROUP sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous projetez d'utiliser comme réplica principal initial de votre nouveau groupe de disponibilité. Cette instance de serveur doit résider sur un nœud de clustering de basculement Windows Server (WSFC).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE AVAILABILITY GROUP group_name  
   WITH (<with_option_spec> [ ,...n ] )  
   FOR [ DATABASE database_name [ ,...n ] ]  
   REPLICA ON <add_replica_spec> [ ,...n ]  
   AVAILABILITY GROUP ON <add_availability_group_spec> [ ,...2 ]  
   [ LISTENER ‘dns_name’ ( <listener_option> ) ]  
[ ; ]  
  
<with_option_spec>::=   
    AUTOMATED_BACKUP_PREFERENCE = { PRIMARY | SECONDARY_ONLY| SECONDARY | NONE }  
  | FAILURE_CONDITION_LEVEL  = { 1 | 2 | 3 | 4 | 5 }   
  | HEALTH_CHECK_TIMEOUT = milliseconds  
  | DB_FAILOVER  = { ON | OFF }   
  | DTC_SUPPORT  = { PER_DB | NONE }  
  | BASIC  
  | DISTRIBUTED
  | REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = { integer }
  | CLUSTER_TYPE = { WSFC | EXTERNAL | NONE } 
  
<add_replica_spec>::=  
  <server_instance> WITH  
    (  
       ENDPOINT_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT },  
       FAILOVER_MODE = { AUTOMATIC | MANUAL }  
       [ , <add_replica_option> [ ,...n ] ]  
    )   
  
  <add_replica_option>::=  
       SEEDING_MODE = { AUTOMATIC | MANUAL }  
     | BACKUP_PRIORITY = n  
     | SECONDARY_ROLE ( {   
            [ ALLOW_CONNECTIONS = { NO | READ_ONLY | ALL } ]   
        [,] [ READ_ONLY_ROUTING_URL = 'TCP://system-address:port' ]  
     } )  
     | PRIMARY_ROLE ( {   
            [ ALLOW_CONNECTIONS = { READ_WRITE | ALL } ]   
        [,] [ READ_ONLY_ROUTING_LIST = { ( ‘<server_instance>’ [ ,...n ] ) | NONE } ]  
     } )  
     | SESSION_TIMEOUT = integer  
  
<add_availability_group_spec>::=  
 <ag_name> WITH  
    (  
       LISTENER_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT },  
       FAILOVER_MODE = MANUAL,  
       SEEDING_MODE = { AUTOMATIC | MANUAL }  
    )  
  
<listener_option> ::=  
   {  
      WITH DHCP [ ON ( <network_subnet_option> ) ]  
    | WITH IP ( { ( <ip_address_option> ) } [ , ...n ] ) [ , PORT = listener_port ]  
   }  
  
  <network_subnet_option> ::=  
     ‘four_part_ipv4_address’, ‘four_part_ipv4_mask’    
  
  <ip_address_option> ::=  
     {   
        ‘four_part_ipv4_address’, ‘four_part_ipv4_mask’  
      | ‘ipv6_address’  
     }  
  
```  
  
## <a name="arguments"></a>Arguments  
 *nom_groupe*  
 Spécifie le nom du nouveau groupe de disponibilité. *nom_groupe* doit être un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [identificateur](../../relational-databases/databases/database-identifiers.md), et il doit être unique parmi tous les groupes de disponibilité dans le cluster WSFC. La longueur maximale d'un nom de groupe de disponibilité est de 128 caractères.  
  
 AUTOMATED_BACKUP_PREFERENCE  **=**  {PRINCIPAL | SECONDARY_ONLY | SECONDAIRE | AUCUN}  
 Spécifie une préférence sur la manière dont un travail de sauvegarde doit évaluer le réplica principal lorsqu'on choisit où effectuer des sauvegardes. Vous pouvez écrire un travail de sauvegarde donné pour prendre en compte la préférence de sauvegarde automatisée. Il est important de comprendre que la préférence n'est pas appliquée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par conséquent, elle n'a aucune incidence sur les sauvegardes ad hoc.  
  
 Les valeurs prises en charge sont les suivantes :  
  
 PRIMARY  
 Spécifie que les sauvegardes doivent toujours avoir lieu sur le réplica principal. Cette option est utile si vous avez besoin de fonctionnalités de sauvegarde, telles que la création de sauvegardes différentielles, qui ne sont pas prises en charge lorsque la sauvegarde est exécutée sur un réplica secondaire.  
  
> [!IMPORTANT]  
>  Si vous envisagez d’utiliser la copie de journaux de transaction pour préparer des bases de données secondaires pour un groupe de disponibilité, définissez la préférence de sauvegarde automatisée sur **Principal** jusqu’à ce que toutes les bases de données secondaires aient été préparées et attachées au groupe de disponibilité.  
  
 SECONDARY_ONLY  
 Spécifie que les sauvegardes ne doivent jamais être effectuées sur le réplica principal. Si le réplica principal est le seul réplica en ligne, la sauvegarde ne doit pas avoir lieu.  
  
 SECONDARY  
 Spécifie que les sauvegardes doivent se produire sur un réplica secondaire sauf lorsque le réplica principal est le seul réplica en ligne. Dans ce cas, la sauvegarde doit se produire sur le réplica principal. Il s'agit du comportement par défaut.  
  
 Aucune  
 Spécifie que vous préférez que les travaux de sauvegarde ignorent le rôle des réplicas de disponibilité lorsque vous choisissez le réplica pour effectuer les sauvegardes. Notez que les travaux de sauvegarde peuvent évaluer d'autres facteurs tels que la priorité de sauvegarde de chaque réplica de disponibilité en association avec son état opérationnel et son état connecté.  
  
> [!IMPORTANT]  
>  Il n'y a aucune contrainte du paramètre AUTOMATED_BACKUP_PREFERENCE. La traduction de cette préférence dépend de la logique, le cas échéant, que vous avez écrite dans les travaux de sauvegarde pour les bases de données dans un groupe de disponibilité donné. Le paramètre de préférence de sauvegarde automatisée n'a aucun impact sur les sauvegardes ad-hoc. Pour plus d’informations, consultez [configurer la sauvegarde sur les réplicas de disponibilité &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  
  
> [!NOTE]  
>  Pour afficher la préférence de sauvegarde automatisée d’un groupe de disponibilité existant, sélectionnez le **automated_backup_preference** ou **automated_backup_preference_desc** colonne de la [sys.availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) affichage catalogue. En outre, [sys.fn_hadr_backup_is_preferred_replica &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql.md) peut être utilisé pour déterminer le réplica de sauvegarde par défaut.  Cette fonction retourne 1 pour au moins un des réplicas, même lorsque `AUTOMATED_BACKUP_PREFERENCE = NONE`.  
  
 FAILURE_CONDITION_LEVEL  **=**  {1 | 2 | **3** | 4 | 5}  
 Spécifie les conditions d’échec déclencheront un basculement automatique pour ce groupe de disponibilité. FAILURE_CONDITION_LEVEL est défini au niveau du groupe mais s’applique uniquement sur les réplicas de disponibilité qui sont configurés pour le mode de disponibilité à validation synchrone (AVAILIBILITY_MODE  **=**  SYNCHRONOUS_COMMIT). En outre, les conditions d’échec peuvent déclencher un basculement automatique, uniquement si les réplicas principales et secondaire sont configurés pour le mode de basculement automatique (FAILOVER_MODE  **=**  automatique) et le réplica secondaire est actuellement synchronisé avec le réplica principal.  
  
 Les niveaux de condition d'échec (1-5) s'étendent du moins restrictif, niveau 1, au plus restrictif, le niveau 5. Un niveau de condition donné comprend tous les niveaux moins restrictifs. Par conséquent, le niveau de condition le plus strict, le niveau 5, inclut les quatre niveaux de condition moins restrictifs (1 à 4), le niveau 4 inclut les niveaux 1 à 3, et ainsi de suite. Le tableau suivant décrit la condition d'échec qui correspond à chaque niveau.  
  
|Level|Condition d'échec|  
|-----------|-----------------------|  
|1|Spécifie qu'un basculement automatique doit être initialisé lorsque l'une des conditions suivantes se produit :<br /><br /> -La [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service est arrêté.<br /><br /> -Le bail du groupe de disponibilité pour la connexion au cluster WSFC expire car aucun accusé de réception n’est reçu à partir de l’instance de serveur. Pour plus d’informations, consultez [Fonctionnement : délai d’expiration de bail Always On SQL Server](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-AlwaysOn-lease-timeout.aspx).|  
|2|Spécifie qu'un basculement automatique doit être initialisé lorsque l'une des conditions suivantes se produit :<br /><br /> -L’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne se connecte pas au cluster, et le seuil HEALTH_CHECK_TIMEOUT spécifié par l’utilisateur du groupe de disponibilité est dépassé.<br /><br /> -Le réplica de disponibilité est en état d’échec.|  
|3|Spécifie qu'un basculement automatique doit être initialisé sur les erreurs internes critiques [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], telles que les verrouillages spinlock orphelins, les violations graves d'accès en écriture, ou en cas de vidages trop importants.<br /><br /> Il s'agit du comportement par défaut.|  
|4|Spécifie qu'un basculement automatique doit être initialisé sur les erreurs internes modérées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], telles qu'une condition persistante de mémoire insuffisante dans le pool de ressources interne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|5|Spécifie qu'un basculement automatique doit être initialisé sur tous les états d'échec qualifiés, notamment :<br /><br /> -Insuffisance des threads de travail du moteur SQL.<br /><br /> -Détection d’un blocage insoluble.|  
  
> [!NOTE]  
>  Absence de réponse par une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client demandes ne s’applique pas aux groupes de disponibilité.  
  
 Les valeurs de FAILURE_CONDITION_LEVEL et de HEALTH_CHECK_TIMEOUT, définir un *stratégie de basculement flexible* pour un groupe donné. Cette stratégie de basculement souple vous offre un contrôle granulaire sur les conditions qui doivent entraîner un basculement automatique. Pour plus d’informations, consultez [stratégie de basculement Flexible pour le basculement automatique d’un groupe de disponibilité &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/flexible-automatic-failover-policy-availability-group.md).  
  
 HEALTH_CHECK_TIMEOUT  **=**  *millisecondes*  
 Spécifie le temps d’attente (en millisecondes) pour le [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) procédures stockées système pour retourner les informations d’intégrité du serveur avant que le cluster WSFC suppose que l’instance de serveur est lente ou suspendue. HEALTH_CHECK_TIMEOUT est défini au niveau du groupe mais s’applique uniquement sur les réplicas de disponibilité qui sont configurés pour le mode de disponibilité à validation synchrone avec basculement automatique (AVAILIBILITY_MODE  **=**  SYNCHRONOUS_COMMIT).  En outre, d’un délai d’attente de contrôle d’intégrité peut déclencher un basculement automatique uniquement si les réplicas principales et secondaire sont configurés pour le mode de basculement automatique (FAILOVER_MODE  **=**  automatique) et le réplica secondaire est actuellement synchronisé avec le réplica principal.  
  
 La valeur par défaut de HEALTH_CHECK_TIMEOUT est de 30 000 millisecondes (30 secondes). La valeur minimale est 15 000 millisecondes (15 secondes), et la valeur maximale est 4 294 967 295 millisecondes.  
  
> [!IMPORTANT]  
>  **sp_server_diagnostics** n’exécute pas de vérifications d’intégrité au niveau de la base de données.  
  
 DB_FAILOVER  **=**  {ON | {OFF}  
 Indique l’action à entreprendre lorsqu’une base de données sur le réplica principal est hors connexion. Lorsque cette propriété a la valeur ON, n’importe quel état autre que ONLINE pour une base de données dans le groupe de disponibilité déclenche un basculement automatique. Lorsque cette option est définie sur OFF, uniquement l’intégrité de l’instance est utilisée pour déclencher un basculement automatique.  
  
  Pour plus d’informations sur ce paramètre, consultez [Option de détection de base de données au niveau d’intégrité](../../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md) 
  
 DTC_SUPPORT  **=**  {PER_DB | AUCUN}  
 Spécifie si les transactions entre bases de données sont pris en charge par le biais du coordinateur de transactions distribuées (DTC). Les transactions entre bases de données sont uniquement prise en charge dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. PER_DB crée le groupe de disponibilité avec prise en charge de ces transactions. Pour plus d’informations, consultez [Transactions entre bases de données et transactions distribuées pour des groupes de disponibilité Always On et la mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  
 BASIC  
 Utilisé pour créer un groupe de disponibilité de base. Les groupes de disponibilité de base sont limités à une base de données et deux réplicas : un réplica principal et un réplica secondaire. Cette option est un remplacement pour la base de données déconseillée mise en miroir de SQL Server Standard Edition. Pour plus d’informations, consultez [base des groupes de disponibilité &#40; Toujours sur les groupes de disponibilité &#41; ](../../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md). Groupes de disponibilité de base sont pris en charge à compter de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  

 DISTRIBUTED  
 Utilisé pour créer un groupe de disponibilité distribué. Cette option est utilisée avec le paramètre de groupe de disponibilité ON pour connecter deux groupes de disponibilité dans les Clusters de basculement Windows Server distincts.  Pour plus d’informations, consultez [Groupes de disponibilité distribués &#40;groupes de disponibilité Always On&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md). Groupes de disponibilité distribués sont pris en charge à compter de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. 

 REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT   
 Introduite dans SQL Server 2017 CTP 2.2. Utilisé pour définir un nombre minimal de réplicas secondaires synchrones requis pour valider avant que le réplica principal valide une transaction. Garantit que la transaction SQL Server attend jusqu'à ce que les journaux des transactions sont mis à jour sur le nombre minimal de réplicas secondaires. La valeur par défaut est 0, ce qui donne le même comportement que SQL Server 2016. La valeur minimale est 0. La valeur maximale est le nombre de réplicas moins 1. Cette option se rapporte aux réplicas en mode de validation synchrone. Lorsque les réplicas sont en mode de validation synchrone, les écritures sur le réplica principal patienter jusqu'à ce que les écritures sur les réplicas secondaires synchrones sont validées dans le journal des transactions de base de données réplica. Si un serveur SQL Server qui héberge un réplica synchrone secondaire cesse de répondre, le serveur SQL qui héberge le réplica principal marque ce réplica secondaire comme pas synchronisés et continuer. Lorsque la base de données ne répond pas revient en ligne, il se trouve dans un état « non synchronisé » et le réplica est marqué comme étant non fonctionnelle jusqu'à ce que le serveur principal peut rendre synchrones à nouveau. Ce paramètre garantit que le réplica principal attend jusqu'à ce que le nombre minimal de réplicas ont validées à chaque transaction. Si le nombre minimal de réplicas n’est pas disponible est validée sur le serveur principal échoue. Ce paramètre s’applique aux groupes de disponibilité avec le type de cluster `WSFC` et `EXTERNAL`. Pour le type de cluster `EXTERNAL` le paramètre est modifié lorsque le groupe de disponibilité est ajouté à une ressource de cluster. Consultez [haute disponibilité et protection des données pour les configurations de groupe de disponibilité](../../linux/sql-server-linux-availability-group-ha.md).

 CLUSTER_TYPE  
 Introduite dans SQL Server 2017 CTP 2.2. Utilisé pour identifier si le groupe de disponibilité est sur un Cluster de basculement du serveur Windows (WSFC).  La valeur WSFC lorsque le groupe de disponibilité se trouve sur une instance de cluster de basculement sur un cluster de basculement Windows Server. La valeur externe lorsque le cluster est géré par un gestionnaire de cluster qui n’est pas un cluster de basculement Windows Server, tels que Linux STIMULATEUR. Défini sur NONE lorsque ne pas à l’aide de WSFC pour la coordination de cluster du groupe de disponibilité. Par exemple, lorsqu’un groupe de disponibilité comprend des serveurs Linux. 

 Base de données *nom_base_de_données*  
 Spécifie une liste d'une ou plusieurs bases de données utilisateur sur l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale (autrement dit, l'instance de serveur sur laquelle vous créez le groupe de disponibilité). Vous pouvez spécifier plusieurs bases de données pour un groupe de disponibilité, mais chaque base de données ne peut appartenir qu'à un seul groupe de disponibilité. Pour plus d’informations sur le type de bases de données prises en charge par un groupe de disponibilité, consultez [conditions préalables, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md). Pour les bases de données locales appartient déjà à un groupe de disponibilité, consultez le **replica_id** colonne dans la [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vue de catalogue.  
  
 La clause DATABASE est facultative. Si vous l’omettez, le nouveau groupe de disponibilité est vide.  
  
 Après avoir créé le groupe de disponibilité, connectez-vous à chaque instance de serveur qui héberge un réplica secondaire puis préparer chaque base de données secondaire et joindre au groupe de disponibilité. Pour plus d’informations, consultez [Démarrer un mouvement de données sur une base de données secondaire Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
> [!NOTE]  
>  Ultérieurement, vous pouvez ajouter des bases de données appropriées sur l'instance de serveur qui héberge le réplica principal actuel à un groupe de service. Vous pouvez également supprimer une base de données secondaire dans un groupe de disponibilité. Pour plus d’informations, consultez [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
 REPLICA ON  
 Spécifie une à cinq instances de SQL Server comme réplicas de disponibilité hôtes dans le nouveau groupe de disponibilité.  Chaque réplica est spécifié par son adresse d'instance de serveur suivie d'une clause WITH (…). Au minimum, vous devez spécifier votre instance de serveur local, qui devient le réplica principal initial. Éventuellement, vous pouvez également spécifier jusqu'à quatre réplicas secondaires.  
  
 Vous devez joindre chaque réplica secondaire au groupe de disponibilité. Pour plus d’informations, consultez [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
> [!NOTE]  
>  Si vous spécifiez moins de quatre réplicas secondaires lorsque vous créez un groupe de disponibilité, vous pouvez ajouter un réplica secondaire supplémentaire à tout moment à l’aide de la [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction. Vous pouvez également utiliser cette instruction pour supprimer un réplica secondaire d'un groupe de disponibilité existant.  
  
 \<instance_serveur > Spécifie l’adresse de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est l’hôte pour un réplica. Le format de l'adresse varie selon que l'instance est l'instance par défaut ou une instance nommée et s'il s'agit d'une instance autonome ou d'une instance de cluster de basculement (FCI), comme suit :  
  
 { '*nom_système*[\\*nom_instance*]' | '*nom_réseau_FCI*[\\*nom_instance*]' }  
  
 Les composants de cette adresse sont les suivants :  
  
 *nom_système*  
 Nom NetBIOS du système informatique sur lequel réside l'instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cet ordinateur doit être un nœud WSFC.  
  
 *nom_réseau_FCI*  
 Nom réseau utilisé pour accéder à un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez ce nom si l'instance de serveur participe en tant que serveur partenaire de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L’exécution de SELECT [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) sur une instance de cluster, instance de serveur renvoie son intégralité '*nom_réseau_fci*[\\*nom_instance*]' chaîne (qui est le nom du réplica complet).  
  
 *nom_instance*  
 Est le nom d’une instance d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est hébergé par *nom_système* ou *nom_réseau_fci* et qui a HADR service est activé. Pour une instance de serveur par défaut, *nom_instance* est facultatif. Les noms d'instance ne respectent pas la casse. Sur une instance de serveur autonome, ce nom de la valeur est identique à la valeur retournée par l’exécution de SELECT [@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md).  
  
 \  
 Séparateur utilisé uniquement lors de la spécification *nom_instance*, afin de séparer de *nom_système* ou *nom_réseau_fci*.  
  
 Pour plus d’informations sur la configuration requise pour les nœuds WSFC et les instances de serveur, consultez [conditions préalables, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 ENDPOINT_URL **='**TCP**://***adresse-système***:***port***'**  
 Spécifie le chemin d’accès d’URL pour le [point de terminaison de mise en miroir de base de données](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md) sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge le réplica de disponibilité que vous définissez dans votre clause REPLICA ON actuelle.  
  
 La clause ENDPOINT_URL est obligatoire. Pour plus d’informations, consultez [Spécifier l’URL de point de terminaison lors de l’ajout ou lors de la modification d’un réplica de disponibilité &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md).  
  
 **'**TCP**://***adresse-système***:***port***'**  
 Spécifie une URL pour spécifier une URL de point de terminaison ou l'URL de routage en lecture seule. Les paramètres d'URL sont les suivants :  
  
 *system-address*  
 Chaîne, telle qu'un nom de système, un nom de domaine complet ou une adresse IP, qui identifie de manière unique l'ordinateur de destination.  
  
 *port*  
 Numéro de port associé au point de terminaison de mise en miroir de l'instance de serveur partenaire (pour l'option ENDPOINT_URL) ou numéro de port utilisé par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] de l'instance de serveur (pour l'option READ_ONLY_ROUTING_URL).  
  
 AVAILABILITY_MODE  **=**  {{SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT}  
 SYNCHRONOUS_COMMIT ou ASYNCHRONOUS_COMMIT Spécifie si le réplica principal doit attendre que le réplica secondaire accepter la sécurisation renforcée (écriture) des enregistrements de journal sur le disque avant que le réplica principal peut valider la transaction sur une base de données primaire. Les transactions sur des bases de données différentes sur le même réplica principal peuvent être validées indépendamment.
  
 SYNCHRONOUS_COMMIT  
 Spécifie que le réplica principal attend pour valider des transactions jusqu'à ce qu’ils ont été renforcés sur ce réplica secondaire (mode de validation synchrone). Vous pouvez spécifier SYNCHRONOUS_COMMIT pour trois réplicas au maximum, y compris le réplica principal.  
  
 ASYNCHRONOUS_COMMIT  
 Spécifie que le réplica principal valide les transactions sans attendre que la sécurité du journal de ce réplica secondaire soit renforcée (mode de disponibilité de validation synchrone). Vous pouvez spécifier ASYNCHRONOUS_COMMIT pour cinq réplicas de disponibilité au maximum, y compris le réplica principal.  
  
 La clause AVAILABILITY_MODE est obligatoire. Pour plus d’informations, consultez [Modes de disponibilité &#40;groupes de disponibilité Always On&#41;](../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).  
  
 FAILOVER_MODE  **=**  {AUTOMATIQUE | MANUEL}  
 Spécifie le mode de basculement du réplica de disponibilité que vous définissez.  
  
 AUTOMATIC  
 Active le basculement automatique. Cette option n'est prise en charge que si vous spécifiez également AVAILABILITY_MODE = SYNCHRONOUS_COMMIT. Vous pouvez spécifier AUTOMATIC pour deux réplicas de disponibilité, y compris le réplica principal.  
  
> [!NOTE]  
>  Les instances de cluster de basculement (FCI) SQL Server ne prennent pas en charge le basculement automatique par les groupes de disponibilité. Par conséquent, tout réplica de disponibilité hébergé par une instance de cluster de basculement ne peut être configuré que pour un basculement manuel.  
  
 MANUAL  
 Active le basculement manuel planifié ou le basculement manuel forcé (généralement appelé *le basculement forcé*) par l’administrateur de base de données.  
  
 La clause FAILOVER_MODE est obligatoire. Les deux types de basculement manuel, le basculement manuel sans perte de données et le basculement forcé (avec perte de données possible) sont pris en charge dans différentes conditions. Pour plus d’informations, consultez [Basculement et modes de basculement &#40;groupes de disponibilité Always On&#41;](../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md).  
  
 SEEDING_MODE  **=**  {AUTOMATIQUE | MANUEL}  
 Spécifie comment le réplica secondaire est initialement d’amorçage.  
  
 AUTOMATIC  
 Permet à l’amorçage direct. Cette méthode est basée sur le réplica secondaire sur le réseau. Cette méthode ne nécessite pas de sauvegarder et restaurer une copie de la base de données principal sur le réplica.  
  
> [!NOTE]  
>  Pour l’amorçage direct, vous devez autoriser la création de la base de données sur chaque réplica secondaire en appelant **ALTER AVAILABILITY GROUP** avec la **GRANT CREATE ANY DATABASE** option.  
  
 MANUAL  
 Spécifie l’amorçage manuel (par défaut). Cette méthode vous oblige à créer une sauvegarde de la base de données sur le réplica principal et restaurer manuellement cette sauvegarde sur le réplica secondaire.  
  
 BACKUP_PRIORITY  **=** *n*  
 Spécifie la priorité d'exécution des sauvegardes sur ce réplica par rapport aux autres réplicas dans le même groupe de disponibilité. La valeur est un entier compris entre 0 et 100. Ces valeurs ont les significations suivantes :  
  
-   1..100 indique que le réplica de disponibilité peut être choisi pour effectuer des sauvegardes. 1 indique la priorité la plus faible, 100 la priorité la plus élevée. Si BACKUP_PRIORITY = 1, le réplica de disponibilité est choisi pour l'exécution des sauvegardes uniquement si aucun réplica de disponibilité ayant une priorité plus élevée n'est actuellement disponible.  
  
-   0 indique que ce réplica de disponibilité n’est pas pour effectuer des sauvegardes. Cela est utile, par exemple, pour un réplica de disponibilité distant sur lequel vous ne souhaitez jamais basculer de sauvegardes.  
  
 Pour plus d’informations, consultez [Secondaires actifs : sauvegarde sur les réplicas secondaires &#40;groupes de disponibilité Always On&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).  
  
 SECONDARY_ROLE **(** ... **)**  
 Spécifie les paramètres spécifiques au rôle qui en vigueur si ce réplica de disponibilité possède actuellement le rôle secondaire (autrement dit, chaque fois qu’il s’agit d’un réplica secondaire). Entre parenthèses, spécifiez le l'une ou l'autre, ou les deux options de rôle secondaire. Si vous spécifiez les deux, utilisez une liste séparée par des virgules.  
  
 Les options de rôle secondaire sont les suivantes :  
  
 ALLOW_CONNECTIONS  **=**  {NON | READ_ONLY | TOUS LES}  
 Spécifie si les bases de données d'un réplica de disponibilité donné qui joue le rôle secondaire (autrement dit, qui joue le rôle d'un réplica secondaire) peuvent accepter de clients, dont :  
  
 NO  
 Aucune connexion utilisateur n'est autorisée aux bases de données secondaires de ce réplica. Elles ne sont pas disponibles pour l'accès en lecture. Il s'agit du comportement par défaut.  
  
 READ_ONLY  
 Seules les connexions sont autorisées aux bases de données dans le réplica secondaire où la propriété d’intention de l’Application a la valeur **ReadOnly**. Pour plus d'informations sur cette propriété, consultez [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 ALL  
 Toutes les connexions sont autorisées aux bases de données dans le réplica secondaire pour un accès en lecture seule.  
  
 Pour plus d’informations, consultez [Secondaires actifs : réplicas secondaires lisibles &#40;groupes de disponibilité Always On&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 READ_ONLY_ROUTING_URL **='**TCP**://***adresse-système***:***port***'**  
 Spécifie l'URL à utiliser pour le routage des demandes de connexion de tentative de lecture à ce réplica de disponibilité. Il s'agit de l'URL sur laquelle le moteur de base de données SQL Server écoute. En général, l'instance par défaut du moteur de base de données SQL Server écoute le port TCP 1433.  
  
 Pour une instance nommée, vous pouvez obtenir le numéro de port en interrogeant le **port** et **type_desc** les colonnes de la [sys.dm_tcp_listener_states](../../relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql.md) vue de gestion dynamique. L’instance de serveur utilise l’écouteur Transact-SQL (**type_desc = 'TSQL'**).  
  
 Pour plus d’informations sur le calcul de l’URL de routage en lecture seule pour un réplica, consultez [read_only_routing_url de calcul pour Always On](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-AlwaysOn.aspx).  
  
> [!NOTE]  
>  Pour une instance nommée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'écouteur Transact-SQL doit être configuré pour utiliser un port spécifique. Pour plus d’informations, consultez [Configurer un serveur pour écouter un port TCP spécifique &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
 PRIMARY_ROLE **(** ... **)**  
 Spécifie les paramètres spécifiques au rôle qui en vigueur si ce réplica de disponibilité joue actuellement le rôle principal (autrement dit, chaque fois qu’il est le réplica principal). Entre parenthèses, spécifiez le l'une ou l'autre, ou les deux options de rôle principal. Si vous spécifiez les deux, utilisez une liste séparée par des virgules.  
  
 Les options de rôle principal sont les suivantes :  
  
 ALLOW_CONNECTIONS  **=**  {READ_WRITE | TOUS LES}  
 Spécifie le type de connexion que les bases de données d'un réplica de disponibilité donné qui joue le rôle principal (autrement dit, qui joue le rôle d'un réplica principal) peuvent accepter de clients, dont :  
  
 READ_WRITE  
 Les connexions où la propriété de connexion d’intention de l’application a la valeur **ReadOnly** ne sont pas autorisées.  Lorsque la propriété d'intention de l'application a la valeur **ReadWrite** ou si cette propriété n'est pas définie, la connexion est autorisée. Pour plus d'informations sur la propriété de connexion d'intention de l'application, consultez [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 ALL  
 Toutes les connexions aux bases de données sont autorisées dans le réplica principal. Il s'agit du comportement par défaut.  
  
 READ_ONLY_ROUTING_LIST  **=**  { **(«**\<instance_serveur >**'** [ **,**... *n* ] **)** | Aucun} spécifie une liste séparée par des virgules d’instances de serveur qui hébergent les réplicas de disponibilité pour ce groupe de disponibilité qui répondent aux exigences suivantes lors de l’exécution sous le rôle secondaire :  
  
-   Être configurés pour autoriser les connexions ou connexions en lecture seule (voir l'argument ALLOW_CONNECTIONS de l'option de SECONDARY_ROLE, ci-dessus).  
  
-   Disposer de leur URL de routage en lecture seule définie (voir l'argument READ_ONLY_ROUTING_URL de l'option SECONDARY_ROLE, ci-dessus).  
  
 Les valeurs de READ_ONLY_ROUTING_LIST sont les suivantes :  
  
 \<instance_serveur > Spécifie l’adresse de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est l’hôte pour un réplica qui est un réplica secondaire lisible lors de l’exécution sous le rôle secondaire.  
  
 Utilisez une liste séparée par des virgules pour spécifier toutes les instances de serveur qui peuvent héberger un réplica secondaire lisible. Routage en lecture seule suit l’ordre dans le serveur auquel les instances sont spécifiées dans la liste. Si vous incluez l'instance de serveur hôte d'un réplica dans la liste de routage en lecture seule du réplica, il est généralement recommandé d'insérer cette instance de serveur à la fin de la liste, afin que les connexions de tentative de lecture soient dirigées vers un réplica secondaire (le cas échéant).  
  
 À partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], vous pouvez les demandes avec intention de lecture de l’équilibrage de charge entre les réplicas secondaires lisibles. Vous spécifiez cela en plaçant les réplicas dans un jeu imbriqué de parenthèses dans la liste de routage en lecture seule. Pour plus d’informations et d’exemples, consultez [configurer l’équilibrage de charge entre des réplicas en lecture seule](../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md#loadbalancing).  
  
 Aucune  
 Spécifie que lorsque ce réplica de disponibilité est le réplica principal, routage en lecture seule n'est pas pris en charge. Il s'agit du comportement par défaut.  
  
 SESSION_TIMEOUT  **=**  *entier*  
 Spécifie le délai d'expiration de la session en secondes. Si vous ne précisez pas de valeur, le délai défini par défaut est 10 secondes. La valeur minimale est de 5 secondes.  
  
> [!IMPORTANT]  
>  Le temps d'attente recommandé est de 10 secondes minimum.  
  
 Pour plus d’informations sur la période d’expiration de session, consultez [vue d’ensemble de groupes de disponibilité AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
 GROUPE DE DISPONIBILITÉ SUR  
 Spécifie les deux groupes de disponibilité qui constituent un *groupe de disponibilité distribué*. Chaque groupe de disponibilité est la partie de son propre Cluster de basculement Windows Server (WSFC). Lorsque vous créez un groupe de disponibilité distribué, le groupe de disponibilité sur l’Instance actuelle de SQL Server devient le groupe de disponibilité principal. Le deuxième groupe de disponibilité devient le groupe de disponibilité secondaire.  
  
 Vous devez joindre le groupe de disponibilité secondaire au groupe de disponibilité distribué. Pour plus d’informations, consultez [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
 \<ag_name > Spécifie le nom du groupe de disponibilité qui constitue une partie du groupe de disponibilité distribués.  
  
 ÉCOUTEUR **='**TCP**://***adresse-système***:***port***'**  
 Spécifie le chemin d’accès de l’URL de l’écouteur associé au groupe de disponibilité.  
  
 La clause de l’écouteur est obligatoire.  
  
 **'**TCP**://***adresse-système***:***port***'**  
 Spécifie une URL de l’écouteur associé au groupe de disponibilité. Les paramètres d'URL sont les suivants :  
  
 *system-address*  
 Est une chaîne, comme un nom système, un nom de domaine complet ou une adresse IP, qui identifie sans ambiguïté l’écouteur.  
  
 *port*  
 Est un numéro de port qui est associé au point de terminaison de mise en miroir du groupe de disponibilité. Notez que cela n’est pas le port de l’écouteur.  
  
 AVAILABILITY_MODE  **=**  {SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT}  
 Spécifie si le réplica principal se trouve en attente pour le groupe de disponibilité secondaire accepter la sécurisation renforcée (écriture) des enregistrements de journal sur le disque avant que le réplica principal peut valider la transaction sur une base de données primaire.  
  
 SYNCHRONOUS_COMMIT  
 Spécifie que le réplica principal attend pour valider des transactions jusqu'à ce qu’ils ont été renforcés sur le groupe de disponibilité secondaire. Vous pouvez spécifier SYNCHRONOUS_COMMIT pour les deux groupes de disponibilité, y compris le groupe de disponibilité principal.  
  
 ASYNCHRONOUS_COMMIT  
 Spécifie que le réplica principal valide les transactions sans attendre que ce groupe de disponibilité secondaire renforce le journal. Vous pouvez spécifier ASYNCHRONOUS_COMMIT pour les deux groupes de disponibilité, y compris le groupe de disponibilité principal.  
  
 La clause AVAILABILITY_MODE est obligatoire.  
  
 FAILOVER_MODE  **=**  {MANUEL}  
 Spécifie le mode de basculement du groupe de disponibilité distribués.  
  
 MANUAL  
 Active le basculement manuel planifié ou le basculement manuel forcé (généralement appelé *le basculement forcé*) par l’administrateur de base de données.  
  
 La clause FAILOVER_MODE est obligatoire, et la seule option disponible est manuel. Le basculement automatique vers le groupe de disponibilité secondaire n’est pas pris en charge.  
  
 SEEDING_MODE  **=**  {AUTOMATIQUE | MANUEL}  
 Spécifie la façon dont le groupe de disponibilité secondaire est initialement d’amorçage.  
  
 AUTOMATIC  
 Permet à l’amorçage direct. Cette méthode est basée sur le groupe de disponibilité secondaire sur le réseau. Cette méthode ne nécessite pas de sauvegarder et restaurer une copie de la base de données principal sur les réplicas du groupe de disponibilité secondaire.  
  
 MANUAL  
 Spécifie l’amorçage manuel (par défaut). Cette méthode vous oblige à créer une sauvegarde de la base de données sur le réplica principal et restaurer manuellement cette sauvegarde sur l’ou les réplicas du groupe de disponibilité secondaire.  
  
 ÉCOUTEUR **'***nom_DNS***» (** \<listener_option > **)** définit un nouvel écouteur de groupe de disponibilité pour ce groupe de disponibilité. LISTENER est un argument facultatif.  
  
> [!IMPORTANT]  
>  Avant de créer votre premier écouteur, nous recommandons fortement de lire [créer ou configurer un écouteur de groupe de disponibilité &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
>   
>  Après avoir créé un écouteur pour un groupe de disponibilité spécifique, nous vous recommandons fortement de procéder comme suit :  
>   
>  -   Demandez à votre administrateur réseau de réserver l'adresse IP de l'écouteur pour son utilisation exclusive.  
> -   Fournissez le nom d'hôte DNS de l'écouteur aux développeurs d'applications pour qu'ils l'utilisent dans les chaînes de connexion lorsqu'ils demandent des connexions clientes vers ce groupe de disponibilité.  
  
 *nom_DNS*  
 Spécifie le nom d'hôte DNS de l'écouteur du groupe de disponibilité. Le nom DNS de l'écouteur doit être unique dans le domaine et dans NetBIOS.  
  
 *nom_DNS* est une valeur de chaîne. Ce nom ne peut contenir que des caractères alphanumériques, des tirets (-) et des caractères de soulignement (_), dans n'importe quel ordre. Les noms d'hôte DNS ne respectent pas la casse. La longueur maximale autorisée est de 63 caractères.  
  
 Nous vous recommandons de spécifier une chaîne explicite. Par exemple, pour un groupe de disponibilité nommé `AG1`, un nom d'hôte DNS explicite est `ag1-listener`.  
  
> [!IMPORTANT]  
>  NetBIOS identifie les 15 premiers caractères du nom_dns. Si vous avez deux clusters WSFC qui sont contrôlés par le même annuaire Active Directory et que vous essayez de créer des écouteurs de groupe de disponibilité dans les deux clusters à l’aide de noms contenant plus de 15 caractères et un préfixe identique de 15 caractères, une erreur signale que la ressource de nom de réseau virtuel ne peut pas être mise en ligne. Pour plus d'informations sur les règles de préfixe des noms DNS, consultez [Attribution de noms de domaine](http://technet.microsoft.com/library/cc731265\(WS.10\).aspx).  
  
 \<listener_option > LISTENER prend l’une des opérations suivantes \<listener_option > options : 
  
 AVEC le protocole DHCP [ON { **(«***four_part_ipv4_address***','***four_part_ipv4_mask***')** }]  
 Spécifie que l’écouteur utilise la Configuration de protocole DHCP (Dynamic Host).  Si vous le souhaitez, utilisez la clause ON pour identifier le réseau sur lequel cet écouteur est créé. DHCP est limité à un seul sous-réseau est utilisé pour chaque instance de serveur qui héberge un réplica du groupe de disponibilité.  
  
> [!IMPORTANT]  
>  Nous vous déconseillons d'utiliser DHCP dans un environnement de production. Lorsqu'un temps mort se produit et que le bail IP DHCP arrive à expiration, une période de temps supplémentaire est requise pour enregistrer la nouvelle adresse IP de réseau DHCP associée au nom DNS de l'écouteur et cela a un impact sur la connectivité client. Toutefois, DHCP peut tout à fait être utilisé pour configurer un environnement de développement et de test dans le but de vérifier les fonctions de base des groupes de disponibilité et l'intégration avec vos applications.  
  
 Exemple :  
  
 `WITH DHCP ON ('10.120.19.0','255.255.254.0')`  
  
 AVEC IP **(** { **(«***four_part_ipv4_address***','***four_part_ipv4_mask***')** | **(«***ipv6_address***')** } [ **,** ...  *n*  ] **)** [ **,** PORT  **=**  *listener_port* ]  
 Spécifie que, au lieu d’utiliser DHCP, l’écouteur utilise une ou plusieurs adresses IP statiques. Pour créer un groupe de service sur plusieurs sous-réseaux, chaque sous-réseau requiert une adresse IP statique dans la configuration de l'écouteur. Pour un sous-réseau donné, l'adresse IP statique peut être une adresse IPv4 ou une adresse IPv6. Contactez votre administrateur réseau pour obtenir une adresse IP statique pour chaque sous-réseau qui héberge un réplica pour le nouveau groupe de disponibilité.  
  
 Exemple :  
  
 `WITH IP ( ('10.120.19.155','255.255.254.0') )`  
  
 *four_part_ipv4_address*  
 Spécifie une adresse IPv4 en quatre parties pour un écouteur du groupe de disponibilité. Par exemple, `10.120.19.155`.  
  
 *four_part_ipv4_mask*  
 Spécifie un masque IPv4 en quatre parties pour un écouteur du groupe de disponibilité. Par exemple, `255.255.254.0`.  
  
 *ipv6_address*  
 Spécifie une adresse IPv6 pour un écouteur du groupe de disponibilité. Par exemple, `2001::4898:23:1002:20f:1fff:feff:b3a3`.  
  
 PORT  **=**  *listener_port*  
 Spécifie le numéro de port :*listener_port*: à utiliser par un écouteur de groupe de disponibilité qui est spécifié par la clause WITH IP. Le PORT est facultatif.  
  
 Le numéro de port par défaut est 1433. Toutefois, si vous avez des problèmes de sécurité, nous vous recommandons d'utiliser un numéro de port différent.  
  
 Par exemple : `WITH IP ( ('2001::4898:23:1002:20f:1fff:feff:b3a3') ) , PORT = 7777`  
  
## <a name="prerequisites-and-restrictions"></a>Conditions préalables requises et restrictions  
 Pour plus d’informations sur la configuration requise pour la création d’un groupe de disponibilité, consultez [conditions préalables, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 Pour plus d’informations sur les restrictions sur les instructions Transact-SQL AVAILABILITY GROUP, consultez [vue d’ensemble d’instructions Transact-SQL pour les groupes de disponibilité AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/transact-sql-statements-for-always-on-availability-groups.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Requiert le rôle serveur fixe **sysadmin** et l’autorisation de serveur CREATE AVAILABILITY GROUP, l’autorisation ALTER ANY AVAILABILITY GROUP ou l’autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-configuring-backup-on-secondary-replicas-flexible-failover-policy-and-connection-access"></a>A. Configuration de la sauvegarde sur les réplicas secondaires, la stratégie flexible de basculement, et l'accès à la connexion  
 L'exemple suivant crée un groupe de disponibilité nommé `MyAg` de deux bases de données utilisateur, `ThisDatabase` et `ThatDatabase`. Le tableau suivant récapitule les valeurs spécifiées pour les options définies pour l'ensemble du groupe de disponibilité.  
  
|Option de groupe|Paramètre| Description|  
|------------------|-------------|-----------------|  
|AUTOMATED_BACKUP_PREFERENCE|SECONDARY|Cette préférence de sauvegarde automatisée indique que les sauvegardes doivent se produire sur un réplica secondaire, sauf lorsque le réplica principal est le seul réplica en ligne (il s'agit du comportement par défaut). Pour que le paramètre AUTOMATED_BACKUP_PREFERENCE ait effet, vous devez générer un script des travaux de sauvegarde dans les bases de données de disponibilité pour prendre en compte la préférence de sauvegarde automatisée.|  
|FAILURE_CONDITION_LEVEL|3|Cette définition du niveau de condition d'échec spécifie qu'un basculement automatique doit être initialisé sur les erreurs internes SQL Server critiques, telles que les verrouillages Spinlock orphelins, les violations graves d'accès en écriture, ou en cas de trop de vidages.|  
|HEALTH_CHECK_TIMEOUT|600000|Cette valeur de délai d’attente de vérification d’intégrité, 60 secondes, spécifie que le cluster WSFC attend 60 000 millisecondes pour les [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) procédures stockées système pour retourner des informations de l’intégrité du serveur sur une instance de serveur qui héberge un réplica avec validation synchrone avec le mode automatique avant que le cluster part du principe que l’instance de serveur hôte est lente ou suspendue. (La valeur par défaut est 30 000 millisecondes.)|  
  
 Trois réplicas de disponibilité doivent être hébergés par les instances de serveur par défaut sur des ordinateurs nommés `COMPUTER01`, `COMPUTER02` et `COMPUTER03`. Le tableau suivant récapitule les valeurs spécifiées pour les options de réplica de chaque réplica.  
  
|Option de réplica|Définition sur `COMPUTER01`|Définition sur `COMPUTER02`|Définition sur `COMPUTER03`| Description|  
|--------------------|-----------------------------|-----------------------------|-----------------------------|-----------------|  
|ENDPOINT_URL|TCP : / /*COMPUTER01:5022*|TCP : / /*COMPUTER02:5022*|TCP : / /*COMPUTER03:5022*|Dans cet exemple, les systèmes sont dans le même domaine ; les URL de point de terminaison peuvent utiliser le nom du système informatique comme adresse système.|  
|AVAILABILITY_MODE|SYNCHRONOUS_COMMIT|SYNCHRONOUS_COMMIT|ASYNCHRONOUS_COMMIT|Deux des réplicas utilisent le mode de validation synchrone. Une fois synchronisés, ils prennent en charge le basculement sans perte de données. Le troisième réplica, qui utilise le mode de disponibilité avec validation asynchrone.|  
|FAILOVER_MODE|AUTOMATIC|AUTOMATIC|MANUAL|Les réplicas de validation synchrone-prennent en charge le basculement automatique et le basculement manuel planifié. Le réplica qui utilise le mode de disponibilité avec validation synchrone-prend uniquement en charge le basculement manuel forcé.|  
|BACKUP_PRIORITY|30|30|90|Une priorité plus élevée (90) que celle affectée aux réplicas de validation synchrone est affectée au réplica de validation asynchrone. Les sauvegardes ont tendance à se produire sur l’instance de serveur qui héberge le réplica avec validation asynchrone.|  
|SECONDARY_ROLE|( ALLOW_CONNECTIONS = NO,<br /><br /> READ_ONLY_ROUTING_URL = 'TCP://COMPUTER01:1433' )|( ALLOW_CONNECTIONS = NO,<br /><br /> READ_ONLY_ROUTING_URL = 'TCP://COMPUTER02:1433' )|( ALLOW_CONNECTIONS = READ_ONLY, <br />READ_ONLY_ROUTING_URL = 'TCP://COMPUTER03:1433' )|Seul le réplica de validation asynchrone sert de réplica secondaire accessible en lecture.<br /><br /> Spécifie le nom d'ordinateur et le numéro de port par défaut du moteur de base de données (1433).<br /><br /> Cet argument est facultatif.|  
|PRIMARY_ROLE|( ALLOW_CONNECTIONS = READ_WRITE, <br />READ_ONLY_ROUTING_LIST = (COMPUTER03) )|( ALLOW_CONNECTIONS = READ_WRITE, <br />READ_ONLY_ROUTING_LIST = (COMPUTER03) )|( ALLOW_CONNECTIONS = READ_WRITE, <br />READ_ONLY_ROUTING_LIST = NONE )|Dans le rôle principal, tous les réplicas rejettent les tentatives de connexion d’intention de lecture.<br /><br /> Les demandes de connexion d’intention de lecture sont routées vers COMPUTER03 si le réplica local s’exécute sous le rôle secondaire. Lorsque ce réplica s'exécute sous le rôle principal, le routage en lecture seule est désactivé.<br /><br /> Cet argument est facultatif.|  
|SESSION_TIMEOUT|10|10|10|Cet exemple spécifie la valeur de délai d'attente par défaut de session (10). Cet argument est facultatif.|  
  
 Enfin, l'exemple spécifie la clause facultative LISTENER pour créer un écouteur du groupe de disponibilité pour le nouveau groupe de disponibilité. Un seul nom DNS, `MyAgListenerIvP6`, est spécifié pour cet écouteur. Les deux réplicas sont sur des sous-réseaux différents, l'écouteur doit utiliser des adresses IP statiques. Pour les deux réplicas de disponibilité, la clause WITH IP spécifie une adresse IP statique, `2001:4898:f0:f00f::cf3c` et `2001:4898:e0:f213::4ce2`, qui utilisent le format IPv6. Cet exemple utilise également l'argument facultatif PORT pour spécifier le port `60173` comme port d'écoute.  
  
```  
CREATE AVAILABILITY GROUP MyAg   
   WITH (  
      AUTOMATED_BACKUP_PREFERENCE = SECONDARY,  
      FAILURE_CONDITION_LEVEL  =  3,   
      HEALTH_CHECK_TIMEOUT = 600000  
       )  
  
   FOR   
      DATABASE  ThisDatabase, ThatDatabase   
   REPLICA ON   
      'COMPUTER01' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC,  
         BACKUP_PRIORITY = 30,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = NO,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER01:1433' ),
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER03) ),  
         SESSION_TIMEOUT = 10  
         ),   
  
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC,  
         BACKUP_PRIORITY = 30,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = NO,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER02:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER03) ),  
         SESSION_TIMEOUT = 10  
         ),   
  
      'COMPUTER03' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:5022',  
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
         FAILOVER_MODE =  MANUAL,  
         BACKUP_PRIORITY = 90,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER03:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = NONE ),  
         SESSION_TIMEOUT = 10  
         );
GO  
ALTER AVAILABIIITY GROUP [MyAg]
  ADD LISTENER ‘MyAgListenerIvP6’ ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173 );   
GO  
```  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [Utiliser l’Assistant Groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
 [GROUPE de disponibilité &#40; Transact-SQL &#41;](../../t-sql/statements/drop-availability-group-transact-sql.md)   
 [Résoudre les problèmes toujours sur la Configuration des groupes de disponibilité &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)   
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
  

