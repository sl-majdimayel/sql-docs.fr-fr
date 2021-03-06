---
title: ': (Plage) (MDX) | Documents Microsoft'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 882082d503bf88f21566ac79ea4393a24ee551e4
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742778"
---
# <a name="-range-mdx"></a>: (Plage) (MDX)


  Exécute une opération de jeu qui retourne un jeu naturellement ordonné, dont les extrémités sont représentées par les deux membres spécifiés, entre lesquels figurent les autres membres du jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression : Member_Expression      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="return-value"></a>Valeur de retour  
 Jeu contenant les membres spécifiés et tous les membres situés entre eux.  
  
## <a name="remarks"></a>Notes  
 Les deux paramètres doivent spécifier des membres situés dans le même niveau et la même hiérarchie d'une dimension donnée. Si les deux paramètres spécifient le même membre, le **: (plage)** renvoie un jeu qui contient uniquement le membre spécifié. Si le premier paramètre est Null, le jeu contient tous les membres du début du niveau du membre spécifié dans le second paramètre jusqu'au dernier membre (inclus) sur le même niveau. Si le second paramètre est Null, le jeu contient tous les membres du membre spécifié dans le premier paramètre jusqu'au dernier membre (inclus) sur le même niveau.  
  
 Cet opérateur de jeu n'a aucun équivalent fonctionnel dans MDX.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This query returns the freight cost per user  
-- for products, averaged by month, for the first quarter.  
With Member [Measures].[Freight Per Customer] as  
 (  
     [Measures].[Internet Freight Cost]  
     /   
     [Measures].[Customer Count]  
)  
  
SELECT   
    {[Ship Date].[Calendar].[Month].&[2004]&[1] : [Ship Date].[Calendar].[Month].&[2004]&[3]} ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
