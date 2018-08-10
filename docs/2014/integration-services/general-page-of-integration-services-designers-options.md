---
title: Page Général | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4bc23fd22ec07f78e71713e1cce93d9845c35ccc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229279"
---
# <a name="general-page"></a>Page Général
  Utilisez la page **Général** de la page **Concepteurs de services d'intégration** dans la boîte de dialogue **Options** pour spécifier les options de chargement, d'affichage et de mise à niveau des packages.  
  
 Pour ouvrir la page **Général** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans le menu **Outils** , cliquez sur **Options**, développez **Concepteurs Business Intelligence**et sélectionnez **Concepteurs de services d'intégration**.  
  
## <a name="options"></a>Options  
 **Vérifier la signature numérique lors du chargement d'un package**  
 Sélectionnez cette option pour que [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vérifie la signature numérique durant le chargement d’un package. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vérifie uniquement si la signature numérique est présente, si elle est valide et si elle provient d’une source fiable. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ne vérifie pas si le package a été modifié depuis qu'il a été signé.  
  
 Si vous définissez la valeur de Registre **BlockedSignatureStates** , cette valeur de Registre remplace l’option **Vérifier la signature numérique lors du chargement d’un package** . Pour plus d’informations, consultez [Implémenter une stratégie de signature en définissant une valeur de Registre](implement-a-signing-policy-by-setting-a-registry-value.md).  
  
 Pour plus d’informations sur les packages et les certificats numériques, consultez [Identifier la source de packages à l’aide de signatures numériques](security/identify-the-source-of-packages-with-digital-signatures.md).  
  
 **Afficher un avertissement si un package n'est pas signé**  
 Sélectionnez cette option pour afficher un avertissement lors du chargement d'un package qui n'est pas signé.  
  
 **Afficher les étiquettes de contrainte de précédence**  
 Sélectionnez l'étiquette (Réussite, Échec ou À l'achèvement) à afficher sur les contraintes de précédence lors de la consultation de packages dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 **Langage de script**  
 Sélectionnez le langage de script par défaut pour les nouvelles tâches de script et les composants Script.  
  
 **Mettre à jour les chaînes de connexion pour l'utilisation des nouveaux noms de fournisseurs**  
 Durant l’ouverture ou la mise à niveau de packages [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] , mettez à jour les chaînes de connexion afin d’utiliser les noms correspondant aux fournisseurs suivants, pour la version actuelle de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Fournisseur OLE DB  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client  
  
 L'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] met à jour uniquement les chaînes de connexion qui sont stockées dans des gestionnaires de connexions. Il ne met pas à jour les chaînes de connexion qui sont construites dynamiquement à l'aide du langage d'expression [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ou en utilisant du code dans une tâche de script.  
  
 **Créer un ID de package**  
 Durant la mise à niveau de packages [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] , créez des ID de package pour les versions mises à niveau des packages.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](security/security-overview-integration-services.md)   
 [Extension de packages avec des scripts](extending-packages-scripting/extending-packages-with-scripting.md)  
  
  