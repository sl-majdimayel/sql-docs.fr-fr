---
title: Objets pris en charge par l’Assistant Génération de scripts | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32148fabf2e10e620f308bad63648e3e74f48e86
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202459"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>Objets pris en charge par l'Assistant Génération de scripts
  L'Assistant Générer et publier des scripts prend en charge un sous-ensemble des objets pris en charge par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="supported-objects"></a>Objets pris en charge  
 Le tableau suivant répertorie les objets qui peuvent être publiés et pris en charge par l'Assistant Générer et publier des scripts.  
  
||||||  
|-|-|-|-|-|  
|Rôle d'application|Rôle de base de données|schéma|Agrégat défini par l'utilisateur|Vue<sup>1</sup>|  
|Assembly|Contrainte DEFAULT|Procédure stockée<sup>1</sup>|Type de données défini par l'utilisateur|Collection de schémas XML|  
|Contrainte CHECK|Catalogue de texte intégral|Synonyme|Fonction définie par l'utilisateur||  
|Procédure stockée CLR (common language runtime)<sup>1</sup>|Index|Table de charge de travail|Table définie par l'utilisateur||  
|Fonction CLR définie par l'utilisateur|Règle|Utilisateur<sup>2</sup>|Type défini par l'utilisateur||  
  
 <sup>1</sup> publié sans chiffrement.  
  
 <sup>2</sup> tous les utilisateurs non-système qui existent dans la base de données sont publiés comme rôles.  
  
  
