---
title: DB_ID (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DB_ID_TSQL
- DB_ID
dev_langs:
- TSQL
helpviewer_keywords:
- viewing database ID numbers
- IDs [SQL Server], databases
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
- displaying database ID numbers
- DB_ID function
ms.assetid: 7b3aef89-a6fd-4144-b468-bf87ebf381b8
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 60272ce672c0a32738b0084ea86f8907ec7fc0a5
ms.openlocfilehash: 99497c63e037054daf249ac75ef35073f102a498
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="dbid-transact-sql"></a>DB_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne le numéro d'identification (ID) de la base de données.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DB_ID ( [ 'database_name' ] )   
```  
  
## <a name="arguments"></a>Arguments  
'*nom_base_de_données*'  
Nom de base de données utilisé pour retourner le numéro d'identification (ID) de la base de données correspondante. *database_name* est **sysname**. Si *nom_base_de_données* est omis, l’ID de base de données actuel est retourné.
  
## <a name="return-types"></a>Types de retour
**int**
  
## <a name="permissions"></a>Permissions  
Si l’appelant de **DB_ID** n’est pas le propriétaire de la base de données et la base de données n’est pas **master** ou **tempdb**, les autorisations minimales requises pour consulter la ligne correspondante sont ALTER ANY DATABASE ou VIEW ANY DATABASE au niveau du serveur, ou l’autorisation CREATE DATABASE dans le **master** base de données. La base de données à laquelle l'appelant est connecté peut toujours être vue dans **sys.databases**.
  
> [!IMPORTANT]  
>  Par défaut, le rôle public a l’autorisation VIEW ANY DATABASE, ce qui permet des connexions d’accès aux informations de base de données. Pour bloquer une connexion à partir de la capacité de détecter une base de données, RÉVOQUER l’autorisation VIEW ANY DATABASE public, ou refuser l’autorisation VIEW ANY DATABASE pour des connexions individuelles.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-database-id-of-the-current-database"></a>A. Retour de l'ID de la base de données active  
L'exemple suivant retourne l'ID de la base de données active.
  
```sql
SELECT DB_ID() AS [Database ID];  
GO  
```  
  
### <a name="b-returning-the-database-id-of-a-specified-database"></a>B. Retour de l'ID d'une base de données spécifique  
L’exemple suivant retourne l’ID de base de données de la [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données.
  
```sql
SELECT DB_ID(N'AdventureWorks2008R2') AS [Database ID];  
GO  
```  
  
### <a name="c-using-dbid-to-specify-the-value-of-a-system-function-parameter"></a>C. Utilisation de DB_ID pour spécifier la valeur d'un paramètre de fonction système  
L’exemple suivant utilise `DB`_`ID` pour retourner l’ID de base de données de la [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données dans la fonction système `sys.dm_db` \_ `index` \_ `operational` \_ `stats`. Le premier paramètre de la fonction est un ID de base de données.
  
```sql
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-return-the-id-of-the-current-database"></a>D. Retourner l’ID de la base de données en cours  
L'exemple suivant retourne l'ID de la base de données active.
  
```sql
SELECT DB_ID();  
```  
  
### <a name="e-return-the-id-of-a-named-database"></a>E. Retourne l’ID de base de données nommée.  
L’exemple suivant retourne l’ID de base de données de la base de données AdventureWorksDW2012.
  
```sql
SELECT DB_ID('AdventureWorksPDW2012');  
```  
  
## <a name="see-also"></a>Voir aussi
[Db_name &#40; Transact-SQL &#41;](../../t-sql/functions/db-name-transact-sql.md)  
[Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)
  
  

