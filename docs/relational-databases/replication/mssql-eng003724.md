---
title: MSSQL_ENG003724 | Microsoft Docs
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
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d97300f400557643da18e81201136649d629b681
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng003724"></a>MSSQL_ENG003724
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3724|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de %S_MSG le %S_MSG '%.*ls' parce qu’il est utilisé pour la réplication.|  
  
## <a name="explanation"></a>Explication  
 Lorsque des objets d'une base de données sont répliqués, ils sont marqués comme étant répliqués dans la table système **sysarticles** (publications transactionnelles ou d'instantanés) ou dans la table système **sysmergearticles** (publications de fusion). Si vous tentez de supprimer un objet répliqué, cette erreur est générée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que l'objet de base de données n'est pas répliqué avant d'essayer de le supprimer. Exemple :  
  
-   Si l'erreur se produit dans la base de données de publication, supprimez l'article de la publication avant de supprimer l'objet. Pour plus d’informations, consultez [Ajouter et supprimer des articles de publications existantes](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
-   Si l'erreur se produit dans la base de données d'abonnement, supprimez l'abonnement avant de supprimer l'objet. Pour plus d’informations, consultez [S’abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md). Dans le cas d'abonnements aux publications transactionnelles, il est possible de supprimer l'abonnement à un article individuel plutôt qu'à la publication complète. Pour plus d’informations, consultez [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md).  
  
 Si cette erreur se produit dans une base de données qui n’est pas répliquée, exécutez [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) pour vérifier que les objets de la base de données ne sont pas marqués comme étant répliqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  