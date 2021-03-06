---
title: Fonction de Conversion de types de données explicites | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- explicit data type conversion functions [ODBC]
- data type conversion functions [ODBC]
- functions [ODBC], explicit data type conversion functions
ms.assetid: d5789450-b668-4753-96c8-6789e955e7ed
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77cb69877324b36120b3a277688bb1ad737f5c4d
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54129819"
---
# <a name="explicit-data-type-conversion-function"></a>Fonctions de conversion de types de données explicites
Conversion de type de données explicite est spécifiée en termes de définitions de type de données SQL.  
  
 La syntaxe ODBC pour la fonction de conversion de type de données explicite ne limite pas les conversions. La validité de conversions spécifiques d’un type de données à un autre type de données sera déterminée par chaque implémentation spécifiques au pilote. Le pilote, car elle traduit la syntaxe ODBC la syntaxe native, rejette les conversions qui, bien qu’autorisée dans la syntaxe ODBC, ne sont pas pris en charge par la source de données. La fonction ODBC **SQLGetInfo**, avec la conversion options (telles que SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH et ainsi de suite), offre un moyen pour obtenir des informations sur les conversions prises en charge par la source de données .  
  
 Le format de la **convertir** fonction est :  
  
 **CONVERTIR (** _value_exp_, _data_type_**)**  
  
 La fonction retourne la valeur spécifiée par *value_exp* converti spécifié *data_type*, où *data_type* est un des mots clés suivants :  
  
|||  
|-|-|  
|SQL_BIGINT|SQL_INTERVAL_HOUR_TO_MINUTE|  
|SQL_BINARY|SQL_INTERVAL_HOUR_TO_SECOND|  
|SQL_BIT|SQL_INTERVAL_MINUTE_TO_SECOND|  
|SQL_CHAR|SQL_LONGVARBINARY|  
|SQL_DECIMAL|SQL_LONGVARCHAR|  
|SQL_DOUBLE|SQL_NUMERIC|  
|SQL_FLOAT|SQL_REAL|  
|SQL_GUID|SQL_SMALLINT|  
|SQL_INTEGER|SQL_DATE|  
|SQL_INTERVAL_MONTH|SQL_TIME|  
|SQL_INTERVAL_YEAR|SQL_TIMESTAMP|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_TINYINT|  
|SQL_INTERVAL_DAY|SQL_VARBINARY|  
|SQL_INTERVAL_HOUR|SQL_VARCHAR|  
|SQL_INTERVAL_MINUTE|SQL_WCHAR|  
|SQL_INTERVAL_SECOND|SQL_WLONGVARCHAR|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_WVARCHAR|  
|SQL_INTERVAL_DAY_TO_MINUTE||  
|SQL_INTERVAL_DAY_TO_SECOND||  
  
 La syntaxe ODBC pour la fonction de conversion de type de données explicite ne prend pas en charge la spécification de format de la conversion. Si la spécification des formats explicites est prise en charge par la source de données sous-jacente, un pilote doit spécifier une valeur par défaut ou implémenter la spécification de format.  
  
 L’argument *value_exp* peut être un nom de colonne, le résultat d’une autre fonction scalaire ou une valeur numérique ou la chaîne littérale. Exemple :  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 Convertit la sortie de la fonction scalaire CURDATE en une chaîne de caractères.  
  
 Étant donné que ODBC n’impose un type de données pour les valeurs de retour de fonctions scalaires (comme les fonctions sont souvent spécifiques à la source de données), applications doivent utiliser la fonction scalaire CONVERT chaque fois que possible de forcer la conversion de type de données.  
  
 Les deux exemples suivants illustrent l’utilisation de la **convertir** (fonction). Ces exemples supposent l’existence d’une table appelée employés, avec une colonne de MATEMP de type SQL_SMALLINT et une colonne EMPNAME de type SQL_CHAR.  
  
 Si une application spécifie l’instruction SQL suivante :  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Un pilote pour ORACLE se traduit par l’instruction SQL à :  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   Un pilote pour SQL Server se traduit par l’instruction SQL à :  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 Si une application spécifie l’instruction SQL suivante :  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   Un pilote pour ORACLE se traduit par l’instruction SQL à :  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   Un pilote pour SQL Server se traduit par l’instruction SQL à :  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Un pilote pour Ingres se traduit par l’instruction SQL à :  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
