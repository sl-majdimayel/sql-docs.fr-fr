---
title: "Affecter des autorisations d’objet de modèle (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: fa5c8efcfbefcc52aed6c4ffb5bd1614c3fb607c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="assign-model-object-permissions-master-data-services"></a>Affecter des autorisations d'objet de modèle (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], affectez les autorisations aux objets de modèle lorsque vous devez donner à un utilisateur ou un groupe l'accès aux données dans la zone fonctionnelle **Explorateur** de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], ou lorsque vous devez faire d'un utilisateur ou d'un groupe un administrateur.  
  
> [!NOTE]  
>  Lorsque vous affectez une autorisation à un modèle, l'autorisation à tous les autres modèles est refusée implicitement. Si vous n'affectez pas d'autorisations d'objet de modèle, l'utilisateur ou le groupe ne peut accéder à aucune donnée dans l' **Explorateur**.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Autorisations d'accès** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-assign-model-object-permissions"></a>Pour affecter des autorisations d'objet de modèle  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Autorisations d'accès**.  
  
2.  Dans la page **Utilisateurs** ou **Groupes** , sélectionnez la ligne de l'utilisateur ou du groupe à modifier.  
  
3.  Cliquez sur **Modifier l'utilisateur sélectionné**.  
  
4.  Cliquez sur l'onglet **Modèles** .  
  
5.  Dans la liste **Modèle** , sélectionnez éventuellement un modèle.  
  
6.  Cliquez sur **Modifier**.  
  
7.  Développez l'arborescence, puis cliquez sur l'objet de modèle auquel vous souhaitez affecter des autorisations.  
  
8.  Dans le menu, sélectionnez une combinaison d’autorisations (lecture, création, mise à jour et suppression, ou refus).  
  
9. Au niveau du modèle de niveau supérieur, sélectionnez **Admin** pour créer un administrateur de modèles utilisateur.  
  
10. Cliquez sur **Enregistrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   (Facultatif) [Affecter des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/delete-model-object-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Créer un administrateur de modèle &#40;Master Data Services&#41;](../master-data-services/create-a-model-administrator-master-data-services.md)  
  
  