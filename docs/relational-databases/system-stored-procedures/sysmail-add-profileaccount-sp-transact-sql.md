---
title: sysmail_add_profileaccount_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_profileaccount_sp
- sysmail_add_profileaccount_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profileaccount_sp
ms.assetid: 7cbf430f-1997-45ea-9707-0086184de744
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 44dc2d5341e536179fe0bf6ef152ef7d39afe966
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532101"
---
# <a name="sysmailaddprofileaccountsp-transact-sql"></a>sysmail_add_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un compte de messagerie de base de données à un profil de messagerie de base de données. Exécutez **sysmail_add_profileaccount_sp** une fois un compte de base de données est créé avec [sysmail_add_account_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md), et un profil de base de données est créé avec [sysmail_add_profile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_add_profileaccount_sp { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }  
    [ , [ @sequence_number = ] sequence_number ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @profile_id = ] profile_id` Identificateur du profil auquel le compte est ajouté. *profile_id* est **int**, avec NULL comme valeur par défaut. Soit le *profile_id* ou *profile_name* doit être spécifié.  
  
`[ @profile_name = ] 'profile_name'` Le nom du profil auquel le compte est ajouté. *nom_profil* est **sysname**, avec NULL comme valeur par défaut. Soit le *profile_id* ou *profile_name* doit être spécifié.  
  
`[ @account_id = ] account_id` Id de compte à ajouter au profil. *account_id* est **int**, avec NULL comme valeur par défaut. Soit le *account_id* ou *account_name* doit être spécifié.  
  
`[ @account_name = ] 'account_name'` Le nom du compte à ajouter au profil. *nom_compte* est **sysname**, avec NULL comme valeur par défaut. Soit le *account_id* ou *account_name* doit être spécifié.  
  
`[ @sequence_number = ] sequence_number` Le numéro de séquence du compte au sein du profil. *sequence_number* est **int**, sans valeur par défaut. Le numéro de séquence détermine l'ordre dans lequel les comptes sont utilisés dans le profil.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Le profil et le compte doivent déjà exister. Sinon, la procédure stockée retourne une erreur.  
  
 Notez que cette procédure stockée ne modifie pas le numéro de séquence d'un compte qui est déjà associé au profil spécifié. Pour plus d’informations sur la mise à jour le numéro de séquence d’un compte, consultez [sysmail_update_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md).  
  
 Le numéro de séquence détermine l'ordre d'utilisation des comptes de messagerie de base de données dans le profil. Pour un nouveau message électronique, la messagerie de base de données démarre avec le compte dont le numéro de séquence est le plus petit. Si ce compte échoue, la messagerie de base de données utilise le compte qui possède le numéro de séquence plus élevé suivant, et ainsi de suite jusqu'à ce qu'elle envoie le message correctement ou que le compte qui possède le numéro de séquence le plus élevé échoue. Si le compte qui a le numéro de séquence le plus élevé échoue, la messagerie de base de données interrompt les tentatives d’envoi du courrier électronique pour la durée configurée dans le paramètre *AccountRetryDelay* de **sysmail_configure_sp**, puis relance le processus de tentative d’envoi du courrier électronique en commençant à partir du numéro de séquence le moins élevé. Utilisez le paramètre *AccountRetryAttempts* de **sysmail_configure_sp**pour configurer le nombre de fois que le processus de messagerie externe tente d’envoyer le message électronique à l’aide de chaque compte du profil spécifié.  
  
 Si plusieurs comptes ont le même numéro de séquence, la messagerie de base de données utilisera uniquement l'un de ces comptes pour un message électronique donné. Dans ce cas, la messagerie de base de données exclut toute garantie en ce qui concerne le compte utilisé pour ce numéro de séquence ou l'utilisation du même compte d'un message à un autre.  
  
 La procédure stockée **sysmail_add_profileaccount_sp** est dans le **msdb** de base de données et est détenue par le **dbo** schéma. La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Autorisations  
 Autorisations d’exécution de cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant associe le profil `AdventureWorks Administrator` au compte `Audit Account`. Le numéro de séquence de ce compte est 1.  
  
```  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator',  
    @account_name = 'Audit Account',  
    @sequence_number = 1 ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Objets de Configuration de messagerie de base de données](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Procédures stockées de messagerie de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
