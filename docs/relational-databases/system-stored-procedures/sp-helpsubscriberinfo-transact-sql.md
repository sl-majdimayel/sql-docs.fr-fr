---
title: sp_helpsubscriberinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpsubscriberinfo
- sp_helpsubscriberinfo_TSQL
helpviewer_keywords:
- sp_helpsubscriberinfo
ms.assetid: fbabe1ec-57cf-425c-bae7-af7f5d3198fd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 18a1de1e3b7dc1f312094a9023e0af9df014214b
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526371"
---
# <a name="sphelpsubscriberinfo-transact-sql"></a>sp_helpsubscriberinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche des informations relatives à un Abonné. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpsubscriberinfo [ [ @subscriber =] 'subscriber']  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @subscriber = ] 'subscriber'` Est le nom de l’abonné. *abonné* est **sysname**, avec une valeur par défaut **%**, qui retourne toutes les informations.  
  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *serveur de publication* est **sysname**et la valeur par défaut est le nom du serveur actuel.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être spécifié, sauf si elle est un serveur de publication Oracle.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Nom du serveur de publication.|  
|**subscriber** (Abonné)|**sysname**|Nom de l'Abonné.|  
|**type**|**tinyint**|Type d'Abonné :<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données **1** = source de données ODBC|  
|**login**|**sysname**|ID de connexion pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.|  
|**password**|**sysname**|Mot de passe pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.|  
|**commit_batch_size**|**Int**|Non pris en charge.|  
|**status_batch_size**|**Int**|Non pris en charge.|  
|**flush_frequency**|**Int**|Non pris en charge.|  
|**frequency_type**|**Int**|Fréquence d'exécution de l’Agent de distribution :<br /><br /> **1** = une fois<br /><br /> **2** = à la demande<br /><br /> **4** = quotidienne<br /><br /> **8** = hebdomadaire<br /><br /> **16** = Monthly<br /><br /> **32** = fréquence mensuelle relative<br /><br /> **64** = démarrage automatique<br /><br /> **128** = périodique|  
|**frequency_interval**|**Int**|Valeur appliquée à la fréquence définie par *frequency_type*.|  
|**frequency_relative_interval**|**Int**|Date de l’Agent de Distribution utilisée lorsque *frequency_type* a la valeur **32** (fréquence mensuelle relative) :<br /><br /> **1** = premier<br /><br /> **2** = seconde<br /><br /> **4** = troisième<br /><br /> **8** = quatrième<br /><br /> **16** = dernier|  
|**frequency_recurrence_factor**|**Int**|Facteur de récurrence utilisé par *frequency_type*.|  
|**frequency_subday**|**Int**|Fréquence de replanification nécessaire pendant la période définie :<br /><br /> **1** = une fois<br /><br /> **2** = seconde<br /><br /> **4** = minute<br /><br /> **8** = heure|  
|**frequency_subday_interval**|**Int**|Intervalle pour *frequency_subday*.|  
|**active_start_time_of_day**|**Int**|Heure de la journée lorsque l’Agent de Distribution est planifié pour la première, au format HHMMSS.|  
|**active_end_time_of_day**|**Int**|Heure à laquelle l’Agent de distribution cesse d'être planifié, au format HHMMSS.|  
|**active_start_date**|**Int**|Date à laquelle l’Agent de Distribution tout d’abord, au format AAAAMMJJ.|  
|**active_end_date**|**Int**|Date à laquelle l’Agent de Distribution cesse d’être planifié, au format AAAAMMJJ.|  
|**retryattempt**|**Int**|Non pris en charge.|  
|**retrydelay**|**Int**|Non pris en charge.|  
|**description**|**nvarchar(255)**|Texte de description de l'Abonné.|  
|**security_mode**|**Int**|Mode de sécurité implémenté :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] l’authentification Windows|  
|**frequency_type2**|**Int**|Fréquence d'exécution de l’Agent de fusion :<br /><br /> **1** = une fois<br /><br /> **2** = à la demande<br /><br /> **4** = quotidienne<br /><br /> **8** = hebdomadaire<br /><br /> **16** = Monthly<br /><br /> **32** = fréquence mensuelle relative<br /><br /> **64** = démarrage automatique<br /><br /> **128** = périodique|  
|**frequency_interval2**|**Int**|Valeur appliquée à la fréquence définie par *frequency_type*.|  
|**frequency_relative_interval2**|**Int**|Date de l’Agent de fusion utilisée lorsque *frequency_type* a la valeur 32 (fréquence mensuelle relative) :<br /><br /> **1** = premier<br /><br /> **2** = seconde<br /><br /> **4** = troisième<br /><br /> **8** = quatrième<br /><br /> **16** = dernier|  
|**frequency_recurrence_factor2**|**Int**|Facteur de récurrence utilisé par *frequency_type **.*|  
|**frequency_subday2**|**Int**|Fréquence de replanification nécessaire pendant la période définie :<br /><br /> **1** = une fois<br /><br /> **2** = seconde<br /><br /> **4** = minute<br /><br /> **8** = heure|  
|**frequency_subday_interval2**|**Int**|Intervalle pour *frequency_subday*.|  
|**active_start_time_of_day2**|**Int**|Heure à laquelle l’Agent de fusion est planifié pour la première fois, au format HHMMSS.|  
|**active_end_time_of_day2**|**Int**|Heure de la journée à laquelle l’Agent de fusion cesse d’être planifié, au format HHMMSS.|  
|**active_start_date2**|**Int**|Date à laquelle l’Agent de fusion est planifié pour la première fois, au format AAAAMMJJ.|  
|**active_end_date2**|**Int**|Date à laquelle l’Agent de fusion cesse d'être planifié, au format AAAAMMJJ.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpsubscriberinfo** est utilisé dans la réplication de capture instantanée, la réplication transactionnelle et la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe le **db_owner** rôle de base de données fixe ou de la liste d’accès à la publication peut exécuter **sp_helpsubscriberinfo**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_changesubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
