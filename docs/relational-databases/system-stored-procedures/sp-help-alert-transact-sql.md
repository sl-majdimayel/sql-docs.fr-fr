---
title: sp_help_alert (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_alert
- sp_help_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_alert
ms.assetid: 850cef4e-6348-4439-8e79-fd1bca712091
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bca9c53780bb3258f73a274240c0bb5e63e126c3
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538461"
---
# <a name="sphelpalert-transact-sql"></a>sp_help_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur les alertes définies pour le serveur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_alert [ [ @alert_name = ] 'alert_name' ]   
     [ , [ @order_by = ] 'order_by' ]   
     [ , [ @alert_id = ] alert_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @legacy_format = ] legacy_format ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @alert_name = ] 'alert_name'` Le nom de l’alerte. *nom_alerte* est **nvarchar (128)**. Si *nom_alerte* est ne pas spécifié, les informations sur toutes les alertes sont renvoyées.  
  
`[ @order_by = ] 'order_by'` L’ordre de tri à appliquer pour obtenir les résultats. *Trier par*est **sysname**, avec une valeur par défaut de N '*nom*».  
  
`[ @alert_id = ] alert_id` Le numéro d’identification de l’alerte à des informations de rapport. *alert_id*est **int**, avec NULL comme valeur par défaut.  
  
`[ @category_name = ] 'category'` La catégorie de l’alerte. *catégorie* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @legacy_format = ] legacy_format` S’il faut générer un jeu de résultats hérité est. *legacy_format* est **bits**, avec une valeur par défaut **0**. Lorsque *legacy_format* est **1**, **sp_help_alert** retourne le jeu de résultats retourné par **sp_help_alert** dans Microsoft SQL Server 2000.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Lorsque **@legacy_format** est **0**, **sp_help_alert** produit le jeu de résultats suivant.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|Identificateur entier unique attribué par le système.|  
|**nom**|**sysname**|Nom de l'alerte (par exemple Demo : Complète **msdb** journal).|  
|**event_source**|**nvarchar(100)**|Source de l'événement. Il s’agit toujours **MSSQLServer** pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0|  
|**event_category_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**Int**|Numéro du message d'erreur définissant l'alerte (Correspond généralement à un numéro d’erreur dans le **sysmessages** table). Si le niveau de gravité est utilisé pour définir l’alerte, **message_id** est **0** ou NULL.|  
|**severity**|**Int**|Niveau de gravité (à partir de **9** via **25**, **110**, **120**, **130**, ou **140**) qui définit l’alerte.|  
|**enabled**|**tinyint**|État si l’alerte est actuellement activé (**1**) ou non (**0**). Une alerte non activée ne peut pas être envoyée.|  
|**delay_between_responses**|**Int**|Délai d'attente, en secondes, entre les réponses à l'alerte.|  
|**last_occurrence_date**|**Int**|Date de la dernière apparition de l'alerte.|  
|**last_occurrence_time**|**Int**|Heure de la dernière apparition de l'alerte.|  
|**last_response_date**|**Int**|Date de dernière de l’alerte a répondu à par le **SQLServerAgent** service.|  
|**last_response_time**|**Int**|Heure de l’alerte dernière reçu la réponse de la **SQLServerAgent** service.|  
|**notification_message**|**nvarchar(512)**|Message supplémentaire facultatif qui sera envoyé à l'opérateur avec la notification par courrier électronique ou radiomessagerie.|  
|**include_event_description**|**tinyint**|Indique si la description de l'erreur de SQL Server contenue dans le journal des applications Windows doit apparaître dans le message de notification.|  
|**database_name**|**sysname**|Base de données dans laquelle l'erreur doit apparaître pour que l'alerte soit déclenchée. Si le nom de la base de données est NULL, l'alerte se déclenche où que se soit produite l'erreur.|  
|**event_description_keyword**|**nvarchar(100)**|Description de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le journal des applications Windows qui doit être identique à la séquence de caractères fournie.|  
|**occurrence_count**|**Int**|Nombre de déclenchements de l'alerte.|  
|**count_reset_date**|**Int**|Date de la **occurrence_count** dernière réinitialisation.|  
|**count_reset_time**|**Int**|Temps le **occurrence_count** dernière réinitialisation.|  
|**job_id**|**uniqueidentifier**|Numéro d'identification du travail à exécuter en réponse à une alerte.|  
|**job_name**|**sysname**|Nom du travail à exécuter en réponse à une alerte.|  
|**has_notification**|**Int**|Différent de zéro si un ou plusieurs opérateurs sont notifiés pour cette alerte. Le paramètre peut avoir les valeurs suivantes (liées par OR) :<br /><br /> **1**=has e-mail notification<br /><br /> **2**= notification par radiomessagerie<br /><br /> **4**= a **net send** notification.|  
|**flags**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**performance_condition**|**nvarchar(512)**|Si **type** est **2**, cette colonne indique la définition de la condition de performances ; sinon, la colonne est NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Sera toujours '[Uncategorized]' pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.|  
|**wmi_namespace**|**sysname**|Si **type** est **3**, cette colonne indique l’espace de noms pour l’événement WMI.|  
|**wmi_query**|**nvarchar(512)**|Si **type** est **3**, cette colonne affiche la requête pour l’événement WMI.|  
|**type**|**Int**|Type de l'événement :<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerte d’événement<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerte de performances<br /><br /> **3** = alerte d’événement WMI|  
  
 Lorsque **@legacy_format** est **1**, **sp_help_alert** produit le jeu de résultats suivant.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|Identificateur entier unique attribué par le système.|  
