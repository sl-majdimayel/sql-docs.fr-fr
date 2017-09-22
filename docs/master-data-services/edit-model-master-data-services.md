---
title: "Modifier le modèle (Master Data Services) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], changing name
ms.assetid: 399eed32-7c61-4239-9c06-996a65219518
caps.latest.revision: 9
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: ee796a4c002df4e0a843e7a663e60d4a7f24a398
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="edit-model-master-data-services"></a>Modifier le modèle (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez modifier le nom et la description d’un modèle et indiquer la durée de conservation des journaux des transactions.  
  
 Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-change-a-model"></a>Pour modifier un modèle  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Modèles**.  
  
3.  Sur la page **Gérer les modèles** , dans la grille, sélectionnez la ligne correspondant au modèle dont vous souhaitez modifier le nom ou la description.  
  
4.  Cliquez sur **Modifier**.  
  
5.  Dans la zone **Nom** , tapez le nom mis à jour du modèle.  
  
6.  Dans le champ **Description** , tapez la description mise à jour du modèle.  
  
7.  Dans le champ **Nombre de jours de rétention du journal** , sélectionnez l’une des options permettant de conserver les données du journal. La valeur par défaut est **Paramètre système**, ce qui indique que la valeur est héritée des paramètres système dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
     Pour remplacer le paramètre système sans supprimer les données du journal des transactions, sélectionnez **NON**. Pour conserver uniquement les données du journal d’aujourd’hui et effacer celles des jours précédents, sélectionnez **OUI** et réglez le champ **Jours** sur 0. Pour conserver les données du journal pendant un nombre de jours déterminé, sélectionnez **OUI** et réglez le champ **Jours** sur le nombre de jours souhaité.  
  
8.  Cliquez sur **Enregistrer le modèle**.  
  
 La colonne **État** de la grille affiche l’état de l’opération sur le modèle. Quand vous cliquez sur le bouton **Enregistrer le modèle**, l’image ![Mise à jour](../master-data-services/media/mds-model-status-updating.png "Mise à jour") s’affiche, ce qui signifie que le modèle est en cours de mise à jour. En cas d’erreur pendant la création ou la modification d’un modèle, l’image ![Erreur](../master-data-services/media/mds-model-status-error.png "Erreur") apparaît. Dans le cas contraire, le statut est OK et l’image ![OK](../master-data-services/media/mds-model-status-ok.png "OK") apparaît.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un modèle &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md)   
 [Supprimer un modèle &#40;Master Data Services&#41;](../master-data-services/delete-a-model-master-data-services.md)   
 [Modèles &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)  
  
  