---
title: Fonction CountRows (Générateur de rapports et SSRS) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b9bb3a1c8fcfa71560d4f5973a03588948ae99fd
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56292758"
---
# <a name="report-builder-functions---countrows-function"></a>Fonctions du Générateur de rapports - CountRows
  Retourne le nombre de lignes dans l'étendue spécifiée, y compris celles contenant des valeurs Null.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *portée*  
 (**String**) Nom d’un dataset, d’un groupe ou d’une région de données qui contient les éléments de rapport à compter.  
  
 *récursifs*  
 (**Type énuméré**) Facultatif. **Simple** (par défaut) ou **RdlRecursive**. Indique s'il faut effectuer l'agrégation de manière récursive.  
  
## <a name="return-type"></a>Type de retour  
 Retourne un **Integer**.  
  
## <a name="remarks"></a>Notes   
 **CountRows** compte toutes les lignes dans l'étendue spécifiée, y compris celles contenant des valeurs Null.  
  
 La valeur du paramètre *scope* ne peut pas être une expression et doit faire référence à l'étendue actuelle ou à une étendue contenante.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a> Exemple  
 L'exemple de code suivant affiche une expression qui calcule le nombre de lignes dans un groupe de lignes nommé `GroupbyCategory` (basé sur l'expression `[Category]`).  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
