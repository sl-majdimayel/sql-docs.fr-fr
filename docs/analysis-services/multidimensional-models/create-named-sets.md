---
title: "Créer des jeux nommés | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4a98318cc28f79ab24af1ecce382b0b39a78dfab
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-named-sets"></a>Créer des jeux nommés
  Un jeu nommé est un ensemble de membres de dimension (ou une expression de jeu) créé en vue d'être réutilisé, par exemple dans des requêtes MDX (Multidimensional Expressions). Vous pouvez créer des jeux nommés en combinant des données de cube, des opérateurs arithmétiques, des nombres et des fonctions. Par exemple, vous pouvez créer le jeu nommé « Dix meilleures usines » qui contient les dix membres de la dimension Usines ayant les valeurs les plus élevées pour la mesure Production. « Dix meilleures usines » peut ensuite être utilisé dans des requêtes par les utilisateurs finaux. Par exemple, un utilisateur peut placer « Dix meilleures usines » sur un axe et la dimension Measures, avec Production, sur un autre axe. Pour plus d’informations, consultez [Calculs dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md) et [Création de jeux nommés à l’aide d’expressions MDX &#40;MDX&#41;](../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md).  
  
 Pour créer un jeu nommé, utilisez la commande **Nouveau jeu nommé** , disponible sous l'onglet **Calculs** du Concepteur de cube. Cette commande peut être appelée dans le menu **Cube** de la barre d’outils de l’onglet **Calculs** . Cette commande affiche un formulaire permettant de spécifier les options suivantes pour le jeu nommé :  
  
 **Nom**  
 Choisissez le nom du jeu nommé. C'est celui que verront les utilisateurs lorsqu'ils parcourront le cube.  
  
 **Expression**  
 Spécifiez l'expression qui produit le jeu nommé. Cette expression peut être écrite en MDX. L'expression peut contenir l'un des éléments suivants :  
  
-   Expressions de données représentant des composants de cube (par exemple des dimensions, des niveaux, des mesures, etc.)  
  
-   Opérateurs arithmétiques.  
  
-   Nombres.  
  
-   Fonctions.  
  
 Vous pouvez copier ou faire glisser des composants de cube depuis l’onglet **Métadonnées** du volet **Outils de calcul** vers la zone **Expression** du volet **Éditeur de formulaire de jeu nommé** . Vous pouvez copier ou faire glisser des fonctions depuis l’onglet **Fonctions** du volet **Outils de calcul** vers la zone **Expression** du volet **Éditeur de formulaire de jeu nommé** .  
  
> [!IMPORTANT]  
>  Si vous créez l'expression du jeu en spécifiant explicitement ses membres, placez la liste des membres dans des accolades ({}).  
  
## <a name="see-also"></a>Voir aussi  
 [Calculs dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)  
  
  