---
title: sp_audit_write (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_audit_write
- sp_audit_write_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_audit_write
ms.assetid: 4c523848-1ce6-49ad-92b3-e0e90f24f1c2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 23520ce686562e7ed2f45e87aa4717135dd1ab8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732897"
---
# <a name="spauditwrite-transact-sql"></a>sp_audit_write (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Ajoute un événement d’audit défini par l’utilisateur à la **USER_DEFINED_AUDIT_GROUP**. Si **USER_DEFINED_AUDIT_GROUP** n’est pas activé, **sp_audit_write** est ignoré.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_audit_write [ @user_defined_event_id =  ] user_defined_event_id ,   
        [ @succeeded =  succeeded   
    [ , [ @user_defined_information =  ] 'user_defined_information' ]   
    [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 **@user_defined_event_id**  
 Un paramètre défini par l’utilisateur et enregistré dans le **user_defined_event_id** colonne du journal d’audit. *@user_defined_event_id* est de type **smallint**.  
  
 **@succeeded**  
 Paramètre passé par l'utilisateur pour indiquer si l'événement a ou non réussi. Il apparaît dans la colonne succeeded du journal d'audit. *@succeeded* est **bits**.  
  
 **@user_defined_information**  
 Texte défini par l'utilisateur et enregistré dans la nouvelle colonne user_defined_event_id du journal d'audit. *@user_defined_information* est **nvarchar (4000)**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
 Les échecs sont dus à des paramètres d'entrée incorrects ou à l'impossibilité d'écrire dans le journal d'audit cible.  
  
## <a name="remarks"></a>Notes  
 Lorsque le **USER_DEFINED_AUDIT_GROUP** est ajouté à une spécification d’audit de serveur ou une spécification d’audit de base de données, l’événement déclenché par **sp_audit_write** figureront dans le journal d’audit.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **public** rôle de base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-user-defined-audit-event-with-informational-text"></a>A. Création d'un événement d'audit défini par l'utilisateur avec du texte informatif  
 L'exemple suivant crée un événement d'audit présentant l'ID 27 et la valeur de réussite 0. Il inclut un texte informatif facultatif.  
  
```  
EXEC sp_audit_write @user_defined_event_id =  27 ,   
              @succeeded =  0   
            , @user_defined_information = N'Access to a monitored object.' ;  
```  
  
### <a name="b--creating-a-user-defined-audit-event-without-informational-text"></a>B.  Création d'un événement d'audit défini par l'utilisateur sans texte informatif  
 L'exemple suivant crée un événement d'audit présentant l'ID 27 et la valeur de réussite 0. Il n'inclut pas de texte informatif facultatif ou de noms de paramètres optionnels.  
  
```  
EXEC sp_audit_write 27, 0;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
