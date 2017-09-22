---
title: MSSQLSERVER_926 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 926 (Database Engine error)
ms.assetid: 57e01668-883b-4be4-84a8-a111caaf0486
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8900ade636aee2f01807d4fc0357e6e53302de1c
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver926"></a>MSSQLSERVER_926
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|926|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DB_SUSPECT|  
|Texte du message|La base de données '%.*ls' ne peut pas être ouverte. Elle a été marquée SUSPECT lors de la récupération. Pour plus d’informations, consultez le journal des erreurs SQL Server.|  
  
## <a name="explanation"></a>Explication  
La base de données est marquée comme étant suspecte, car le processus de récupération visant à amener la base de données dans un état transactionnel cohérent a échoué. Cela peut se produire durant les opérations suivantes :  
  
-   Démarrage d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Attachement d'une base de données.  
  
-   Utilisation de la base de données RESTORE ou de procédures RESTORE LOG.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Inspectez le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et déterminez la cause de l'erreur. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été redémarré depuis l'échec de la récupération, regardez dans les journaux des erreurs précédents de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de voir pourquoi la récupération a échoué.  
  
Si la récupération a échoué en raison d'une erreur d'E/S permanente, d'une page endommagée ou d'un autre problème matériel, résolvez le problème matériel sous-jacent et restaurez la base de données en utilisant une sauvegarde. Si aucune sauvegarde n'est disponible, utilisez les options de réparation de DBCC CHECKDB.  
  
Si vous n'arrivez pas à résoudre ce problème, contactez votre fournisseur d'assistance principal. Fournissez-lui le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin qu'il puisse l'examiner.  
  
## <a name="see-also"></a>Voir aussi  
[Sauvegarde et restauration des bases de données SQL Server](~/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
[sys.sysdatabases &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)  
[Attacher et détacher une base de données &#40;SQL Server&#41;](~/relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
