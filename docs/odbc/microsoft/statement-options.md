---
title: "Options de l’instruction | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom statement options [ODBC]
- statement options [ODBC]
- ODBC driver for Oracle [ODBC], statement options
ms.assetid: cd73b769-c8b5-43e0-9f80-b3011b7a6162
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8e73ba4a1fe0bd8a7fb65b8986745f9d2edee550
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="statement-options"></a>Options d’instruction
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Ces options permettent la personnalisation d’une instruction d’exécution spécifique au sein d’une application.  
  
|Option d’instruction|Remarques|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Ne peut pas dépasser 2 147 483 647 octets ou la mémoire disponible.|  
|SQL_CONCURRENCY|Les valeurs autorisées, consultez la [Type de curseur et les combinaisons d’accès concurrentiel](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Le pilote ne permet pas de type SQL_CURSOR_DYNAMIC. Consultez [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) pour plus d’informations. Les valeurs autorisées, consultez la [Type de curseur et les combinaisons d’accès concurrentiel](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Retourne une valeur d’entier 32 bits qui est le signet pour le numéro d’enregistrement en cours. Obtenir uniquement ; Impossible de définir.|  
|SQL_KEYSET_SIZE|Peut être défini uniquement à 0.|  
|SQL_MAX_ROWS|Le nombre maximal de lignes à retourner à partir d’un résultat défini.|  
|SQL_ROW_NUMBER|Retourne un entier de 32 bits spécifiant la position de la ligne actuelle dans le jeu de résultats. Obtenir uniquement ; Impossible de définir.|  
|SQL_ROWSET_SIZE|Ne peut pas dépasser 4 294 967 296 lignes ; Toutefois, vous devez disposer de suffisamment de mémoire virtuelle sur votre ordinateur pour traiter votre demande.|  
|SQL_USE_BOOKMARKS|Prend en charge la définition de SQL_USE_BOOKMARKS à SQL_UB_ON et expose des signets de longueur fixe.|