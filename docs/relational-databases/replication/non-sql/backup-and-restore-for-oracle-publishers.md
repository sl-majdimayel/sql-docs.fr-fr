---
title: Sauvegarde et restauration des serveurs de publication Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], Oracle publishing
- backups [SQL Server replication], Oracle publishing
- Oracle publishing [SQL Server replication], backup and restore
- restoring [SQL Server replication], Oracle publishing
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21b2de27362455291c75e64c93ad6cf7e3529ca8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833347"
---
# <a name="backup-and-restore-for-oracle-publishers"></a>Sauvegarde et restauration des serveurs de publication Oracle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Suivez ces instructions lors de la sauvegarde et de la restauration :  
  
-   Vérifiez que l'Agent de lecture du journal n'est pas en cours d'exécution et que d'autres activités de la base de données sur les tables publiées n'ont pas lieu alors que le serveur de publication est en cours d'exécution.  
  
-   Sauvegardez le serveur de publication et le serveur de distribution au même moment.  
  
-   Si le serveur de publication ou le serveur de distribution doit être restauré, réinitialisez tous les abonnements.  
  
-   Pour restaurer un Abonné à partir d'une sauvegarde (sans avoir à réinitialiser les abonnements), les transactions remises à la base de données de distribution après la fin de la dernière sauvegarde de la base de données doivent être encore disponibles. La période de temps pendant laquelle les transactions sont disponibles dépend des paramètres de rétention de la distribution. Pour plus d’informations, consultez [Expiration et désactivation des abonnements](../../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
-   Si le serveur de publication ou le serveur de distribution devient désynchronisé à la suite d'une restauration de la base de données, les agents de réplication consignent des messages d'erreur. À ce stade, vous devez supprimer et recréer toutes les publications et tous les abonnements concernés :  
  
    1.  Placez la définition des publications et des abonnements dans des scripts. Pour plus d’informations, voir [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
         Si la définition des publications a changé entre les versions des états du serveur de publication et du serveur de distribution, vous devez modifier les scripts.  
  
    2.  Supprimez les publications et les abonnements.  
  
    3.  Exécutez les scripts créés à l'étape 1.  
  
     Si le serveur de publication doit être supprimé et reconfiguré, supprimez le synonyme public **MSSQLSERVERDISTRIBUTOR** et l'utilisateur de réplication Oracle configuré avec l'option **CASCADE** pour supprimer tous les objets de réplication du serveur de publication Oracle.  
  
## <a name="see-also"></a> Voir aussi  
 [Sauvegarder et restaurer des bases de données répliquées](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Configurer un serveur de publication Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Vue d’ensemble de la publication Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  