|**nom**|**sysname**|Nom de l'alerte (par exemple Demo : Complète **msdb** journal).|  
|**event_source**|**nvarchar(100)**|Source de l'événement. Il s’agit toujours **MSSQLServer** pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0|  
|**event_category_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**Int**|Numéro du message d'erreur définissant l'alerte (Correspond généralement à un numéro d’erreur dans le **sysmessages** table). Si le niveau de gravité est utilisé pour définir l’alerte, **message_id** est **0** ou NULL.|  
|**severity**|**Int**|Niveau de gravité (à partir de **9** via **25**, **110**, **120**, **130**, ou 1**40**) qui définit l’alerte.|  
|**enabled**|**tinyint**|État si l’alerte est actuellement activé (**1**) ou non (**0**). Une alerte non activée ne peut pas être envoyée.|  
|**delay_between_responses**|**Int**|Délai d'attente, en secondes, entre les réponses à l'alerte.|  
|**last_occurrence_date**|**Int**|Date de la dernière apparition de l'alerte.|  
|**last_occurrence_time**|**Int**|Heure de la dernière apparition de l'alerte.|  
|**last_response_date**|**Int**|Date de dernière de l’alerte a répondu à par le **SQLServerAgent** service.|  
|**last_response_time**|**Int**|Heure de l’alerte dernière reçu la réponse de la **SQLServerAgent** service.|  
|**notification_message**|**nvarchar(512)**|Message supplémentaire facultatif qui sera envoyé à l'opérateur avec la notification par courrier électronique ou radiomessagerie.|  
|**include_event_description**|**tinyint**|Indique si la description de l'erreur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenue dans le journal des applications Windows doit apparaître dans le message de notification.|  
|**database_name**|**sysname**|Base de données dans laquelle l'erreur doit apparaître pour que l'alerte soit déclenchée. Si le nom de la base de données est NULL, l'alerte se déclenche où que se soit produite l'erreur.|  
|**event_description_keyword**|**nvarchar(100)**|Description de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le journal des applications Windows qui doit être identique à la séquence de caractères fournie.|  
|**occurrence_count**|**Int**|Nombre de déclenchements de l'alerte.|  
|**count_reset_date**|**Int**|Date de la **occurrence_count** dernière réinitialisation.|  
|**count_reset_time**|**Int**|Temps le **occurrence_count** dernière réinitialisation.|  
|**job_id**|**uniqueidentifier**|Numéro d’identification du travail.|  
|**job_name**|**sysname**|Nom d'un travail à la demande exécuté en réponse à une alerte.|  
|**has_notification**|**Int**|Différent de zéro si un ou plusieurs opérateurs sont notifiés pour cette alerte. Le paramètre peut avoir une ou plusieurs des valeurs suivantes (combinées avec OR) :<br /><br /> **1**=has e-mail notification<br /><br /> **2**= notification par radiomessagerie<br /><br /> **4**= a **net send** notification.|  
|**flags**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] .|  
|**performance_condition**|**nvarchar(512)**|Si **type** est **2**, cette colonne indique la définition de la condition de performances. Si **type** est **3**, cette colonne affiche la requête pour l’événement WMI. Dans les autres cas, cette colonne est NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Sera toujours '**[Uncategorized]**' pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.|  
|**type**|**Int**|Type d'alerte :<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerte d’événement<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerte de performances<br /><br /> **3** = alerte d’événement WMI|  
  
## <a name="remarks"></a>Notes  
 **sp_help_alert** doit être exécuté à partir de la **msdb** base de données.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
 Pour plus d’informations sur **SQLAgentOperatorRole**, consultez [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des informations sur l'alerte `Demo: Sev. 25 Errors`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_update_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
