---
title: SYSSUBSCRIPTIONS (vue système) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- syssubscriptions_TSQL
- syssubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syssubscriptions view
ms.assetid: c9613858-9512-43a9-aa53-7ee8064f064c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 529572f02568cb7e13ff8821ab8d48a86d908141
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52783451"
---
# <a name="syssubscriptions-system-view-transact-sql"></a>syssubscriptions (System View) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **syssubscriptions** vue expose des informations d’abonnement. Cette vue est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**Int**|ID unique d'un article ayant fait l'objet de l'abonnement.|  
|**srvid**|**smallint**|L’ID de serveur de l’abonné.|  
|**dest_db**|**sysname**|Le nom de la base de données d’abonnement.|  
|**status**|**tinyint**|L’état de l’abonnement :<br /><br /> **0** = inactif.<br /><br /> **1** = abonné.<br /><br /> **2** = actif.|  
|**sync_type**|**tinyint**|Type de synchronisation initiale :<br /><br /> **1** = automatique.<br /><br /> **2** = none.|  
|**login_name**|**sysname**|Spécifie le nom de connexion utilisé lors de la connexion au serveur de publication pour ajouter l'abonnement.|  
|**subscription_type**|**Int**|Le type d’abonnement :<br /><br /> **0** = push - l’agent de distribution s’exécute sur le serveur de distribution.<br /><br /> **1** = par extraction - l’agent de distribution s’exécute sur l’abonné.|  
|**distribution_jobid**|**binary (16)**|Identifie la tâche de l'Agent de distribution utilisée pour synchroniser l'abonnement.|  
|**timestmap**|**timestamp**|Date et heure de création de l'abonnement.|  
|**update_mode**|**tinyint**|Mode de mise à jour :<br /><br /> **0** = lecture seule.<br /><br /> **1** = mise à jour immédiate.|  
|**loopback_detection**|**bit**|S'applique aux abonnements qui font partie d'une topologie de réplication transactionnelle bidirectionnelle. La détection de boucle détermine si l'Agent de distribution renvoie à l'Abonné les transactions émanant de ce dernier :<br /><br /> **0** = renvoie les transactions.<br /><br /> **1** = ne pas renvoyer.|  
|**queued_reinit**|**bit**|Indique si l'article est marqué pour l'initialisation ou la réinitialisation. La valeur **1** indique que l’abonnement à l’article est marqué pour l’initialisation ou la réinitialisation.|  
|**nosync_type**|**tinyint**|Type d'initialisation de l'abonnement :<br /><br /> **0** = automatique (instantané)<br /><br /> **1** = prise en charge de la réplication uniquement<br /><br /> **2** = initialiser avec une sauvegarde<br /><br /> **3** = initialiser à partir du numéro de séquence de journal (LSN)<br /><br /> Pour plus d’informations, consultez le **@sync_type** paramètre de [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md).<br /><br /> **3** = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**srvname**|**sysname**|Nom de l'Abonné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [syssubscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-tables/syssubscriptions-transact-sql.md)  
  
  
