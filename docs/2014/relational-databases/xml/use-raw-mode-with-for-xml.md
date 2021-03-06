---
title: Utiliser le mode RAW avec FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aec0ec20c9bd46a06560f5ce6ebd374e937f0343
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537041"
---
# <a name="use-raw-mode-with-for-xml"></a>Utiliser le mode RAW avec FOR XML
  Le mode RAW transforme chaque ligne du jeu de résultats de la requête en un élément XML contenant l’identificateur générique \<row> ou le nom d’élément éventuellement fourni. Par défaut, chaque valeur de colonne dans l’ensemble de lignes qui n’est pas NULL est mappée à un attribut de l’élément \<row>. Si la directive ELEMENTS est ajoutée à la clause FOR XML, chaque valeur de colonne est mappée à un sous-élément de l’élément \<row>. Avec la directive ELEMENTS, vous pouvez éventuellement spécifier l'option XSINIL pour mapper les valeurs de colonnes NULL dans le jeu de résultats à un élément qui possède l'attribut xsi:nil=`"`true`"`.  
  
 Vous pouvez demander un schéma pour les données XML résultantes. Spécifier l'option XMLDATA permet de retourner un schéma XDR en ligne. Spécifier l'option XMLSCHEMA permet de retourner un schéma XSD en ligne. Le schéma apparaît au début des données. Dans le résultat, la référence à l'espace de noms du schéma est répétée pour chaque élément de niveau supérieur.  
  
 L'option BINARY BASE64 doit être spécifiée dans la clause FOR XML pour retourner les données binaires dans un format encodé en base 64. En mode RAW, la récupération de données binaires sans spécification de l'option BINARY BASE64 génère une erreur.  
  
## <a name="in-this-section"></a>Dans cette section  
 Cette section contient les exemples suivants :  
  
-   [Exemple : Récupération des informations de modèle de produit au format XML](example-retrieving-product-model-information-as-xml.md)  
  
-   [Exemple : Spécification de XSINIL avec la Directive ELEMENTS](example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [Exemple : Demande de schémas comme résultats avec les Options XMLDATA et XMLSCHEMA](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [Exemple : Récupération de données binaires](example-retrieving-binary-data.md)  
  
-   [Exemple : Renommer le &#60;ligne&#62; élément](example-renaming-the-row-element.md)  
  
-   [Exemple : Spécification d’un élément racine pour les données XML généré par FOR XML](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [Exemple : Interrogation de colonnes](example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [UTiliser le mode AUTO avec FOR XML](use-auto-mode-with-for-xml.md)   
 [Utiliser le mode EXPLICIT avec FOR XML](use-explicit-mode-with-for-xml.md)   
 [Utiliser le mode PATH avec FOR XML](use-path-mode-with-for-xml.md)   
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML &#40;SQL Server&#41;](../xml/for-xml-sql-server.md)  
  
  
