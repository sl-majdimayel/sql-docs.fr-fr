---
title: Inscrire des serveurs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ddc29cf39385a1d91b0f2328ec69e3e61e4c4902
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332959"
---
# <a name="register-servers"></a>Inscrire des serveurs
  L'inscription d'un serveur dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] vous permet de stocker les informations de connexion au serveur pour des connexions futures. Il existe trois façons d'inscrire un serveur dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
1.  Les instances locales de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont automatiquement inscrites lors du premier lancement de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] après son installation.  
  
2.  Vous pouvez également initier le processus d'enregistrement automatique à n'importe quel moment, pour restaurer l'inscription des instances de serveur locales.  
  
3.  Enfin, vous pouvez inscrire un serveur au moyen de l'outil Serveurs inscrits dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="benefits-of-registered-servers"></a>Avantages des serveurs inscrits  
 Grâce aux serveurs inscrits, vous pouvez effectuer les tâches suivantes :  
  
-   inscrire les serveurs pour conserver les informations de connexion ;  
  
-   déterminer si un serveur inscrit est en cours d'exécution ;  
  
-   connecter facilement l'Explorateur d'objets et l'Éditeur de requête à un serveur inscrit ;  
  
-   modifier ou supprimer les informations d'inscription d'un serveur inscrit ;  
  
-   créer des groupes de serveurs ;  
  
-   attribuer des noms conviviaux aux serveurs inscrits en fournissant une valeur dans la zone **Nom du serveur inscrit** (qui est différente de la liste **Nom du serveur** ) ;  
  
-   fournir une description détaillée des serveurs inscrits ;  
  
-   fournir une description détaillée des groupes de serveurs inscrits ;  
  
-   exporter des groupes de serveurs inscrits ;  
  
-   importer des groupes de serveurs inscrits ;  
  
-   consulter les fichiers journaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les instances en ligne ou hors connexion de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="related-tasks"></a>Related Tasks  
 Utilisez les rubriques suivantes pour commencer à utiliser les serveurs inscrits :  
  
|**Description**|**Rubrique**|  
|---------------------|---------------|  
|Inscrire les instances de serveur locales|[Inscrire un serveur connecté &#40;SQL Server Management Studio&#41;](register-a-connected-server-sql-server-management-studio.md)|  
|Inscrire un serveur|[Créer un nouveau serveur inscrit &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)|  
|Afficher les serveurs inscrits|[Afficher des serveurs inscrits dans SQL Server Management Studio](view-registered-servers-in-sql-server-management-studio.md)|  
|Supprimer un serveur inscrit|[Supprimer un serveur inscrit &#40;SQL Server Management Studio&#41;](remove-a-registered-server-sql-server-management-studio.md)|  
|Modifier l'inscription d'un serveur|[Modifier l’inscription d’un serveur &#40;SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md)|  
|Se connecter à un serveur inscrit|[Se connecter à un serveur inscrit &#40;SQL Server Management Studio&#41;](connect-to-a-registered-server-sql-server-management-studio.md)|  
|Se déconnecter d'un serveur inscrit|[Se déconnecter d’un serveur inscrit &#40;SQL Server Management Studio&#41;](disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|Déplacer un serveur ou un groupe de serveurs inscrit|[Déplacer un serveur inscrit ou un groupe de serveurs inscrits &#40;SQL Server Management Studio&#41;](move-a-registered-server-or-registered-server-group.md)|  
|Modifier le nom d'un serveur ou d'un groupe de serveurs inscrit|[Modifier le nom d’un serveur ou d’un groupe de serveurs inscrits &#40;SQL Server Management Studio&#41;](change-the-name-of-registered-server-or-registered-server-group.md)|  
|Créer ou modifier un groupe de serveurs|[Créer ou modifier un groupe de serveurs &#40;SQL Server Management Studio&#41;](create-or-edit-a-server-group-sql-server-management-studio.md)|  
|Supprimer un groupe de serveurs|[Supprimer un groupe de serveurs &#40;SQL Server Management Studio&#41;](remove-a-server-group-sql-server-management-studio.md)|  
|Exporter des informations de serveur inscrit|[Exporter les informations des serveurs inscrits &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md)|  
|Importer des informations de serveur inscrit|[Importer les informations des serveurs inscrits &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md)|  
|Créer un serveur de gestion centralisée et un groupe de serveurs|[Créer un serveur d’administration centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md)|  
|Exécuter des instructions sur plusieurs serveurs simultanément|[Exécuter des instructions simultanément sur plusieurs serveurs &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs distants](../../database-engine/configure-windows/remote-servers.md)  
  
  