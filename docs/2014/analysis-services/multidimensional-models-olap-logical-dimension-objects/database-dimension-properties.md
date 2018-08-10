---
title: Propriétés de la Dimension de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6e9b86509f0b4a5ab87102c43838cfa1b18376a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194329"
---
# <a name="database-dimension-properties"></a>Propriétés de dimension d'une base de données
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les caractéristiques d’une dimension sont définis par les métadonnées pour la dimension, selon les paramètres de diverses propriétés de dimension et des attributs ou des hiérarchies qui sont contenues par la dimension. Le tableau ci-dessous décrit les propriétés des dimensions dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Propriété|Description|  
|--------------|-----------------|  
|`AttributeAllMemberName`|Spécifie le nom du membre Tous pour les attributs d'une dimension.|  
|`Collation`|Détermine le classement utilisé par la dimension.|  
|`CurrentStorageMode`|Contient le mode de stockage en cours pour la dimension.|  
|`DependsOnDimension`|Contient l'identificateur d'une autre dimension dont la dimension dépend (le cas échéant).|  
|`Description`|Contient la description de la dimension.|  
|`ErrorConfiguration`|Paramètres configurables de gestion d'erreur pour la gestion des clés dupliquées, des clés inconnues, des limites d'erreur, des actions en cas de détection d'erreur, du fichier journal des erreurs et pour la gestion des clés NULL.|  
|`ID`|Contient l'identificateur unique (ID) de la dimension.|  
|`Language`|Spécifie la langue par défaut de la dimension.|  
|`MdxMissingMemberMode`|Détermine comment les membres manquants sont gérés pour les instructions MDX (Multidimensional Expressions).|  
|`MiningModelID`|Contient l'identificateur du modèle d'exploration de données à laquelle la dimension d'exploration de données est associée. Cette propriété est applicable seulement si la dimension est une dimension de modèle d'exploration de données.|  
|`Name`|Spécifie le nom de la dimension.|  
|`ProactiveCaching`|Définit les paramètres de cache pro-actif pour la dimension.|  
|`ProcessingGroup`|Spécifie le groupe de traitement. Les valeurs sont ByAttribute ou ByTable. Valeur par défaut est `ByAttribute`.|  
|`ProcessingMode`|Indique si [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] doit créer les index et effectuer l'agrégation lors du traitement ou après celui-ci.|  
|`ProcessingPriority`|Détermine la priorité de traitement de la dimension lors des opérations en arrière-plan, notamment le traitement en différé des agrégations, de l'indexation ou du clustering.|  
|`Source`|Identifie la vue de source de données à laquelle la dimension est liée.|  
|`StorageMode`|Détermine le mode de stockage pour la dimension.|  
|`Type`|Spécifie le type de la dimension.|  
|`UnknownMember`|Indique si le membre inconnu est visible.|  
|`UnknownMemberName`|Spécifie la légende (dans la langue par défaut de la dimension) pour le membre inconnu de la dimension.|  
|`WriteEnabled`|Indique si l'écriture différée de dimension est disponible (soumise à des autorisations de sécurité).|  
  
> [!NOTE]  
>  Pour plus d’informations sur la définition des valeurs pour les propriétés ErrorConfiguration et UnknownMember lorsque vous travaillez avec des valeurs null et d’autres problèmes d’intégrité des données, consultez [gestion des problèmes d’intégrité des données dans Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](attributes-and-attribute-hierarchies.md)   
 [Hiérarchies utilisateur](user-hierarchies.md)   
 [Relations de dimension](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  