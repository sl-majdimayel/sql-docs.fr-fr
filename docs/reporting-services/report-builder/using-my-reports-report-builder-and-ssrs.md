---
title: "À l’aide de Mes rapports (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49c3c1da-b106-41f6-9173-16ff225bade8
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 48a6c898c5381bb777863ed7569c6ac302560eb3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="using-my-reports-report-builder-and-ssrs"></a>Utilisation du dossier Mes rapports (Générateur de rapports et SSRS)
  Sur un serveur de rapports configuré en mode natif, le dossier Mes rapports est un espace de travail personnel où vous pouvez stocker vos rapports et dans lequel vous pouvez travailler sur les rapports dont vous êtes l'auteur. Les autres dossiers du serveur de rapports sont publics et nécessitent généralement que les utilisateurs disposent d'autorisations avancées pour ajouter ou modifier du contenu. Contrairement à ces autres dossiers, le dossier Mes rapports est un espace de travail géré par l'utilisateur. Vous pouvez ajouter ou supprimer des rapports et des dossiers, et enregistrer des rapports liés avec des paramètres personnalisés.  
  
 D'un point de vue conceptuel, le dossier Mes rapports est similaire au dossier Mes documents du système de fichiers Windows. Bien que chaque utilisateur dispose d'un dossier appelé Mes rapports, le dossier auquel chaque utilisateur accède est différent du dossier des autres utilisateurs. À l'exception des administrateurs du serveur de rapports, les utilisateurs ne peuvent pas accéder au contenu du dossier Mes rapports qui ne leur appartient pas.  
  
 La fonctionnalité Mes rapports est facultative et peut être désactivée par un administrateur de serveur de rapports. Si elle est activée, le dossier Mes rapports apparaît dans le Dossier racine, qui est accessible au moyen du Gestionnaire de rapports ou d'un navigateur Web. Pour plus d’informations, consultez [recherche et affichage de rapports dans le Gestionnaire de rapports &#40; Le Générateur de rapports et SSRS &#41; ](/sql-docs/docs/reporting-services/report-builder/finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs).  
  
 Sur un serveur de rapports configuré en mode intégré SharePoint, il n'existe pas d'équivalent au dossier Mes rapports. Pour plus d’informations, consultez [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="ways-to-use-my-reports"></a>Modes d'utilisation du dossier Mes rapports  
 Le dossier Mes rapports est vide tant que vous n'ajoutez pas de rapports, de dossiers ou d'autres éléments. Voici plusieurs méthodes permettant d'ajouter du contenu au dossier Mes rapports.  
  
-   Créer un rapport lié personnel et le stocker dans le dossier Mes rapports. Tous les rapports ne peuvent pas faire l'objet d'un lien. Pour plus d’informations, consultez [Créer un rapport lié](../../reporting-services/reports/create-a-linked-report.md).  
  
-   Télécharger un fichier de définition de rapport (.rdl), un fichier de modèle de rapport (.smdl) ou d'autres fichiers à partir du système de fichiers. Vous pouvez télécharger n'importe quel fichier, mais le serveur de rapports traite uniquement les fichiers de rapport avec l'extension de fichier .rdl ou .smdl. Pour plus d’informations, consultez les définitions de rapport » dans le [documentation de Reporting Services](http://go.microsoft.com/fwlink/?linkid=121312) dans la documentation en ligne de SQL Server et [télécharger un fichier ou rapport &#40; Le Gestionnaire de rapports &#41; ](../../reporting-services/reports/upload-a-file-or-report-report-manager.md).  
  
-   Créer et publier vos rapports dans le dossier Mes rapports. Pour plus d’informations, consultez [mode de création de rapports &#40; Le Générateur de rapports &#41; ](../../reporting-services/report-builder/report-design-view-report-builder.md).  
  
 Habituellement, les autorisations définies pour le dossier Mes rapports vous permettent de gérer le dossier vous-même. Toutefois, c'est l'administrateur du serveur de rapports qui détermine les tâches que les utilisateurs sont autorisés à effectuer. Si des autorisations insuffisantes vous empêchent d'utiliser votre dossier Mes rapports, consultez l'administrateur de votre serveur de rapports.  
  
## <a name="searching-my-reports"></a>Recherche dans le dossier Mes rapports  
 Lorsque vous effectuez des recherches dans la base de données d'un serveur de rapports, le contenu de votre dossier Mes rapports est inclus dans l'étendue de la recherche, tandis que le contenu des dossiers Mes rapports des autres utilisateurs en est exclu. Les résultats de la recherche présentent uniquement les rapports auxquels vous avez accès.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  