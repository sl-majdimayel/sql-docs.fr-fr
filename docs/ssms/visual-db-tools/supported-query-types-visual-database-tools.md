---
title: Types de requêtes pris en charge (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Delete query
- queries [SQL Server], types
- Update query
- Query Designer [SQL Server], query types
- Criteria pane
- Insert Values query
- Select query
- Make Table query
- Insert Results query
- Diagram pane [Visual Database Tools]
- View Designer, query types
ms.assetid: 72b9116c-c128-4078-a78d-257a2955a3f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 21e4585a5b41fe14e68d7d7e5ca38f8da7060a8b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52505570"
---
# <a name="supported-query-types-visual-database-tools"></a>Types de requêtes pris en charge (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Voici les types de requêtes pouvant être créés dans les volets Schéma et Critères (volets graphiques) du [Concepteur de requêtes et de vues](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md):  
  
-   **Requête Select** Extrait des données d’une ou de plusieurs tables ou vues. Ce type de requête crée une instruction SQL SELECT.  
  
-   **Insert Results** Créé des lignes d’une table dans une autre, ou dans la même table en tant que nouvelles lignes. Ce type de requête crée une instruction SQL INSERT INTO...SELECT.  
  
-   **Insert Values** Crée une ligne et insère des valeurs dans des colonnes spécifiées. Ce type de requête crée une instruction SQL INSERT INTO...VALUES.  
  
-   **Requête Update** Modifie les valeurs de colonnes individuelles dans une ou plusieurs lignes existant dans une table. Ce type de requête crée une instruction SQL UPDATE...SET.  
  
-   **Requête Delete** Supprime une ou plusieurs lignes d’une table. Ce type de requête crée une instruction SQL DELETE.  
  
    > [!NOTE]  
    > Une requête Delete supprime de la table des lignes entières. Pour supprimer des valeurs dans des colonnes de données individuelles, utilisez une requête Update.  
  
-   **Requête Make Table** Copie les résultats d’une requête dans une nouvelle table. Ce type de requête crée une instruction SQL DELETE...INTO.  
  
Pour créer des requêtes, vous pouvez utiliser les volets graphiques, mais aussi entrer n'importe quelle instruction SQL dans le volet SQL, par exemple pour créer une requête Union.  
  
Si les instructions SQL que vous utilisez pour créer la requête ne peuvent pas être représentées dans les volets graphiques, le Concepteur de requêtes et de vues estompe ces volets pour indiquer qu'ils ne reflètent pas la requête en cours de création. Cependant, les volets estompés restent actifs et, dans de nombreux cas, il est possible d'apporter des modifications à la requête dans ces volets. Si les modifications que vous apportez donnent lieu à une requête que les volets graphiques peuvent représenter, ces derniers ne sont plus estompés.  
  
## <a name="see-also"></a> Voir aussi  
[Rubriques de procédures relatives à la conception de requêtes et de vues (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Types de requêtes (Visual Database Tools)](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
  
