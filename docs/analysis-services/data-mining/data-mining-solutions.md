---
title: "Solutions d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], about data mining
- data mining [Analysis Services], development
ms.assetid: 84f6548d-ebb0-4e10-9b29-66253fa0a04a
caps.latest.revision: 64
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ee2196b673eb9a53d5fefe5c62d1158ae94bf702
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="data-mining-solutions"></a>Solutions d'exploration de données
  Une solution d'exploration de données est une solution [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient un ou plusieurs projets d'exploration de données.  
  
 Les rubriques de cette section fournissent des informations sur la façon de concevoir et d’implémenter une solution d’exploration de données intégrée à l’aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour une présentation du processus de conception d’exploration de données et des outils connexes, consultez [Concepts d’exploration de données](../../analysis-services/data-mining/data-mining-concepts.md).  
  
 Pour plus d’informations sur d’autres types de projets qui sont utiles pour l’exploration de données, consultez [Projets connexes pour des solutions d’exploration de données](../../analysis-services/data-mining/related-projects-for-data-mining-solutions.md).  
  
 [Vs relationnelles. Solutions multidimensionnelles](#bkmk_RelMD)  
  
 [Déploiement de solutions d’exploration de données](#bkmk_Deploy)  
  
 [Procédures pas à pas liées à la solution](#bkmk_Walkthru)  
  
##  <a name="bkmk_RelMD"></a>Vs relationnelles. solutions multidimensionnelles  
 Une solution d'exploration de données peut être basée sur des données multidimensionnelles (c'est-à-dire un cube existant), des données purement relationnelles (telles que les tables et les vues présentes dans un entrepôt de données), des fichiers texte, des classeurs Excel ou d'autres sources de données externes.  
  
-   Vous pouvez créer des objets d'exploration de données dans une solution de base de données multidimensionnelle existante.  
  
     Vous créez généralement une solution de ce genre si vous avez déjà créé un cube et que vous voulez effectuer une exploration de données en utilisant ce cube comme source de données. Lorsque vous déplacez et sauvegardez des modèles basés sur un cube, le cube doit également être déplacé ou copié.  
  
-   Vous pouvez créer une solution d'exploration de données qui contient uniquement des objets d'exploration de données, y compris les sources de données et vues de sources de données de prise en charge, et qui utilise uniquement la source de données relationnelle.  
  
     Cette méthode est recommandée pour créer des modèles d'exploration de données, car la rapidité du traitement et de l'interrogation est généralement optimale sur les sources de données relationnelles. Vous pouvez également déplacer et sauvegarder facilement des modèles entre des serveurs à l'aide des commandes EXPORT et IMPORT.  
  
##  <a name="bkmk_Deploy"></a> Déploiement de solutions d’exploration de données  
 L’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans laquelle vous déployez la solution doit s’exécuter dans un mode qui prend en charge les objets multidimensionnels et les objets d’exploration de données ; autrement dit, vous ne pouvez pas déployer des objets d’exploration de données dans une instance qui héberge des modèles tabulaires ou des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
 Par conséquent, lorsque vous créez une solution d'exploration de données dans Visual Studio, veillez à utiliser le modèle **Projet multidimensionnel et d'exploration de données Analysis Services**.  
  
 Lorsque vous déployez la solution, les objets utilisés pour l'exploration de données sont créés dans l'instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] spécifiée, dans une base de données portant le même nom que le fichier solution.  
  
 Pour plus d’informations sur la façon de déployer des solutions relationnelles et des solutions multidimensionnelles, consultez [Déploiement de solutions d’exploration de données](../../analysis-services/data-mining/deployment-of-data-mining-solutions.md).  
  
##  <a name="bkmk_Walkthru"></a> Procédure pas à pas liées à la solution  
 Fournit une vue d'ensemble de la création de solutions d'exploration de données à l'aide de l'Assistant Exploration de données.  
  
 [Créer une structure d'exploration de données relationnelle](../../analysis-services/data-mining/create-a-relational-mining-structure.md)  
 Créez une structure d'exploration de données à partir de données relationnelles, de fichiers texte et d'autres sources qui peuvent être combinées dans une vue de source de données.  
  
 [Create an OLAP Mining Structure](../../analysis-services/data-mining/create-an-olap-mining-structure.md)  
 Créez une structure d'exploration de données basée sur des données dans un cube OLAP. Les modèles que vous créez à partir de données OLAP peuvent être enregistrés en tant que dimension d'exploration de données, ou vous pouvez enregistrer l'ensemble de données et vos modèles en tant que nouveau cube.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Projets d'exploration de données](../../analysis-services/data-mining/data-mining-projects.md)  
  
 [Traitement des objets d'exploration de données](../../analysis-services/data-mining/processing-data-mining-objects.md)  
  
 [Projets connexes pour des solutions d’exploration de données](../../analysis-services/data-mining/related-projects-for-data-mining-solutions.md)  
  
 [Déploiement de solutions d’exploration de données](../../analysis-services/data-mining/deployment-of-data-mining-solutions.md)  
  
## <a name="related-tasks-and-topics"></a>Tâches et rubriques connexes  
 Après avoir créé une solution d'exploration de données de base, notamment des sources de données et une structure d'exploration de données, vous pouvez générer la solution en ajoutant de nouveaux modèles, en testant et en comparant des modèles, en créant des prédictions et effectuant des essais avec des sous-ensembles de données.  
  
 Pour plus d'informations, consultez les liens suivants :  
  
|Tâches|Rubriques|  
|-----------|------------|  
|Testez les modèles que vous créez, validez la qualité de vos données d'apprentissage et créez des graphiques qui représentent la précision des modèles d'exploration de données.|[Test et validation &#40;exploration de données&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)|  
|Effectuez l'apprentissage du modèle en remplissant la structure et les modèles associés avec des données. Mettez à jour et étendez des modèles avec de nouvelles données.|[Traitement des objets d'exploration de données](../../analysis-services/data-mining/processing-data-mining-objects.md)|  
|Personnalisez un modèle d'exploration de données en appliquant des filtres aux données d'apprentissage, en choisissant un algorithme différent ou en définissant des paramètres d'algorithme avancés.|[Personnaliser les modèles et les structures d'exploration de données](../../analysis-services/data-mining/customize-mining-models-and-structure.md)|  
|Personnalisez un modèle d'exploration de données en appliquant des filtres aux données utilisées dans l'apprentissage du modèle.|[Ajouter des modèles d’exploration de données à une structure &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|Mettez à jour et gérer des solutions d'exploration de données.|Lien à déterminer|  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels sur l’exploration de données &#40;Analysis Services&#41;](../../analysis-services/data-mining-tutorials-analysis-services.md)  
  
  