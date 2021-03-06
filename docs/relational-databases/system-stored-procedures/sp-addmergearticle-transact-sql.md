---
title: sp_addmergearticle (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergearticle
- sp_addmergearticle_TSQL
helpviewer_keywords:
- sp_addmergearticle
ms.assetid: 0df654ea-24e2-4c61-a75a-ecaa7a140a6c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8852aaf6b8d6baa7a5451f0ccc31229d6f521a33
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494371"
---
# <a name="spaddmergearticle-transact-sql"></a>sp_addmergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un article à une publication de fusion existante. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addmergearticle [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
        , [ @source_object = ] 'source_object'   
    [ , [ @type = ] 'type' ]   
    [ , [ @description = ] 'description' ]   
    [ , [ @column_tracking = ] 'column_tracking' ]   
    [ , [ @status = ] 'status' ]   
    [ , [ @pre_creation_cmd = ] 'pre_creation_cmd' ]   
    [ , [ @creation_script = ] 'creation_script' ]   
    [ , [ @schema_option = ] schema_option ]   
    [ , [ @subset_filterclause = ] 'subset_filterclause' ]   
    [ , [ @article_resolver = ] 'article_resolver' ]   
    [ , [ @resolver_info = ] 'resolver_info' ]   
    [ , [ @source_owner = ] 'source_owner' ]   
    [ , [ @destination_owner = ] 'destination_owner' ]   
    [ , [ @vertical_partition = ] 'vertical_partition' ]   
    [ , [ @auto_identity_range = ] 'auto_identity_range' ]   
    [ , [ @pub_identity_range = ] pub_identity_range ]   
    [ , [ @identity_range = ] identity_range ]   
    [ , [ @threshold = ] threshold ]   
    [ , [ @verify_resolver_signature = ] verify_resolver_signature ]   
    [ , [ @destination_object = ] 'destination_object' ]   
    [ , [ @allow_interactive_resolver = ] 'allow_interactive_resolver' ]   
    [ , [ @fast_multicol_updateproc = ] 'fast_multicol_updateproc' ]   
    [ , [ @check_permissions = ] check_permissions ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @published_in_tran_pub = ] 'published_in_tran_pub' ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @logical_record_level_conflict_detection = ] 'logical_record_level_conflict_detection' ]  
    [ , [ @logical_record_level_conflict_resolution = ] 'logical_record_level_conflict_resolution' ]  
    [ , [ @partition_options = ] partition_options ]  
    [ , [ @processing_order = ] processing_order ]  
    [ , [ @subscriber_upload_options = ] subscriber_upload_options ]  
    [ , [ @identityrangemanagementoption = ] 'identityrangemanagementoption' ]  
    [ , [ @delete_tracking = ] delete_tracking ]  
    [ , [ @compensate_for_errors = ] 'compensate_for_errors' ]   
    [ , [ @stream_blob_columns = ] 'stream_blob_columns' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication contenant l’article. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'` Est le nom de l’article. Le nom doit être unique dans la publication. *article* est **sysname**, sans valeur par défaut. *article* doit se trouver sur l’ordinateur local exécutant [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et doit se conformer aux règles des identificateurs.  
  
`[ @source_object = ] 'source_object'` Est l’objet de base de données à publier. *source_object* est **sysname**, sans valeur par défaut. Pour plus d’informations sur les types d’objets qui peuvent être publiés à l’aide de la réplication de fusion, consultez [publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
`[ @type = ] 'type'` Est le type d’article. *type* est **sysname**, avec une valeur par défaut **table**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**table** (valeur par défaut)|Table avec schéma et données. La réplication surveille la table pour déterminer les données à répliquer.|  
|**schéma de Func uniquement**|Fonction avec schéma uniquement.|  
|**la vue indexée** **schéma uniquement**|Vue indexée avec schéma uniquement.|  
|**proc schéma uniquement**|Procédure stockée avec schéma uniquement.|  
|**schéma du synonyme**|Synonyme avec schéma uniquement.|  
|**afficher le schéma uniquement**|Vue avec schéma uniquement.|  
  
`[ @description = ] 'description'` Est une description de l’article. *Description* est **nvarchar (255)**, avec NULL comme valeur par défaut.  
  
`[ @column_tracking = ] 'column_tracking'` Est le paramètre pour le suivi au niveau des colonnes. *column_tracking* est **nvarchar (10)**, avec FALSE comme valeur par défaut. **true**Active le suivi de colonne. **false** désactive le suivi de colonne et conserve la détection de conflit au niveau des lignes. Si la table est déjà publiée dans d'autres publications de fusion, vous devez utiliser la même valeur de suivi de colonne que celle des articles existants basés sur cette table. Ce paramètre concerne uniquement les articles de table.  
  
> [!NOTE]  
>  Si le suivi de lignes est utilisé pour la détection de conflits (valeur par défaut), la table de base peut inclure 1 024 colonnes au maximum, mais les colonnes doivent être filtrées à partir de l'article afin que 246 colonnes au maximum soient publiées. Si le suivi de colonnes est utilisé, la table de base peut inclure 246 colonnes au maximum.  
  
`[ @status = ] 'status'` Est l’état de l’article. *état* est **nvarchar (10)**, avec une valeur par défaut **unsynced**. Si **active**, le script de traitement initial pour publier la table est exécuté. Si **unsynced**, le script de traitement initial pour publier la table est exécuté à la prochaine exécution de l’Agent d’instantané.  
  
`[ @pre_creation_cmd = ] 'pre_creation_cmd'` Spécifie ce que le système doit faire si la table existe sur l’abonné lors de l’application de l’instantané. *pre_creation_cmd* est **nvarchar (10)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**None**|Si la table existe déjà côté abonné, aucune action n'est effectuée.|  
|**delete**|Entraîne une suppression basée sur la clause WHERE dans le filtre de sous-ensemble.|  
|**DROP** (valeur par défaut)|Supprime la table avant de la recréer. Requis pour prendre en charge [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] abonnés.|  
|**truncate**|Tronque la table de destination.|  
  
`[ @creation_script = ] 'creation_script'` Est le chemin d’accès et le nom d’un script de schéma d’article facultatif utilisé pour créer l’article dans la base de données d’abonnement. *creation_script* est **nvarchar (255)**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Les scripts de création ne sont pas exécutés sur les Abonnés [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
`[ @schema_option = ] schema_option` Est un bitmap de l’option de génération de schéma pour l’article donné. *schema_option* est **Binary (8)** et peut être le [| (OR au niveau du bit) ](../../t-sql/language-elements/bitwise-or-transact-sql.md) produit d’une ou plusieurs des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0x00**|Désactive la génération de scripts par l’Agent d’instantané et utilise le script de précréation de schéma fourni défini dans *creation_script*.|  
|**0x01**|Génère la création d'objets (CREATE TABLE, CREATE PROCEDURE, etc.). Cette valeur est la valeur par défaut pour les articles de procédure stockée.|  
|**0x10**|Génère un index cluster correspondant. Même si cette option n'est pas activée, les index relatifs aux clés primaires et aux contraintes UNIQUE sont générés s'ils sont déjà définis sur une table publiée.|  
|**0x20**|Convertit les types de données définis par l'utilisateur (UDT) en types de données de base auprès de l'Abonné. Vous ne pouvez pas utiliser cette option lorsqu'il existe une contrainte CHECK ou DEFAULT sur une colonne de type défini par l'utilisateur (UDT), si une colonne UDT fait partie de la clé primaire, ou si une colonne calculée désigne une colonne UDT.|  
|**0x40**|Génère les index non-cluster correspondants. Même si cette option n'est pas activée, les index relatifs aux clés primaires et aux contraintes UNIQUE sont générés s'ils sont déjà définis sur une table publiée.|  
|**0x80**|Réplique les contraintes PRIMARY KEY. Tous les index relatifs à la contrainte sont également répliqués, même si options **0 x 10** et **0 x 40** ne sont pas activés.|  
|**0x100**|Réplique les déclencheurs utilisateur, si ceux-ci sont définis, sur un article de table.|  
|**0x200**|Réplique les contraintes FOREIGN KEY. Si la table référencée ne fait pas partie d'une publication, aucune contrainte FOREIGN KEY appliquée à une table publiée n'est répliquée.|  
|**0x400**|Réplique les contraintes CHECK.|  
|**0x800**|Réplique les valeurs par défaut.|  
|**0x1000**|Réplique le classement au niveau des colonnes.|  
|**0x2000**|Réplique les propriétés étendues associées à l'objet source de l'article publié.|  
|**0x4000**|Réplique les contraintes UNIQUE. Tous les index relatifs à la contrainte sont également répliqués, même si options **0 x 10** et **0 x 40** ne sont pas activés.|  
|**0x8000**|Cette option n'est pas valide pour les serveurs de publication qui exécutent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou des versions ultérieures.|  
|**0x10000**|Réplique les contraintes CHECK en tant que NOT FOR REPLICATION afin que les contraintes ne soient pas appliquées durant la synchronisation.|  
|**0x20000**|Réplique les contraintes FOREIGN KEY en tant que NOT FOR REPLICATION afin que les contraintes ne soient pas appliquées durant la synchronisation.|  
|**0x40000**|Réplique les groupes de fichiers associés à une table ou un index partitionné.|  
|**0x80000**|Réplique le schéma de partition d'une table partitionnée.|  
|**0x100000**|Réplique le schéma de partition d'un index partitionné.|  
|**0x200000**|Réplique les statistiques d'une table.|  
|**0x400000**|Réplique des liaisons par défaut.|  
|**0x800000**|Réplique des liaisons de règle.|  
|**0x1000000**|Réplique l’index de recherche en texte intégral.|  
|**0x2000000**|Collections de schéma XML liées aux **xml** colonnes ne sont pas répliquées.|  
|**0x4000000**|Réplique les index sur **xml** colonnes.|  
|**0x8000000**|Crée n'importe quel schéma qui n'est pas déjà présent sur l'abonné.|  
|**0x10000000**|Convertit **xml** colonnes à **ntext** sur l’abonné.|  
|**0x20000000**|Types de données de l’objet convertit volumineux (**nvarchar (max)**, **varchar (max)**, et **varbinary (max)**) introduite dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] aux types de données qui sont prises en charge sur [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].|  
|**0x40000000**|Réplique des autorisations.|  
|**0x80000000**|Tente de supprimer les dépendances à tous les objets ne faisant pas partie de la publication.|  
|**0x100000000**|Utilisez cette option pour répliquer l’attribut FILESTREAM s’il est spécifié sur **varbinary (max)** colonnes. Ne spécifiez pas cette option si vous répliquez des tables sur des Abonnés [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. La réplication de tables qui possèdent des colonnes FILESTREAM sur [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] abonnés n'est pas pris en charge, quelle que soit la façon dont cette option de schéma est définie. Consultez l’option connexe **0 x 800000000**.|  
|**0x200000000**|Convertit les types de données de date et heure (**date**, **temps**, **datetimeoffset**, et **datetime2**) introduite dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] aux données les types qui sont pris en charge sur les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**0x400000000**|Réplique l'option de compression pour les données et les index. Pour plus d’informations, consultez [Compression de données](../../relational-databases/data-compression/data-compression.md).|  
|**0x800000000**|Définissez cette option pour stocker les données FILESTREAM dans leur propre groupe de fichiers sur l'Abonné. Si cette option n'est pas définie, les données FILESTREAM sont stockées dans le groupe de fichiers par défaut. La réplication ne crée pas de groupes de fichiers ; par conséquent, si vous définissez cette option, vous devez créer le groupe de fichiers avant d'appliquer l'instantané à l'Abonné. Pour plus d’informations sur la création d’objets avant d’appliquer l’instantané, consultez [exécuter des Scripts avant et après l’instantané est appliqué](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).<br /><br /> Consultez l’option connexe **0 x 100000000**.|  
|**0x1000000000**|Convertit les types common language runtime (CLR) défini par l’utilisateur (UDT) **varbinary (max)** afin que les colonnes de type UDT puissent être répliquées sur les abonnés qui sont en cours d’exécution [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x2000000000**|Convertit le **hierarchyid** type de données à **varbinary (max)** afin que les colonnes de type **hierarchyid** peuvent être répliquées sur les abonnés qui sont en cours d’exécution [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour plus d’informations sur l’utilisation **hierarchyid** colonnes dans les tables répliquées, consultez [hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
|**0x4000000000**|Réplique tous les index filtrés sur la table. Pour plus d’informations sur les index filtrés, consultez [créer des index filtrés](../../relational-databases/indexes/create-filtered-indexes.md).|  
|**0x8000000000**|Convertit le **geography** et **geometry** types de données **varbinary (max)** afin que les colonnes de ces types peuvent être répliquées sur les abonnés qui sont en cours d’exécution [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x10000000000**|Réplique les index sur des colonnes de type **geography** et **geometry**.|  
  
 Si la valeur est NULL, le système génère automatiquement une option de schéma valide pour l'article. Le **Option de schéma par défaut** table dans la section Notes montre la valeur qui est choisie en fonction du type d’article. En outre, pas toutes *schema_option* valeurs sont valides pour chaque type de réplication et le type d’article. Le **Option de schéma valide** tableau donné dans la section Notes montre les options qui peuvent être spécifiées pour un type d’article donné.  
  
> [!NOTE]  
>  Le *schema_option* paramètre affecte uniquement les options de réplication pour l’instantané initial. Une fois que le schéma initial a été généré par l’Agent d’instantané et appliqué sur l’abonné, la réplication des modifications de schéma de publication à l’abonné se produisent en fonction des règles de réplication de modification de schéma et le *replicate_ddl* valeur du paramètre spécifié dans [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Pour plus d’informations, consultez [Modifier le schéma dans les bases de données de publication](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
`[ @subset_filterclause = ] 'subset_filterclause'` Une clause WHERE spécifiant le filtrage horizontal d’un article de table sans le mot WHERE inclus. *subset_filterclause* est de **nvarchar (1000)**, avec une valeur par défaut d’une chaîne vide.  
  
> [!IMPORTANT]  
>  Pour des raisons de performances, il est recommandé de ne pas appliquer de fonctions aux noms de colonnes dans les clauses de filtres de lignes paramétrables, comme `LEFT([MyColumn]) = SUSER_SNAME()`. Si vous utilisez [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) dans une clause de filtre et que vous remplacez la valeur HOST_NAME, vous devrez peut-être convertir des types de données à l’aide de [convertir](../../t-sql/functions/cast-and-convert-transact-sql.md). Pour plus d’informations sur les meilleures pratiques pour ce cas, consultez la section « Substitution de la valeur de HOST_NAME() » dans [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
`[ @article_resolver = ] 'article_resolver'` Est le programme de résolution COM utilisé pour résoudre les conflits sur l’article de table ou de l’assembly .NET Framework appelé pour exécuter une logique métier personnalisée sur l’article de table. *article_resolver* est **varchar (255)**, avec NULL comme valeur par défaut. Les valeurs disponibles pour ce paramètre sont répertoriées dans la liste des outils de résolution personnalisés [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Si la valeur fournie ne correspond pas à l'un des outils de résolution [!INCLUDE[msCoName](../../includes/msconame-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise l'outil de résolution spécifié et non celui qui est fourni par le système. Utilisez **sp_enumcustomresolvers** pour énumérer la liste des résolveurs personnalisés disponibles. Pour plus d’informations, consultez [exécuter une logique au cours de synchronisation de fusion](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md) et [Advanced Merge Replication Conflict Detection et résolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
`[ @resolver_info = ] 'resolver_info'` Permet de spécifier des informations supplémentaires requises par un résolveur personnalisé. Certains outils de résolution [!INCLUDE[msCoName](../../includes/msconame-md.md)] nécessitent une colonne en guise d'entrée. *resolver_info* est **nvarchar (255)**, avec NULL comme valeur par défaut. Pour plus d’informations, consultez [Programmes de résolution COM Microsoft](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md).  
  
`[ @source_owner = ] 'source_owner'` Est le nom du propriétaire de la *source_object*. *lui* est **sysname**, avec NULL comme valeur par défaut. Si la valeur NULL est affectée à l'argument, l'utilisateur actuel est supposé être le propriétaire.  
  
`[ @destination_owner = ] 'destination_owner'` Est le propriétaire de l’objet dans la base de données d’abonnement, si ce n’est pas « dbo ». *destination_owner* est **sysname**, avec NULL comme valeur par défaut. Si la valeur NULL est affectée à l'argument, « dbo » est supposé être le propriétaire.  
  
`[ @vertical_partition = ] 'column_filter'` Active et désactive le filtrage de colonne sur un article de table. *partition_verticale* est **nvarchar (5)** avec FALSE comme valeur par défaut.  
  
 **false** indique l’absence de filtrage vertical et publie toutes les colonnes.  
  
 **true** efface toutes les colonnes à l’exception de la clé primaire déclarée et des colonnes ROWGUID. Colonnes sont ajoutées à l’aide de **sp_mergearticlecolumn**.  
  
`[ @auto_identity_range = ] 'automatic_identity_range'` Active et désactive la gestion de cet article de table sur une publication lors de la création de plages d’identité automatique. *auto_identity_range* est **nvarchar (5)**, avec FALSE comme valeur par défaut. **true** permet la plage d’identité automatique gérant, tandis que **false** le désactive.  
  
> [!NOTE]  
>  *auto_identity_range* a été déconseillée et est fourni pour la compatibilité descendante uniquement. Vous devez utiliser *identityrangemanagementoption* pour spécifier les options de gestion de plage identité. Pour plus d’informations, consultez [ Répliquer des colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @pub_identity_range = ] pub_identity_range` Contrôle la taille de plage d’identité allouée à un abonné avec un abonnement serveur lors de la gestion de plages d’identité automatique est utilisée. Cette plage d'identité est réservée à un Abonné de republication qui peut l'allouer à ses propres Abonnés. *pub_identity_range* est **bigint**, avec NULL comme valeur par défaut. Vous devez spécifier ce paramètre si *identityrangemanagementoption* est **automatique** ou si *auto_identity_range* est **true**.  
  
`[ @identity_range = ] identity_range` Contrôle la taille de plage d’identité allouée à la fois au serveur de publication et à l’abonné lors de la gestion de plages d’identité automatique est utilisée. *identity_range* est **bigint**, avec NULL comme valeur par défaut. Vous devez spécifier ce paramètre si *identityrangemanagementoption* est **automatique** ou si *auto_identity_range* est **true**.  
  
> [!NOTE]  
>  *identity_range* contrôle la taille de plage d’identité sur les abonnés à l’aide de versions précédentes de republication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
`[ @threshold = ] threshold` Valeur de pourcentage qui contrôle le moment où l’Agent de fusion affecte une nouvelle plage d’identité. Lorsque le pourcentage de valeurs spécifié dans *seuil* est utilisé, l’Agent de fusion crée une nouvelle plage d’identité. *seuil* est **int**, avec NULL comme valeur par défaut. Vous devez spécifier ce paramètre si *identityrangemanagementoption* est **automatique** ou si *auto_identity_range* est **true**.  
  
`[ @verify_resolver_signature = ] verify_resolver_signature` Spécifie si une signature numérique est vérifiée avant d’utiliser un résolveur dans la réplication de fusion. *verify_resolver_signature* est **int**, avec 1 comme valeur par défaut.  
  
 **0** Spécifie que la signature ne sera pas vérifiée.  
  
 **1** indique que la signature est vérifiée pour s’il s’agit d’une source approuvée.  
  
`[ @destination_object = ] 'destination_object'` Est le nom de l’objet dans la base de données d’abonnement. *destination_object* est **sysname**, avec une valeur par défaut de ce qui est dans **@source_object**. Ce paramètre ne peut être spécifié que si l'article est un article de schéma exclusivement, tel que le sont les procédures stockées, vues et fonctions définies par l'utilisateur. Si l’article spécifié est un article de table, la valeur dans *@source_object* remplace la valeur dans *destination_object*.  
  
`[ @allow_interactive_resolver = ] 'allow_interactive_resolver'` Active ou désactive l’utilisation du résolveur interactif sur un article. *allow_interactive_resolver* est **nvarchar (5)**, avec FALSE comme valeur par défaut. **true** permet l’utilisation du résolveur interactif sur l’article ; **false** le désactive.  
  
> [!NOTE]  
>  L'outil de résolution interactif n'est pas pris en charge par les Abonnés [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
`[ @fast_multicol_updateproc = ] 'fast_multicol_updateproc'` Ce paramètre a été déconseillé et est conservé pour compatibilité descendante des scripts.  
  
`[ @check_permissions = ] check_permissions` Est un bitmap des autorisations au niveau des tables qui seront vérifiées lorsque l’Agent de fusion applique les modifications au serveur de publication. Si la connexion d'accès/le compte d'utilisateur du serveur de publication utilisé par le processus de fusion ne possède pas les autorisations de table appropriées, les modifications non valides sont enregistrées en tant que conflits. *check_permissions* est **int**et peut être le [| (OR au niveau du bit) ](../../t-sql/language-elements/bitwise-or-transact-sql.md) produit d’une ou plusieurs des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0 x 00** (valeur par défaut)|Les autorisations ne sont pas vérifiées.|  
|**0x10**|Les autorisations sont vérifiées sur le serveur de publication avant que les opérations d'insertion exécutées sur l'Abonné puissent être téléchargées.|  
|**0x20**|Les autorisations sont vérifiées sur le serveur de publication avant que les opérations de mise à jour exécutées sur l'Abonné puissent être téléchargées.|  
|**0x40**|Les autorisations sont vérifiées sur le serveur de publication avant que les opérations de suppression exécutées sur l'Abonné puissent être téléchargées.|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Confirme que l’action entreprise par cette procédure stockée peut invalider un instantané existant. *àce_invalidate_snapshot* est un **bits**, avec 0 comme valeur par défaut.  
  
 **0** indique que l’ajout d’un article n’entraîne pas l’instantané n’est pas valide. Si la procédure stockée détecte que la modification requiert un nouvel instantané, une erreur se produit et aucune modification n'est effectuée.  
  
 **1** Spécifie que l’option Ajout d’un article peut-être invalider l’instantané n’est pas valide et il existe des abonnements qui nécessitent un nouvel instantané, autorise l’instantané existant soit marqué comme obsolète et de générer un nouvel instantané. *àce_invalidate_snapshot* a la valeur **1** lors de l’ajout d’un article à une publication avec un instantané existant.  
  
`[ @published_in_tran_pub = ] 'published_in_tran_pub'` Indique qu’un article dans une publication de fusion est également publié dans une publication transactionnelle. *published_in_tran_pub* est **nvarchar (5)**, avec FALSE comme valeur par défaut. **true** indique que l’article est également publié dans une publication transactionnelle.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Confirme que l’action entreprise par cette procédure stockée peut nécessiter la réinitialisation des abonnements existants. *àce_reinit_subscription* est un **bits**, avec 0 comme valeur par défaut.  
  
 **0** indique que l’ajout d’un article n’entraîne pas la réinitialisation de l’abonnement. Si la procédure stockée détecte que la modification nécessite la réinitialisation des abonnements existants, une erreur se produit et aucune modification n'est effectuée.  
  
 **1** indique que les modifications apportées à l’article de fusion entraînent la réinitialisation des abonnements existants et autorise la réinitialisation des abonnements se produise. *àce_reinit_subscription* a la valeur **1** lorsque *subset_filterclause* spécifie un filtre de lignes paramétrable.  
  
`[ @logical_record_level_conflict_detection = ] 'logical_record_level_conflict_detection'` Spécifie le niveau de détection de conflit pour un article qui est membre d’un enregistrement logique. *logical_record_level_conflict_detection* est **nvarchar (5)**, avec FALSE comme valeur par défaut.  
  
 **true** Spécifie qu’un conflit sera détecté si des modifications sont apportées n’importe où dans l’enregistrement logique.  
  
 **false** Spécifie que la détection de conflit par défaut est utilisée comme spécifié par *column_tracking*. Pour plus d’informations, consultez [Regrouper les modifications apportées à des lignes connexes à l’aide d’enregistrements logiques](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  Étant donné que les enregistrements logiques ne sont pas pris en charge par [!INCLUDE[ssEW](../../includes/ssew-md.md)] abonnés, vous devez spécifier une valeur de **false** pour *logical_record_level_conflict_detection* pour prendre en charge ces abonnés.  
  
`[ @logical_record_level_conflict_resolution = ] 'logical_record_level_conflict_resolution'` Spécifie le niveau de résolution des conflits pour un article qui est membre d’un enregistrement logique. *logical_record_level_conflict_resolution* est **nvarchar (5)**, avec FALSE comme valeur par défaut.  
  
 **true** Spécifie que l’enregistrement logique gagnant complet remplace l’enregistrement logique perdant.  
  
 **false** Spécifie que les lignes gagnantes ne sont pas limitées à l’enregistrement logique. Si *logical_record_level_conflict_detection* est **true**, puis *logical_record_level_conflict_resolution* doit également être définie sur **true**. Pour plus d’informations, consultez [Regrouper les modifications apportées à des lignes connexes à l’aide d’enregistrements logiques](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  Étant donné que les enregistrements logiques ne sont pas pris en charge par [!INCLUDE[ssEW](../../includes/ssew-md.md)] abonnés, vous devez spécifier une valeur de **false** pour *logical_record_level_conflict_resolution* pour prendre en charge ces abonnés.  
  
`[ @partition_options = ] partition_options` Définit la façon dont les données de l’article sont partitionnées, ce qui permet d’optimiser les performances lorsque toutes les lignes appartiennent à une seule partition ou dans un seul abonnement. *partition_options* est **tinyint**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0** (valeur par défaut)|Le filtrage de l’article est statique ou ne produit pas un sous-ensemble unique de données pour chaque partition, autrement dit, une partition en « chevauchement ».|  
|**1**|Les partitions se chevauchent, et les mises à jour DML (langage de manipulation des données) effectuées sur l'abonné ne peuvent pas modifier la partition à laquelle une ligne appartient.|  
|**2**|Le filtrage de l'article produit des partitions qui ne se chevauchent pas, mais plusieurs abonnés peuvent recevoir la même partition.|  
|**3**|Le filtrage de l'article produit des partitions qui ne se chevauchent pas et qui sont uniques pour chaque abonnement.|  
  
> [!NOTE]  
>  Si la table source pour un article est déjà publiée dans une autre publication, la valeur de *partition_options* doivent être identiques pour les deux articles.  
  
`[ @processing_order = ] processing_order` Indique l’ordre de traitement des articles dans une publication de fusion. *processing_order* est **int**, avec 0 comme valeur par défaut. **0** Spécifie que l’article n’est pas ordonné, et toute autre valeur représente la valeur ordinale de l’ordre de traitement pour cet article. Les articles sont traités à partir de la valeur la plus faible vers la valeur la plus élevée. Si deux articles ont la même valeur, l’ordre de traitement est déterminé par l’ordre du surnom de l’article dans le [sysmergearticles](../../relational-databases/system-tables/sysmergearticles-transact-sql.md) (table système). Pour plus d’informations, consultez [Spécifier les propriétés de la réplication de fusion](../../relational-databases/replication/merge/specify-merge-replication-properties.md).  
  
`[ @subscriber_upload_options = ] subscriber_upload_options` Définit des restrictions sur les mises à jour effectuées sur un abonné avec un abonnement client. Pour plus d’informations, consultez [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md). *subscriber_upload_options* est **tinyint**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0** (valeur par défaut)|Aucune restriction. Les modifications sur l'abonné sont téléchargées par le serveur de publication.|  
|**1**|Les modifications sont autorisées sur l'abonné, mais elles ne sont pas téléchargées sur le serveur de publication.|  
|**2**|Les modifications ne sont pas autorisées sur l'abonné.|  
  
 Modification *subscriber_upload_options* nécessite l’abonnement pour réinitialisation en appelant [sp_reinitmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md).  
  
> [!NOTE]  
>  Si la table source pour un article est déjà publiée dans une autre publication, la valeur de *subscriber_upload_options* doivent être identiques pour les deux articles.  
  
`[ @identityrangemanagementoption = ] identityrangemanagementoption` Spécifie les modalités de gestion de plage d’identité pour l’article. *identityrangemanagementoption* est **nvarchar (10)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**None**|Désactive la gestion de plage d’identité.|  
|**manual**|Marque la colonne d'identité en utilisant NOT FOR REPLICATION pour activer la gestion manuelle des plages d'identité.|  
|**auto**|Spécifie la gestion automatique des plages d'identité.|  
|NULL(Default)|Valeur par défaut est **aucun**lorsque la valeur de *auto_identity_range* n’est pas **true**.|  
  
 Pour la compatibilité descendante, lorsque la valeur de *identityrangemanagementoption* est NULL, la valeur de *auto_identity_range* est activée. Toutefois, lorsque la valeur de *identityrangemanagementoption* n’est pas NULL, alors la valeur de *auto_identity_range* est ignoré. Pour plus d’informations, consultez [ Répliquer des colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
`[ @delete_tracking = ] 'delete_tracking'` Indique si les suppressions sont répliquées. *delete_tracking* est **nvarchar (5)**, avec TRUE comme valeur par défaut. **false** indique que les suppressions ne sont pas répliquées, et **true** indique que les suppressions sont répliquées, ce qui correspond au comportement normal pour la réplication de fusion. Lorsque *delete_tracking* a la valeur **false**, de lignes supprimées sur l’abonné doivent être supprimées manuellement sur le serveur de publication et de lignes supprimées sur le serveur de publication doivent être supprimées manuellement sur l’abonné.  
  
> [!IMPORTANT]  
>  Paramètre *delete_tracking* à **false** entraîne une non-convergence. Si la table source pour un article est déjà publiée dans une autre publication, la valeur de *delete_tracking* doivent être identiques pour les deux articles.  
  
> [!NOTE]  
>  *delete_tracking* options ne peuvent pas être définies à l’aide de la **Assistant Nouvelle Publication** ou **propriétés de la Publication** boîte de dialogue.  
  
`[ @compensate_for_errors = ] 'compensate_for_errors'` Indique si des actions de compensation sont entreprises lorsque des erreurs sont rencontrées lors de la synchronisation. *compensate_for_errors je*s **nvarchar (5)**, avec FALSE comme valeur par défaut. Lorsque la valeur **true**, modifications qui ne peut pas être appliqué à un abonné ou serveur de publication pendant la synchronisation toujours entraîner actions de compensation pour annuler la modification ; Toutefois, un configuré incorrectement abonné qui génère une erreur de peut entraîner des modifications à d’autres abonnés et les éditeurs à être annulée. **false** désactive ces actions de compensation, toutefois, les erreurs sont toujours consignés comme avec la compensation et les fusions suivantes continue à appliquer les modifications jusqu'à sa réussite.  
  
> [!IMPORTANT]  
>  Bien que les données des lignes affectées puissent sembler être hors de convergence, dès que vous résolvez une erreur, des modifications peuvent être appliquées et les données convergent. Si la table source pour un article est déjà publiée dans une autre publication, la valeur de *compensate_for_errors* doivent être identiques pour les deux articles.  
  
`[ @stream_blob_columns = ] 'stream_blob_columns'` Spécifie qu’une optimisation de flux de données être utilisé lors de la réplication de colonnes d’objets binaires volumineux. *stream_blob_columns* est **nvarchar (5)**, avec FALSE comme valeur par défaut. **true** signifie que l’optimisation sera tentée. *stream_blob_columns* est définie sur true lorsque FILESTREAM est activé. Cela permet la réplication des données FILESTREAM dans le but d'optimiser et de réduire l'utilisation de la mémoire. Pour forcer les articles de table FILESTREAM à ne pas utiliser le flux d’objet blob, utilisez **sp_changemergearticle** pour définir *stream_blob_columns* avec la valeur false.  
  
> [!IMPORTANT]  
>  L'activation de cette optimisation de mémoire peut réduire les performances de l'Agent de fusion pendant la synchronisation. Cette option ne doit être utilisée que lors de la réplication de colonnes contenant des mégaoctets de données.  
  
> [!NOTE]  
>  Certaines fonctionnalités de réplication de fusion, telles que les enregistrements logiques, peuvent encore empêcher l’optimisation de flux utilisée lors de la réplication des objets binaires volumineux même avec *stream_blob_columns* la valeur **true**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addmergearticle** est utilisé dans la réplication de fusion.  
  
 Lorsque vous publiez des objets, leurs définitions sont copiées sur les abonnés. Si vous publiez un objet de base de données qui dépend d'un ou de plusieurs autres objets, vous devez publier tous les objets référencés. Par exemple, si vous publiez une vue qui dépend d'une table, vous devez publier la table également.  
  
 Si vous spécifiez une valeur de **3** pour *partition_options*, il peut y avoir qu’un seul abonnement pour chaque partition de données de cet article. Si un deuxième abonnement est créé dans lequel le critère de filtrage du nouvel abonnement produit la même partition que l'abonnement existant, ce dernier est supprimé.  
  
 Lorsque vous spécifiez une valeur de 3 pour *partition_options*, métadonnées sont nettoyées à chaque fois que l’Agent de fusion s’exécute et l’instantané partitionné expire plus rapidement. Lorsque vous utilisez cette option, pensez à activer l'instantané partitionné requis par l'abonné. Pour plus d'informations, voir [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 Ajout d’un article avec un filtre horizontal statique, à l’aide de *subset_filterclause*, à une publication existante avec les articles possèdent des filtres paramétrés nécessite la réinitialisation des abonnements.  
  
 Lorsque vous spécifiez *processing_order*, nous vous recommandons de conserver des écarts entre les valeurs d’ordre de l’article, ce qui le rend plus facile de définir de nouvelles valeurs à l’avenir. Par exemple, si vous avez trois articles Article1, Article2 et Article3, définissez *processing_order* 10, 20 et 30, plutôt que 1, 2 et 3. Pour plus d’informations, consultez [Spécifier les propriétés de la réplication de fusion](../../relational-databases/replication/merge/specify-merge-replication-properties.md).  
  
## <a name="default-schema-option-table"></a>Tableau des options de schéma par défaut  
 Ce tableau décrit la valeur par défaut qui est définie par la procédure stockée si une valeur NULL est spécifiée pour *schema_option*, qui varie selon le type d’article.  
  
|Type de l'article|Valeur de l'option de schéma|  
|------------------|-------------------------|  
|**schéma de Func uniquement**|**0x01**|  
|**schéma de vue indexée uniquement**|**0x01**|  
|**proc schéma uniquement**|**0x01**|  
|**table**|**0x0C034FD1**  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et publications ultérieures compatibles avec un instantané en mode natif.<br /><br /> **0x08034FF1**  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et publications ultérieures compatibles avec un instantané de mode caractère.|  
|**afficher le schéma uniquement**|**0x01**|  
  
> [!NOTE]  
>  Si la publication prend en charge les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l’option de schéma par défaut pour **table** est **0x30034FF1**.  
  
## <a name="valid-schema-option-table"></a>Tableau des options de schéma valides  
 Le tableau suivant décrit les valeurs autorisées *schema_option* selon le type d’article.  
  
|Type de l'article|Valeurs de l'option de schéma|  
|------------------|--------------------------|  
|**schéma de Func uniquement**|**0 x 01** et **0 x 2000**|  
|**schéma de vue indexée uniquement**|**0 x 01**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0x1000000**et **0x200000**|  
|**proc schéma uniquement**|**0 x 01** et **0 x 2000**|  
|**table**|Toutes les options.|  
|**afficher le schéma uniquement**|**0 x 01**, **0 x 040**, **0 x 0100**, **0 x 2000**, **0 x 40000**, **0x1000000**et **0x200000**|  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-addmergearticle-trans_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance au rôle de serveur fixe **sysadmin** ou au rôle de base de données fixe **db_owner** .  
  
## <a name="see-also"></a>Voir aussi  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Répliquer des colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_dropmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
