---
title: "Se connecter à SQL Server ou Azure SQL Database | Microsoft Docs"
ms.custom: 
ms.date: 08/25/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 2d5048825b3c71ecaec5da0f6ae75277994d1697
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="connect-to-a-sql-server-or-azure-sql-database"></a>Se connecter à SQL Server ou Azure SQL Database

Pour travailler avec des serveurs et des bases de données, vous devez d’abord vous connecter au serveur. Vous pouvez vous connecter à plusieurs serveurs en même temps.

[SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md) prend en charge plusieurs types de connexions. Cet article fournit des détails pour la connexion à SQL Server et à Azure SQL Database (connexion à un serveur logique SQL Azure). Pour plus d’informations sur les autres options de connexion, consultez les [liens](#see-also) au bas de cette page.
  
## <a name="connecting-to-a-server"></a>Connexion à un serveur  

1. Dans l’**Explorateur d’objets**, cliquez sur **Connexion > Moteur de base de données...**.

   ![connexion](../media/connect-to-server/connect-db-engine.png)

1. Renseignez l’écran **Se connecter au serveur** et cliquez sur **Connexion** :

   ![connexion au serveur](../media/connect-to-server/connect.png)

1. Si vous vous connectez à un serveur SQL Azure, vous serez peut-être invité à vous connecter pour créer une règle de pare-feu. Cliquez sur **Connexion...** (sinon, passez à l’étape 6 ci-dessous)

   ![pare-feu](../media/connect-to-server/firewall-rule-sign-in.png)

1. Une fois que vous êtes connecté, l’écran est prérempli avec votre adresse IP spécifique. Si votre adresse IP change souvent, il peut être plus simple d’accorder l’accès à une plage, donc sélectionnez l’option qui convient le mieux à votre environnement. 

   ![pare-feu](../media/connect-to-server/new-firewall-rule.png)

1. Pour créer la règle de pare-feu et vous connecter au serveur, cliquez sur **OK**.

1. Le serveur s’affiche dans l’**Explorateur d’objets** après vous être connecté :

   ![connecté](../media/connect-to-server/connected.png)

## <a name="next-steps"></a>Étapes suivantes

[Concevoir, créer et mettre à jour des tables](../visual-db-tools/design-tables-visual-database-tools.md)

## <a name="see-also"></a>Voir aussi

[SQL Server Management Studio (SSMS)](../sql-server-management-studio-ssms.md)  
[Télécharger SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md)

[Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/connect-to-analysis-services)  
[Integration Services](https://docs.microsoft.com/sql/integration-services/sql-server-integration-services)  
[Reporting Services](https://docs.microsoft.com/sql/reporting-services/tools/connect-to-a-report-server-in-management-studio)  
[Stockage Azure](../f1-help/connect-to-microsoft-azure-storage.md)  
