---
title: sp_getqueuedrows (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getqueuedrows_TSQL
- sp_getqueuedrows
helpviewer_keywords:
- sp_getqueuedrows
ms.assetid: 139e834f-1988-4b4d-ac81-db1f89ea90e8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fa6ce6b4e0d1c3fbefe7256f3ca96c84d59e664d
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535411"
---
# <a name="spgetqueuedrows-transact-sql"></a>sp_getqueuedrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Extrait, de l'Abonné, les lignes pour lesquelles il existe des mises à jour dans la file d'attente. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_getqueuedrows [ @tablename = ] 'tablename'  
    [ , [ @owner = ] 'owner'  
    [ , [ @tranid = ] 'transaction_id' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @tablename = ] 'tablename'` Est le nom de la table. *TableName* est **sysname**, sans valeur par défaut. La table doit faire partie d'un abonnement en file d'attente.  
  
`[ @owner = ] 'owner'` Est le propriétaire de l’abonnement. *propriétaire* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @tranid = ] 'transaction_id'` Permet à la sortie à filtrer par ID de transaction. *transaction_id* est **nvarchar (70)**, avec NULL comme valeur par défaut. Si cet argument est défini, l'identificateur de transaction associé à la commande placée en file d'attente est affiché. Si la valeur est NULL, toutes les commandes figurant dans la file d'attente sont affichées.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Affiche toutes les lignes détenant actuellement au moins une transaction en attente pour la table d'abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**Action**|**nvarchar(10)**|Type d'action à appliquer au moment de la synchronisation.<br /><br /> INS= insertion <br /><br /> DEL = suppression<br /><br /> UPD = mise à jour|  
|**Tranid**|**nvarchar(70)**|Identificateur de transaction sous lequel la commande a été exécutée.|  
|**Colonne1 table... n**||La valeur pour chaque colonne de la table spécifiée dans *tablename*.|  
|**msrepl_tran_version**|**uniqueidentifier**|Cette colonne permet d'assurer le suivi des modifications apportées aux données répliquées et de détecter les conflits sur le serveur de publication. Cette colonne est automatiquement ajoutée à la table.|  
  
## <a name="remarks"></a>Notes  
 **sp_getqueuedrows** est utilisé sur les abonnés concernés dans la mise à jour en file d’attente.  
  
 **sp_getqueuedrows** recherche les lignes d’une table donnée sur un abonnement de base de données qui ont participé à une mise à jour en file d’attente, mais actuellement pas résolues par l’agent de lecture de file d’attente.  
  
## <a name="permissions"></a>Autorisations  
 **sp_getqueuedrows** requiert des autorisations SELECT sur la table spécifiée dans *tablename*.  
  
## <a name="see-also"></a>Voir aussi  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Détection et résolution des conflits de mise à jour en attente](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
