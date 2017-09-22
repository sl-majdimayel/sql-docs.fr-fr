---
title: MSSQL_ENG014162 | Microsoft Docs
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
- MSSQL_ENG014162 error
ms.assetid: a15eef3f-219f-45d3-8286-6a864c85a723
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dd388a3befebcdae6d315d04a46190f12e85bf37
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng014162"></a>MSSQL_ENG014162
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14162|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le seuil [%s:%s] de la publication [%s] a été défini. Assurez-vous que l'Agent de fusion s'exécute et peut respecter les conditions de latence.|  
  
## <a name="explanation"></a>Explication  
 La réplication vous permet d'activer des avertissements pour plusieurs situations. Vous pouvez, entre autres, signaler le dépassement d'une durée spécifiée pour la synchronisation des modifications entre un serveur de publication de fusion et un Abonné. Vous pouvez spécifier des seuils différents pour les connexions LAN et pour les connexions d'accès à distance.  
  
 Lorsque vous activez un avertissement à l'aide du moniteur de réplication ou de la procédure stockée [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), vous spécifiez un seuil qui détermine à quel moment l'avertissement sera déclenché. Quand ce seuil est atteint ou dépassé, un avertissement s'affiche dans le moniteur de réplication et un événement est enregistré dans le journal des événements Windows. Le franchissement d'un seuil peut également déclencher une alerte de l'Agent SQL Server. Pour plus d’informations, consultez [Définir des seuils et des avertissements dans le moniteur de réplication](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md) et [Surveiller la réplication par programme](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si un abonnement dépasse un seuil de durée, vous devez déterminer si le système a un problème de performance ou si le seuil doit être modifié. Une fois la réplication configurée, élaborez un référentiel de performances qui vous permettra d'évaluer les performances de la réplication avec une charge de travail standard pour vos applications et votre topologie. Intégrez la durée de synchronisation à ce référentiel afin de pouvoir définir une valeur appropriée pour le seuil.  
  
 Si la valeur du seuil est appropriée, mais qu'elle continue à être franchie, vous devez déterminer où se trouve le goulet d'étranglement dans le système. Pour plus d'informations sur le contrôle des performances de réplication et la résolution des éventuels problèmes, consultez les rubriques suivantes :  
  
-   [Analyser les performances avec le Moniteur de réplication](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) (en particulier, la section « Affichage des performances de synchronisation détaillées pour la réplication de fusion »)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  