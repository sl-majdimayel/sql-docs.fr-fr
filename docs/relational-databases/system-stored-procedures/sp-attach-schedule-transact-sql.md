---
title: sp_attach_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_attach_schedule_TSQL
- sp_attach_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_schedule
ms.assetid: 80c80eaf-cf23-4ed8-b8dd-65fe59830dd1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4102c272fe9d880e6213917091b6078a413aebf8
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494301"
---
# <a name="spattachschedule-transact-sql"></a>sp_attach_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit la planification d'un travail.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_attach_schedule  
     { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,   
     { [ @schedule_id = ] schedule_id   
     | [ @schedule_name = ] 'schedule_name' }  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_id = ] job_id` Numéro d’identification du travail auquel ajouter la planification. *job_id*est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
`[ @job_name = ] 'job_name'` Le nom du travail auquel ajouter la planification. *job_name*est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
`[ @schedule_id = ] schedule_id` Le numéro d’identification de planification de la planification à définir pour le travail. *id_de_la_planification*est **int**, avec NULL comme valeur par défaut.  
  
`[ @schedule_name = ] 'schedule_name'` Le nom de la planification à définir pour le travail. *nom_de_la_planification*est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *id_de_la_planification* ou *nom_de_la_planification* doit être spécifié, mais ne peut pas être spécifiés.  
  
## <a name="remarks"></a>Notes  
 La planification et le travail doivent avoir le même propriétaire.  
  
 Une planification peut être définie pour plusieurs travaux. Un travail peut être exécuté dans plusieurs planifications.  
  
 Cette procédure stockée doit être exécutée à partir de la **msdb** base de données.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Notez que le propriétaire du travail peut joindre un travail à une planification et détacher un travail d'une planification sans être le propriétaire de la planification. Toutefois, une planification ne peut pas être supprimée si le détachement la conserve sans travaux, sauf si l’appelant est propriétaire de la planification.  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vérifie si l'utilisateur détient à la fois le travail et la planification.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une planification nommée `NightlyJobs`. Les travaux qui utilisent cette planification s'exécutent tous les jours lorsque l'heure indiquée par le serveur est `01:00`. L'exemple joint la planification au travail `BackupDatabase` et au travail `RunReports`.  
  
> [!NOTE]  
>  Cet exemple suppose que les travaux `BackupDatabase` et `RunReports` existent déjà.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_add_schedule  
    @schedule_name = N'NightlyJobs' ,  
    @freq_type = 4,  
    @freq_interval = 1,  
    @active_start_time = 010000 ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'BackupDatabase',  
   @schedule_name = N'NightlyJobs' ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'RunReports',  
   @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)  
  
  
