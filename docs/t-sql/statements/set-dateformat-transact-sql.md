---
title: SET DATEFORMAT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATEFORMAT
- SET DATEFORMAT
- SET_DATEFORMAT_TSQL
- DATEFORMAT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], formats
- dates [SQL Server], ordering date parts
- SET DATEFORMAT option [SQL Server]
- DATEFORMAT option [SQL Server]
- date and time [SQL Server], SET DATEFORMAT
- options [SQL Server], date
- date and time [SQL Server], DATEFORMAT
- dateparts [SQL Server], dateformat
ms.assetid: da217878-7ec4-477e-aa13-604073c948f8
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9262ca6e0f2dce018ae925b05e306cc43753a0b7
ms.sourcegitcommit: 5ef24b3229b4659ede891b0af2125ef22bd94b96
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759972"
---
# <a name="set-dateformat-transact-sql"></a>SET DATEFORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Définit le classement des parties de date mois, jour et année pour interpréter les chaînes de caractères de date. Ces chaînes sont de type **date**, **smalldatetime**, **datetime**, **datetime2** ou **datetimeoffset**.  
  
 Pour obtenir une vue d’ensemble de tous les types de données et fonctions de date et d’heure [!INCLUDE[tsql](../../includes/tsql-md.md)], consultez [Types de données et fonctions de date et d’heure &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SET DATEFORMAT { format | @format_var }   
```  
  
## <a name="arguments"></a>Arguments  
 *format* | **@**_format_var_  
 Ordre des parties de la date. Les paramètres valides sont **mdy**, **dmy**, **ymd**, **ydm**, **myd** et **dym**. Il peut s'agir du format Unicode ou d'un jeu de caractères codés sur deux octets (DBCS) converti en Unicode. La valeur par défaut pour l’anglais des États-Unis est **mdy**. Pour connaître le paramètre DATEFORMAT par défaut de toutes les langues prises en charge, consultez [sp_helplanguage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md).  
  
## <a name="remarks"></a>Notes   
 Le paramètre DATEFORMAT **ydm** n’est pas pris en charge pour les types de données **date**, **datetime2** et **datetimeoffset**.  
  
 Le paramètre DATEFORMAT peut interpréter des chaînes de caractères différemment pour les types de données de date, en fonction de leur format de chaîne. Par exemple, les interprétations **datetime** et **smalldatetime** peuvent ne pas correspondre à **date**, **datetime2** ou  **datetimeoffset**. Le paramètre DATEFORMAT affecte l’interprétation des chaînes de caractères quand elles sont converties en valeurs de date pour la base de données. Il n’affecte pas l’affichage des valeurs du type de données Date ni leur format de stockage dans la base de données.  
  
 Certains formats de chaînes de caractères, par exemple ISO 8601, sont interprétés indépendamment du paramètre DATEFORMAT.  
  
 L'option SET DATEFORMAT est appliquée lors de l'exécution, et non pas lors de l'analyse.  
  
 SET DATEFORMAT remplace le paramètre de format de date implicite de [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise différentes chaînes de date comme entrées dans les sessions avec le même paramètre `DATEFORMAT`.  
  
```  
-- Set date format to day/month/year.  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '31/12/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: 2008-12-31 09:01:01.123  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '12/31/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: Msg 241: Conversion failed when converting date and/or time -- from character string.  
  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  

