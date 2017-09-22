---
title: "ALTER INDEX (index XML sélectifs) | Documents Microsoft"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cca96a8f-7737-42d2-bbcc-03d5f858dcc1
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e7854dd1d9365f97628341c4160c368f97308302
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-index-selective-xml-indexes"></a>ALTER INDEX (index XML sélectifs)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Modifie un index XML sélectif existant. L'instruction ALTER INDEX modifie un ou plusieurs des éléments suivants :  
  
-   La liste de chemins d'accès indexés (clause FOR).  
  
-   La liste des espaces de noms (clause WITH XMLNAMESPACES).  
  
-   Les options d'index (clause WITH).  
  
 Vous ne pouvez pas modifier des index XML secondaires sélectifs. Pour plus d’informations, consultez [Create, Alter et Drop des index XML secondaires sélectifs](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ALTER INDEX index_name  
    ON <table_object>   
    [WITH XMLNAMESPACES ( <xmlnamespace_list> )]  
    FOR ( <promoted_node_path_action_list> )  
    [WITH ( <index_options> )]  
  
<table_object> ::=   
{ [database_name. [schema_name ] . | schema_name. ] table_name }  
<promoted_node_path_action_list> ::=   
<promoted_node_path_action_item> [, <promoted_node_path_action_list>]  
  
<promoted_node_path_action_item>::=   
<add_node_path_item_action> | <remove_node_path_item_action>  
  
<add_node_path_item_action> ::=  
ADD <path_name> = <promoted_node_path_item>  
  
<promoted_node_path_item>::=  
<xquery_node_path_item> | <sql_values_node_path_item>  
  
<remove_node_path_item_action> ::= REMOVE <path_name>   
  
<path_name_or_typed_node_path>::=   
<path_name> | <typed_node_path>  
  
<typed_node_path> ::=   
<node_path> [[AS XQUERY <xsd_type_ext>] | [AS SQL <sql_type>]]  
  
<xquery_node_path_item> ::=   
<node_path> [AS XQUERY <xsd_type_or_node_hint>] [SINGLETON]  
  
<xsd_type_or_node_hint> ::=   
[<xsd_type>] [MAXLENGTH(x)] | 'node()'  
  
<sql_values_node_path_item> ::=   
<node_path> AS SQL <sql_type> [SINGLETON]  
  
<node_path> ::=   
character_string_literal  
  
<xsd_type_ext> ::=   
character_string_literal  
  
<sql_type> ::=   
identifier  
  
<path_name> ::=   
identifier  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
<xmlnamespace_uri> AS <xmlnamespace_prefix>  
  
<xml_namespace_uri> ::= character_string_literal  
<xml_namespace_prefix> ::= identifier  
  
<index_options> ::=   
(   
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY =OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE =OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> Arguments  
 *index_name*  
 Nom de l'index existant à modifier.  
  
 *\<table_object >*  
 Table contenant la colonne XML à indexer. Utilisez l'un des éléments suivants :  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 [WITH XMLNAMESPACES **(** \<xmlnamespace_list > **)**]  
 Liste des espaces de noms utilisés par les chemins d'accès à indexer. Pour plus d’informations sur la syntaxe de la clause WITH XMLNAMESPACES, consultez [WITH XMLNAMESPACES &#40; Transact-SQL &#41; ](../../t-sql/xml/with-xmlnamespaces.md).  
  
 POUR **(** \<promoted_node_path_action_list > **)**  
 Liste des chemins d'accès indexés à ajouter ou à supprimer.  
  
-   **Ajoutez un chemin d’accès.** Lorsque vous AJOUTEZ un chemin d'accès, vous utilisez la même syntaxe que celle qui est utilisée pour créer des chemins d'accès à l'aide de l'instruction CREATE SELECTIVE XML INDEX. Pour plus d’informations sur les chemins d’accès que vous pouvez spécifier dans l’instruction CREATE ou ALTER, consultez [spécifier les chemins d’accès et les indicateurs d’optimisation pour les index XML sélectifs](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md).  
  
-   **SUPPRIMER un chemin d’accès.** Lorsque vous SUPPRIMEZ un chemin d'accès, vous devez fournir le nom qui a été donné au chemin d'accès au moment de sa création.  
  
 [Avec **(** \<index_options > **)**]  
 Vous ne pouvez spécifier \<index_options > lorsque vous utilisez ALTER INDEX sans la clause FOR. Lorsque vous utilisez ALTER INDEX pour ajouter ou supprimer des chemins d'accès dans l'index, les options d'index ne sont pas des arguments valides. Pour plus d’informations sur les options d’index, consultez [CREATE XML INDEX &#40; Index XML sélectifs &#41; ](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]  
>  Lorsque vous exécutez une instruction ALTER INDEX, l'index XML sélectif est toujours reconstruit. Assurez-vous de prendre en compte l'impact de ce processus sur les ressources du serveur.  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 L'exécution de ALTER INDEX nécessite une autorisation ALTER sur la table ou la vue.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre une instruction ALTER INDEX. Cette instruction ajoute le chemin `'/a/b/m'` à la partie XQuery de l’index et supprime le chemin `'/a/b/e'` de la partie SQL de l’index créé dans l’exemple de la rubrique [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md). Le chemin d'accès à supprimer est identifié par le nom qui lui a été donné lors de sa création.  
  
```tsql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
);  
```  
  
 L'exemple suivant illustre une instruction ALTER INDEX qui spécifie les options d'index. Les options d'index sont autorisées, car l'instruction n'utilise pas de clause FOR pour ajouter ou supprimer des chemins d'accès.  
  
```tsql  
ALTER INDEX sxi_index  
ON Tbl  
PAD_INDEX = ON;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Index XML sélectifs &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Créer, modifier et supprimer des index XML sélectif](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)   
 [Spécifier les chemins d’accès et les indicateurs d’optimisation des index XML sélectifs](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md)  
  
  
