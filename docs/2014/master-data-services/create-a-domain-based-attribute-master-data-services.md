---
title: Créer un attribut basé sur un domaine (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], creating
- creating domain-based attributes [Master Data Services]
- attributes [Master Data Services], creating domain-based attributes
ms.assetid: 11c31c9f-e6cc-47b7-b76a-d691f84c93c6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1dc346c31b7d26989dd2fac018a7bae0752f77e4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52755411"
---
# <a name="create-a-domain-based-attribute-master-data-services"></a>Créer un attribut basé sur un domaine (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez un attribut basé sur un domaine pour remplir les valeurs d'un attribut avec les membres d'une entité.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Une entité doit exister pour servir de source de valeurs d'attribut. Par exemple, vous devez créer l'entité Color avant de créer un attribut basé sur un domaine et sur l'entité Color. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
-   Une entité doit exister pour créer l'attribut qui lui est destiné. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-create-a-domain-based-attribute"></a>Pour créer un attribut basé sur un domaine  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Sélectionnez la ligne de l'entité pour laquelle vous souhaitez créer un attribut.  
  
5.  Cliquez sur **Modifier l'entité sélectionnée**.  
  
6.  Dans la page **Modifier l'entité** :  
  
    -   Si l'attribut est destiné à des membres feuille, dans le volet **Attributs de membre feuille** , cliquez sur **Ajouter un attribut feuille**.  
  
    -   Si l'attribut est destiné à des membres consolidés, dans le volet **Attributs de membre consolidé** , cliquez sur **Ajouter un attribut consolidé**.  
  
    -   Si l'attribut est destiné à des collections, dans le volet **Attributs de collection** , cliquez sur **Ajouter un attribut de collection**.  
  
7.  Sur le **ajouter un attribut** page, sélectionnez le **basés sur domaine** option.  
  
8.  Dans la zone **Nom** , tapez un nom pour l'attribut. Il ne doit pas nécessairement s'agir du nom de l'entité qui sert de source aux valeurs d'attribut.  
  
9. Dans la zone **Largeur d'affichage en pixels** , tapez la largeur de la colonne d'attribut à afficher dans la grille **Explorateur** .  
  
10. À partir de la **entité** , sélectionnez l’entité à utiliser pour remplir les valeurs d’attribut.  
  
11. Facultatif. Sélectionnez **Activer le suivi des modifications** pour effectuer le suivi des modifications apportées aux groupes d'attributs. Pour plus d’informations, consultez [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
12. Cliquez sur **Enregistrer l'attribut**.  
  
13. Dans la page **Maintenance de l'entité** , cliquez sur **Enregistrer l'entité**.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs basés sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)   
 [Créer une hiérarchie dérivée &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)   
 [Modifier un nom d’attribut &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)   
 [Supprimer un attribut &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-master-data-services.md)  
  
  
