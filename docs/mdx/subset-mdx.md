---
title: Sous-ensemble (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 07d813587dc530924becbb187a970f78022e5476
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743338"
---
# <a name="subset-mdx"></a>Subset (MDX)


  Retourne un sous-ensemble de tuples d'un jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Subset(Set_Expression, Start [ ,Count ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Démarrer*  
 Expression numérique valide qui précise la position du premier tuple à retourner.  
  
 *Nombre*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
## <a name="remarks"></a>Notes  
 Dans le jeu spécifié, le **sous-ensemble** fonction retourne un sous-ensemble qui contient le nombre spécifié de tuples, en commençant à la position de début spécifiée. La position de départ est fondée sur un index de base zéro : zéro (0) correspond au premier tuple dans le jeu spécifié, 1 correspond au deuxième, et ainsi de suite.  
  
 Si *nombre* n’est pas spécifié, la fonction retourne tous les tuples à partir de *Démarrer* à la fin de l’ensemble.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la mesure Reseller Sales pour les cinq premières sous-catégories de vente de produits, quelle que soit la hiérarchie et conformément à la mesure Reseller Gross Profit (marge brute du revendeur). Le **sous-ensemble** fonction est utilisée pour retourner uniquement les cinq premiers jeux dans le résultat, une fois que le résultat est trié à l’aide de la **ordre** (fonction).  
  
```  
SELECT Subset  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,0  
   ,5  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
