---
title: "Fonction min (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa1ee96f-9fc4-4775-b9d4-c6187dc37e27
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b38b762b36db8e43b1a572bc98ad5e5995c8cfe0
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="report-builder-functions---min-function"></a>Fonctions du Générateur de rapports - Min (fonction)
  Retourne la valeur minimale de toutes les valeurs numériques non Null spécifiées par l'expression, dans le contexte de l'étendue donnée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Min(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *expression*  
 (**Variant**) Expression sur laquelle effectuer l’agrégation.  
  
 *portée*  
 (**Chaîne**) Facultatif. Nom d'un dataset, d'un groupe ou d'une région de données qui contient les éléments de rapport auxquels appliquer la fonction d'agrégation. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
 *récursifs*  
 (**Type énuméré**) Facultatif. **Simple** (par défaut) ou **RdlRecursive**. Indique s'il faut effectuer l'agrégation de manière récursive.  
  
## <a name="return-type"></a>Type de retour  
 Déterminé par le type de l'expression.  
  
## <a name="remarks"></a>Notes  
 Le jeu de données spécifié dans l'expression doit avoir le même type de données. Pour convertir des données qui ont plusieurs types de données numériques en un même type de données, utilisez des fonctions de conversion telles que **CInt**, **CDbl** ou **CDec**. Pour plus d'informations, consultez [Fonctions de conversion de types de données](http://go.microsoft.com/fwlink/?LinkId=96142).  
  
 La valeur du paramètre *scope* doit être une constante de chaîne et ne peut pas être une expression. Pour les agrégats externes ou les agrégats qui ne spécifient pas d'autres agrégats, le paramètre *scope* doit faire référence à l'étendue actuelle ou à une étendue contenante. Pour les agrégats d'agrégats, les agrégats imbriqués peuvent spécifier une étendue enfant.  
  
 *Expression* peut contenir des appels aux fonctions d'agrégation imbriquées avec les exceptions et conditions suivantes :  
  
-   Le paramètre*Scope* des agrégats imbriqués doit être identique à l'étendue de l'agrégat externe ou contenu par celle-ci. Pour toutes les étendues distinctes de l'expression, une étendue doit figurer dans une relation enfant avec toutes les autres étendues.  
  
-   Le paramètre*Scope* des agrégats imbriqués ne peut pas être le nom d'un dataset.  
  
-   *Expression* ne doit pas contenir les fonctions **First**, **Last**, **Previous**ou **RunningValue** .  
  
-   *Expression* ne doit pas contenir les agrégats imbriqués qui spécifient *recursive*.  
  
 Pour plus d’informations, consultez [Informations de référence sur les fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code ci-dessous fournit le total le plus faible de l'étendue actuelle.  
  
```  
=Min(Fields!OrderTotal.Value)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  