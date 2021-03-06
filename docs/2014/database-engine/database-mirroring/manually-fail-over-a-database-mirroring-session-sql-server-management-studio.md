---
title: Basculer manuellement une session de mise en miroir de bases de données (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 4ecf9c63-b3a4-4c54-b553-5bc37973232b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b42fdb9d53a4aa0444a98ee311000fb1c2929ff1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212079"
---
# <a name="manually-fail-over-a-database-mirroring-session-sql-server-management-studio"></a>Basculer manuellement une session de mise en miroir de bases de données (SQL Server Management Studio)
  Lorsque la base de données en miroir est synchronisée (que son état est SYNCHRONIZED), le propriétaire de la base de données peut initier un basculement manuel vers le serveur miroir.  
  
 Lors d'un basculement manuel, les rôles de principal et de serveur miroir sont permutés pour la base de données concernée par le basculement. La base de données miroir devient la base de données principale et inversement. Par exemple, le tableau suivant illustre la façon dont les rôles de deux serveurs partenaires de mise en miroir sont permutés à l'occasion d'un basculement manuel : `SQLDBENGINE0_1` et `SQLDBENGINE0_2`.  
  
|Serveur|Avant le basculement|Après le basculement|  
|------------|---------------------|--------------------|  
|`SQLDBENGINE0_1`|PRINCIPAL|MIRROR|  
|`SQLDBENGINE0_2`|MIRROR|PRINCIPAL|  
  
 Sachez que les rôles serveur des autres sessions de mise en miroir de base de données ne sont pas affectés. Pour plus d’informations, consultez [Basculement de rôle durant une session de mise en miroir de bases de données &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).  
  
### <a name="to-manually-fail-over-database-mirroring"></a>Pour effectuer un basculement manuel d'une mise en miroir de base de données  
  
1.  Connectez-vous à l'instance du serveur principal puis, dans le volet **Explorateur d'objets** , cliquez sur le nom du serveur pour développer l'arborescence.  
  
2.  Développez **Bases de données**, puis sélectionnez la base de données à basculer.  
  
3.  Cliquez avec le bouton droit sur la base de données, sélectionnez **Tâches**, puis cliquez sur **Miroir**. La page **Mise en miroir** de la boîte de dialogue **Propriétés de la base de données** s'affiche.  
  
4.  Cliquez sur **Basculement**.  
  
     Une boîte de confirmation s'affiche.  Le serveur principal commence par essayer de se connecter au serveur miroir à l'aide de l'authentification Windows. Si l’authentification Windows ne fonctionne pas, le serveur principal affiche la boîte de dialogue **Se connecter au serveur** . Si le serveur miroir utilise l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sélectionnez **Authentification SQL Server** dans la zone **Authentification** . Dans la zone de texte **Connexion** , spécifiez le compte de connexion à utiliser pour se connecter sur le serveur miroir puis, dans la zone de texte **Mot de passe** , spécifiez le mot de passe de ce compte.  
  
     Si le basculement réussit, la boîte de dialogue **Propriétés de la base de données** se ferme. La base de données miroir devient la base de données principale et inversement.  
  
     Si le basculement échoue, un message d'erreur s'affiche et la boîte de dialogue reste ouverte.  
  
    > [!IMPORTANT]  
    >  Si vous avez modifié des propriétés depuis l’ouverture de la page **Mise en miroir** , ces modifications ne sont pas enregistrées.  
  
     La boîte de dialogue se ferme automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la base de données &#40;page Mise en miroir&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Basculer manuellement une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md)   
 [Suspendre ou reprendre une session de mise en miroir de bases de données &#40;SQL Server&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md)   
 [Supprimer une mise en miroir de bases de données &#40;SQL Server&#41;](remove-database-mirroring-sql-server.md)  
  
  
