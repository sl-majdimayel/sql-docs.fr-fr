---
title: Propriétés personnalisées de la destination ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 07508c40-6c08-4359-96cd-8ff17671244d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bedbe74352ca317497d731acc0ff542eb0b8bd63
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58272908"
---
# <a name="odbc-destination-custom-properties"></a>Propriétés personnalisées des destinations ODBC
  Le tableau suivant décrit les propriétés personnalisées de la destination ODBC. Toutes les propriétés peuvent être définies à partir des expressions de propriété SSIS.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|Connexion|Connexion ODBC|Connexion ODBC utilisée pour accéder à la base de données de destination.|  
|BatchSize|Entier|Taille du lot pour le chargement en bloc. Il s’agit du nombre de lignes chargées dans un même lot. Cette valeur est valide uniquement si la liaison de paramètre selon les lignes est prise en charge. Si la liaison de paramètre selon les lignes n'est pas prise en charge, la taille de lot est 1.|  
|BindCharColumnAs|Integer (énumération)|Cette propriété détermine la manière dont la destination ODBC lie les colonnes avec des types chaîne à plusieurs octets, tels que SQL_CHAR, SQL_VARCHAR ou SQL_LONGVARCHAR.<br /><br /> Les valeurs possibles sont Unicode (0), qui lie les colonnes en tant que SQL_C_WCHAR, et ANSI (1), qui lie les colonnes en tant SQL_C_CHAR). La valeur par défaut est Unicode (0).<br /><br /> Unicode est la meilleure solution pour la plupart des fournisseurs ODBC 3.x et les fournisseurs ODBC 2.x qui prennent en charge la liaison des paramètres CHAR en tant que chaînes étendues. Lorsque vous sélectionnez Unicode et que ExposeCharColumnsAsUnicode a la valeur True, l'utilisateur n'a pas besoin de spécifier la page de codes utilisée par la base de données source.<br /><br /> **Remarque :** Cette propriété n’est pas disponible dans **l’Éditeur de destination ODBC**mais peut être définie à l’aide de **l’Éditeur avancé**.|  
|BindNumericAs|Integer (énumération)|Cette propriété détermine la manière dont la destination ODBC lie les colonnes comportant des données numériques avec les types de données SQL_TYPE_NUMERIC et SQL_TYPE_DECIMAL.<br /><br /> Les valeurs possibles sont Char (0), qui lie les colonnes en tant que SQL_C_CHAR et Numérique (1), qui lie les colonnes en tant que SQL_C_NUMERIC. La valeur par défaut est Char (0).<br /><br /> **Remarque**: Cette propriété n’est pas disponible dans **l’Éditeur de destination ODBC**mais peut être définie à l’aide de **l’Éditeur avancé**.|  
|DefaultCodePage|Entier|Page de codes à utiliser pour les colonnes de chaîne.<br /><br /> **Remarque**: Cette propriété n’est pas disponible dans **l’Éditeur de destination ODBC**mais peut être définie à l’aide de **l’Éditeur avancé**.|  
|InsertMethod|Integer (énumération)|Méthode utilisée pour insérer les données. Les valeurs possibles sont Ligne par ligne (0) et Lot (1). La valeur par défaut est Lot (1).<br /><br /> Pour plus d’informations sur ces options, consultez « Options de chargement » dans la rubrique [Destination ODBC](../../integration-services/data-flow/odbc-destination.md).|  
|StatementTimeout|Entier|Nombre de secondes pendant lequel attendre l'exécution d'une instruction SQL avant de la retourner à l'application avec une erreur. La valeur par défaut est 120.|  
|TableName|String|Nom de la table de destination dans laquelle les données sont insérées.|  
|TransactionSize|Entier|Nombre d'insertions dans une transaction unique. La valeur par défaut est 0, ce qui signifie que la destination ODBC fonctionne en mode de validation automatique.<br /><br /> Étant donné que le gestionnaire de connexions ODBC ne prend pas en charge les transactions distribuées, il est possible d'attribuer à cette propriété une valeur autre que 0. Toutefois, si la propriété **RetainSameConnection** du gestionnaire de connexions a la valeur **true** , cette propriété doit avoir la valeur 0.<br /><br /> **Remarque**: Cette propriété n’est pas disponible dans **l’Éditeur de destination ODBC**mais peut être définie à l’aide de **l’Éditeur avancé**.|  
|LobChunkSize|Entier|Taille de segment allouée pour les colonnes LOB.|  
  
  
