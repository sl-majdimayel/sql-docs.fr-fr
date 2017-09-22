---
title: IF... ELSE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/11/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IF_TSQL
- IF
dev_langs:
- TSQL
helpviewer_keywords:
- IF...ELSE keyword
- ELSE (IF...ELSE) keyword
- ELSE keyword
- IF keyword
ms.assetid: 676c881f-dee1-417a-bc51-55da62398e81
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ea7d020bc637ff2dda4ba0540de8385e99170cd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="ifelse-transact-sql"></a>IF...ELSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Impose les conditions d'exécution d'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui suit le mot clé IF et sa condition est exécutée si la condition est remplie, c'est-à-dire lorsque l'expression booléenne retourne la valeur TRUE. Le mot clé facultatif ELSE introduit une autre instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui est exécutée lorsque la condition IF n'est pas remplie : l'expression booléenne retourne alors la valeur FALSE.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
IF Boolean_expression   
     { sql_statement | statement_block }   
[ ELSE   
     { sql_statement | statement_block } ]   
```  
  
## <a name="arguments"></a>Arguments  
 *Expression_booléenne*  
 Expression qui renvoie TRUE ou FALSE. Si l'expression booléenne contient une instruction SELECT, cette dernière doit être mise entre parenthèses.  
  
 { *sql_statement*| *statement_block* }  
 Représente toute instruction ou tout groupe d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] tel que défini dans un bloc d'instructions. À moins que vous n'utilisiez un bloc d'instructions, la condition IF ou ELSE ne peut affecter les performances que d'une seule instruction [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Pour définir un bloc d'instructions, utilisez les mots clés de contrôle de flux BEGIN et END.  
  
## <a name="remarks"></a>Notes  
 Une construction IF...ELSE peut être utilisée dans des traitements d'instructions, des procédures stockées et des requêtes ad hoc. Lorsque cette construction est utilisée dans une procédure stockée, elle est souvent utilisée pour rechercher la présence de certains paramètres.  
  
 Les tests de la condition IF peuvent être imbriqués après une autre condition IF ou après une condition ELSE. La limite concernant le nombre de niveaux imbriqués dépend de la mémoire disponible.  
  
## <a name="example"></a>Exemple  
  
```  
IF DATENAME(weekday, GETDATE()) IN (N'Saturday', N'Sunday')
       SELECT 'Weekend';
ELSE 
       SELECT 'Weekday';
```  
  
 Pour plus d’exemples, consultez [ELSE &#40; si... AUTRE &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/else-if-else-transact-sql.md).  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant utilise `IF…ELSE` pour déterminer lequel des deux réponses permettant à l’utilisateur, en fonction du poids d’un élément dans le `DimProduct` table.  
  
```  
-- Uses AdventureWorksDW  
  
DECLARE @maxWeight float, @productKey integer  
SET @maxWeight = 100.00  
SET @productKey = 424  
IF @maxWeight <= (SELECT Weight from DimProduct 
                  WHERE ProductKey = @productKey)   
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is too heavy to ship and is only available for pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
ELSE  
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is available for shipping or pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [BEGIN... FIN &#40; Transact-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [FIN &#40; BEGIN... FIN &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Alors que &#40; Transact-SQL &#41;](../../t-sql/language-elements/while-transact-sql.md)   
 [CAS &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Langage de contrôle de flux &#40; Transact-SQL &#41; ](~/t-sql/language-elements/control-of-flow.md) [ELSE &#40; si... AUTRE &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/else-if-else-transact-sql.md) 
  
  



