---
title: Utilisation (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 459d6a0240ac2588c0924eae7bdae348a71f5946
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37990983"
---
# <a name="usage-dmx"></a>Utilisation (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Lorsque vous utilisez des Extensions DMX (Data Mining) pour définir un nouveau modèle d’exploration de données dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vous devez spécifier la façon dont l’algorithme d’exploration de données qui génère le modèle utilisera chaque colonne. Vous pouvez spécifier une colonne comme étant l'un des types suivants :  
  
-   **Clé**  
  
-   **Séquence clé**  
  
-   **Temps clé**  
  
-   **Predict**  
  
-   **PredictOnly**  
  
 En langage DMX, les colonnes non spécifiées sont considérées comme des colonnes d'entrée.  
  
 Pour traiter correctement un modèle, l'algorithme doit savoir quelle est la colonne clé qui identifie de manière unique chaque ligne, quelle est la colonne cible pour la création des prédictions si vous créez un modèle prévisible et quelles colonnes utiliser comme colonnes d'entrée pour créer les relations qui prévoient la colonne cible.  
  
 Colonnes qui sont spécifiées en tant que le **Predict** type sont utilisées en tant que colonnes d’entrée et de sortie. Colonnes qui sont spécifiées en tant que **PredictOnly** sont uniquement utilisées comme colonnes de sortie. Il est possible que des algorithmes spécifiques considèrent les colonnes de type Predict différemment.  
  
 Pour plus d’informations sur la colonne types d’utilisation qui [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge, consultez [colonnes du modèle d’exploration de données](../analysis-services/data-mining/mining-model-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Data Mining Extensions &#40;DMX&#41; référence](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;DMX&#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
