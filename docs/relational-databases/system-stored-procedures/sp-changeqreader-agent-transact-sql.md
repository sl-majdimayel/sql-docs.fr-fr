---
title: sp_changeqreader_agent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changeqreader_agent_TSQL
- sp_changeqreader_agent
helpviewer_keywords:
- sp_changeqreader_agent
ms.assetid: d3fe79c5-31ef-4565-bf38-b476b5fb16f7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 994ec0ee8fa6cd5424f808d884eb3355ffdc22ba
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526121"
---
# <a name="spchangeqreaderagent-transact-sql"></a>sp_changeqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés de sécurité d'un Agent de lecture de la file d'attente. Cette procédure stockée est exécutée sur la base de données de distribution du serveur de distribution ou sur la base de publication du serveur de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changeqreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_login = ] 'job_login'` Nom de connexion pour le [!INCLUDE[msCoName](../../includes/msconame-md.md)] du compte Windows sous lequel l’agent s’exécute. *job_login* est **nvarchar (257)**, avec NULL comme valeur par défaut.  
  
`[ @job_password = ] 'job_password'` Est le mot de passe pour le compte Windows sous lequel l’agent s’exécute. *job_password* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @frompublisher = ] frompublisher` Indique si la procédure est exécutée sur le serveur de publication. *frompublisher* est de type bit, avec la valeur par défaut **0**. La valeur **1** signifie que la procédure est en cours d’exécution du serveur de publication sur la base de données de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changeqreader_agent** est utilisé dans la réplication transactionnelle.  
  
 **sp_changeqreader_agent** est utilisé pour modifier le compte Windows sous lequel s’exécute un agent de lecture de file d’attente. Vous pouvez changer le mot de passe d'une connexion Windows existante ou fournir une nouvelle connexion et un nouveau mot de passe Windows.  
  
 Après avoir modifié le nom de connexion ou le mot de passe d'un Agent, vous devez arrêter et redémarrer celui-ci avant que la modification prenne effet.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_changeqreader_agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les paramètres de sécurité de la réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addqreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
  
