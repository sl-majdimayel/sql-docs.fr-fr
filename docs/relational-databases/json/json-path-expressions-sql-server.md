---
title: Expressions de chemin JSON (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 01/23/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, path expressions
- path expressions (JSON)
ms.assetid: 25ea679c-84cc-4977-867c-2cbe9d192553
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 07c873941669f7a36ff9b93651a938ecae2662b7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/31/2017

---
# <a name="json-path-expressions-sql-server"></a>Expressions de chemin JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Utilisez les expressions de chemins JSON pour référencer les propriétés des objets JSON.  
  
 Vous devez fournir une expression de chemin lorsque vous appelez les fonctions suivantes.  
  
-   Lorsque vous appelez **OPENJSON** pour créer une vue relationnelle des données JSON. Pour plus d’informations, consultez [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
-   Quand vous appelez **JSON_VALUE** pour extraire une valeur de texte JSON. Pour plus d’informations, consultez [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md).  
  
-   Quand vous appelez **JSON_QUERY** pour extraire un tableau ou un objet JSON. Pour plus d’informations, consultez [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  
  
-   Quand vous appelez **JSON_MODIFY** pour mettre à jour la valeur d’une propriété dans une chaîne JSON. Pour plus d’informations, consultez [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md).  

## <a name="parts-of-a-path-expression"></a>Parties d’une expression de chemin
 Une expression de chemin comporte deux composants.  
  
1.  Le [mode PATH](#PATHMODE) facultatif, avec la valeur **lax** ou **strict**.  
  
2.  Le [chemin](#PATH) lui-même.  

##  <a name="PATHMODE"></a> Path mode  
 Au début de l’expression de chemin, vous pouvez éventuellement déclarer le mode PATH en spécifiant le mot clé **lax** ou **strict**. La valeur par défaut est **lax**.  
  
-   En mode **lax**, la fonction retourne des valeurs vides si l’expression de chemin contient une erreur. Par exemple, si vous demandez la valeur **$.name** et si le texte JSON ne contient pas de clé **name**, la fonction retourne une valeur null mais ne génère pas d’erreur.  
  
-   En mode **strict**, la fonction génère une erreur si l’expression de chemin contient une erreur.  

La requête suivante spécifie explicitement le mode `lax` dans l’expression de chemin.

```sql  
DECLARE @json NVARCHAR(MAX)
SET @json=N'{ ... }'

SELECT * FROM OPENJSON(@json, N'lax $.info')
```  
  
##  <a name="PATH"></a> Path  
 Après la déclaration de mode de chemin facultatif, spécifiez le chemin lui-même.  
  
-   Le signe dollar (`$`) représente l’élément de contexte.  
  
-   Le chemin de la propriété est un ensemble d’étapes de chemin. Les étapes de chemin peuvent contenir les éléments et les opérateurs suivants.  
  
    -   Noms de clés. Par exemple, `$.name` et `$."first name"`. Si le nom de clé commence par un signe dollar ou contient des caractères spéciaux tels que des espaces, placez-le entre guillemets.   
  
    -   Éléments du tableau. Par exemple, `$.product[3]`. Les tableaux sont de base zéro.  
  
    -   L’opérateur point (`.`) indique un membre d’un objet. Par exemple, dans `$.people[1].surname`, `surname` est un enfant de `people`.
  
## <a name="examples"></a>Exemples  
 Les exemples de cette section font référence au texte JSON suivant.  
  
```json  
{
    "people": [{
        "name": "John",
        "surname": "Doe"
    }, {
        "name": "Jane",
        "surname": null,
        "active": true
    }]
}
```  
  
 Le tableau suivant présente des exemples d’expressions de chemin.  
  
|Expression de chemin|Valeur|  
|---------------------|-----------|  
|$.people[0].name|John|  
|$.people[1]|{ "name": "Jane",  "surname": null, "active": true }|  
|$.people[1].surname|Null|  
|$|{ "people": [ { "name": "John",  "surname": "Doe" },<br />   { "name": "Jane",  "surname": null, "active": true } ] }|  
  
## <a name="how-built-in-functions-handle-duplicate-paths"></a>Comment les fonctions intégrées gèrent-elles les chemins en double ?  
 Si le texte JSON contient des propriétés dupliquées (par exemple, deux clés portant le même nom au même niveau), les fonctions **JSON_VALUE** et **JSON_QUERY** retournent uniquement la première valeur correspondant au chemin. Pour analyser un objet JSON contenant des clés dupliquées et retourner toutes les valeurs, utilisez **OPENJSON**, comme indiqué dans l’exemple suivant.  
  
```sql  
DECLARE @json NVARCHAR(MAX)
SET @json=N'{"person":{"info":{"name":"John", "name":"Jack"}}}'

SELECT value
FROM OPENJSON(@json,'$.person.info') 
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la prise en charge intégrée de JSON dans SQL Server  
Pour accéder à un grand nombre de solutions spécifiques, de cas d’usage et de recommandations, consultez les [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et Azure SQL Database, écrits par Jovan Popovic (Microsoft Program Manager).
  
## <a name="see-also"></a>Voir aussi  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)  
  
  
