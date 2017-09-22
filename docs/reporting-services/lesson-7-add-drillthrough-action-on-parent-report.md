---
title: "Leçon 7 : Ajouter l’Action d’extraction sur le rapport Parent | Documents Microsoft"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: aad2da1a-d7b1-4afa-a66a-1ff102e8306f
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 9a9790c4afc44e66c521005a3556f8082527d260
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="lesson-7-add-drillthrough-action-on-parent-report"></a>Leçon 7 : ajouter l'action d'extraction dans le rapport parent
Après avoir ajouté un contrôle ReportViewer à l'application de site Web, l'étape suivante consiste à ajouter une action d'extraction dans le rapport parent.  
  
### <a name="to-add-drillthrough-action-on-the-parent-report"></a>Pour ajouter une action d'extraction au rapport parent  
  
1.  Accédez au rapport parent.  
  
2.  Cliquez sur la zone de texte qui contient la valeur de **Nom**.  
  
3.  Cliquez avec le bouton droit sur la zone de texte, puis sélectionnez **Propriétés de la zone de texte**.  
  
4.  Accédez à l’onglet **Action** , puis sélectionnez l’option **Atteindre le rapport** .  
  
5.  Entrez le nom du rapport enfant dans la section **Spécifier un rapport** .  
  
    > [!NOTE]
    > N’incluez pas l’extension de fichier dans le nom du rapport.  
  
6.  Cliquez sur **Ajouter** sous la section **Utilisez ces paramètres pour exécuter le rapport** .  
  
7.  Tapez **productid** dans la zone de **nom** , puis sélectionnez **ProductID** dans la liste déroulante **Valeur** .  
  
8.  Sélectionnez **OK** pour terminer.  
  
## <a name="next-task"></a>Tâche suivante  
Vous venez d'ajouter une action d'extraction dans le rapport parent. Vous allez à présent créer un filtre de données pour la table de données que vous avez définie pour le rapport enfant. Consultez la [Leçon 8 : Créer un filtre de données](../reporting-services/lesson-8-create-a-data-filter.md).  
  
  
  

