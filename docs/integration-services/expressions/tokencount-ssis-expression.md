---
title: TOKENCOUNT (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3c1ee4bf54117a9b2b29aa2e892186d61b44683c
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58271219"
---
# <a name="tokencount-ssis-expression"></a>TOKENCOUNT (expression SSIS)
  Retourne le nombre de jetons d'une chaîne qui contient des jetons séparés par les délimiteurs spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
 Chaîne qui contient des jetons séparés par des délimiteurs.  
  
 *delimiter_string*  
 Chaîne qui contient les caractères de délimitation. Par exemple, « ; , » contient trois caractères de délimitation : le point-virgule, un espace vide et une virgule.  
  
## <a name="result-types"></a>Types des résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes   
 Les remarques suivantes s'appliquent à la fonction TOKEN :  
  
-   La chaîne de délimitation peut contenir un ou plusieurs caractères de délimitation.  
  
-   Les délimiteurs de début sont ignorés.  
  
-   TOKENCOUNT fonctionne uniquement avec le type de données DT_WSTR. Un argument *character_expression* représentant un littéral de chaîne ou une colonne de données du type de données DT_STR est implicitement converti dans le type de données DT_WSTR avant que la fonction TOKEN ne soit exécutée. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR.  
  
-   TOKENCOUNT retourne 0 (zéro) si character_expression est Null.  
  
-   Vous pouvez utiliser des variables et des colonnes en tant qu'arguments pour cette expression.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Dans l’exemple suivant, la fonction TOKENCOUNT retourne 3, car la chaîne contient trois jetons : « 01 », « 12 » et « 2011 ».  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 Dans l’exemple suivant, la fonction TOKENCOUNT retourne 4, car il existe quatre jetons (« a », « little », « white », « dog »).  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 Dans l’exemple suivant, la fonction TOKENCOUNT retourne 1. La fonction analyse la chaîne d'entrée à la recherche de délimiteurs et comme il n'y en a pas dans la chaîne, elle ajoute simplement la chaîne entière en tant que premier jeton.  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 Dans l'exemple suivant, la fonction TOKENCOUNT retourne 4. La chaîne de délimitation de cet exemple contient 5 délimiteurs. La chaîne d’entrée contient 4 jetons : « a », « little », « white », « dog ».  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 Dans l'exemple suivant, la fonction TOKENCOUNT retourne 4. Elle ignore tous les espaces de début.  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
