---
title: "Spécifier la clause TOP dans des requêtes (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TOP clause, queries
- percentage of rows returned [SQL Server]
- number of rows
- search conditions [SQL Server], TOP clause
- restricting rows returned
- search criteria [SQL Server], limiting rows returned
- inspecting portion of results
- limiting rows returned
- search criteria [SQL Server], TOP clause
ms.assetid: ba7d7c10-9bb3-4d9b-90b0-5fa94ecae59b
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fd92acc6387cf67dd4b2a75b83e0e69b97a2ed3e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/18/2017

---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a>Spécifier la clause TOP dans des requêtes (Visual Database Tools)
La clause TOP retourne uniquement les *n* lignes ou *n premiers pourcents* des lignes d’une requête. La clause TOP peut être utile si vous souhaitez inspecter une partie de vos résultats afin de déterminer si votre requête se comporte de la manière escomptée, sans devoir utiliser les ressources nécessaires pour retourner tous les résultats de la requête.  
  
### <a name="to-specify-the-top-clause-in-queries"></a>Pour spécifier la clause TOP dans des requêtes  
  
1.  Ouvrez une requête dans l'Explorateur de solutions ou créez-en une nouvelle.  
  
2.  Dans le menu **Affichage** , cliquez sur **Fenêtre Propriétés**.  
  
3.  Dans la **Fenêtre Propriétés**, recherchez et développez la propriété **Spécification Top** .  
  
4.  Cliquez sur la propriété enfant **(Haut)** et affectez-lui la valeur **Oui**.  
  
5.  Dans la propriété enfant **Expression** , tapez une expression qui a un résultat numérique (par exemple, « 10 » ou « 2*5 »).  
  
6.  Cliquez sur la propriété enfant **Pourcentage** et indiquez si la propriété **Expression** doit être traitée comme un pourcentage de toutes les lignes retournées (Oui) ou comme le nombre absolu de lignes retournées (Non).  
  
7.  Si votre requête utilise la clause ORDER BY, cliquez sur la propriété enfant **With Ties** et sélectionnez **Oui** pour afficher toutes les lignes d’un groupe si seule une partie du groupe est incluse ou **Non** pour les tronquer.  
  
Au fur et à mesure que vous exécutez la procédure précédente, remarquez que la clause TOP, affichée dans le volet SQL, se modifie pour refléter les valeurs actuelles des propriétés.  
  
> [!NOTE]  
> Vous pouvez également modifier les valeurs des propriétés enfants de la propriété **Spécification Top** en modifiant la clause TOP dans le volet SQL.  
  
## <a name="see-also"></a>Voir aussi  
[Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Propriétés de la requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-properties-visual-database-tools.md)  
  
