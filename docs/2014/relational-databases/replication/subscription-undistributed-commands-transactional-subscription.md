---
title: Abonnement, commandes non distribuées (abonnement transactionnel, SQL Server 2005 et versions ultérieur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a1f957c417c5c63766dfbffa923edd6935d1eb5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52752531"
---
# <a name="subscription-undistributed-commands-transactional-subscription-sql-server-2005-and-later"></a>Abonnement, Commandes non distribuées (Abonnement transactionnel, SQL Server 2005 et version ultérieure)
  L'onglet **Commandes non distribuées** contient des informations sur le nombre de commandes de la base de données de distribution qui n'ont pas été distribuées à l'abonné sélectionné, ainsi que le délai estimé de distribution de ces commandes. Pour plus d’informations sur l’affichage des commandes dans la base de données de distribution, consultez [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql).  
  
## <a name="options"></a>Options  
 **Nombre de commandes dans la base de données de distribution attendant d'être appliquées à cet abonné.**  
 Nombre de commandes dans la base de données de distribution qui n'ont pas été distribuées à l'abonné sélectionné. Une commande est constituée d'une instruction DML (Data Manipulation Language) Transact-SQL ou d'une instruction DDL (Data Definition Language).  
  
 **Temps estimé pour appliquer ces commandes, sur base des performances passées**  
 Délai estimé de distribution des commandes à l'Abonné. Si cette valeur est supérieure au délai nécessaire pour générer et appliquer un instantané à l'Abonné, réinitialisez l'Abonné. Pour plus d’informations, consultez [Réinitialiser des abonnements](reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Analyser les performances avec le moniteur de réplication](monitor/monitor-performance-with-replication-monitor.md)   
 [Surveillance de la réplication](monitoring-replication.md)  
  
  
