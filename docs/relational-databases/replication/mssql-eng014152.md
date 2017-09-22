---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 06008fe3c31133feab100628a7f0e813acefa17c
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng014152"></a>MSSQL_ENG014152
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14152|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Réplication-%s : agent %s programmé pour réessayer. %s|  
  
## <a name="explanation"></a>Explication  
 L'agent de réplication spécifié a été programmé pour retenter l'opération demandée. Le processus continue à réessayer jusqu'à ce qu'il atteigne le nombre maximal de tentatives de reprise configuré pour l'étape du travail.  
  
 Une nouvelle tentative est effectuée généralement pour l'une des raisons suivantes :  
  
-   La valeur **QueryTimeout** est dépassée.  
  
-   La valeur **LoginTimeout** est dépassée.  
  
-   Le processus de réplication a été choisi comme victime du blocage.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si ce message est occasionnel, aucune action de l'utilisateur n'est requise.  
  
 Utilisez [sp_help_jobstep](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md) pour afficher le paramétrage actuel du nombre maximal de tentatives défini pour l'étape **Exécution de l'Agent** pour l'agent de réplication spécifié. Vous pouvez utiliser le paramètre **@retry_attempts** de la procédure stockée [sp_update_jobstep](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md) pour ajuster le nombre de tentatives de reprise d'une étape de travail.  
  
 Si ce message est récurrent, résolvez le problème en fonction du message qui est à l'origine de la nouvelle tentative. Vérifiez si l'historique de l'agent contient des messages indiquant pourquoi la reprise a dû être planifiée. Dans certains cas, vous devrez peut-être activer une journalisation plus détaillée pour votre agent de réplication. Pour plus d'informations sur la configuration de la journalisation pour la réplication, consultez l'article [312292](http://support.microsoft.com/kb/312292)de la Base de connaissances Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  