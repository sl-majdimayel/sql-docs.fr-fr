---
title: Propriétés (SSAS tabulaire) de la table | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.tableprop.f1
ms.assetid: 16d3347b-7e43-4a6b-9956-fdd6ede092e6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5b9fbcb4aa054d261d47bea61edf1d1815cba27f
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52401032"
---
# <a name="table-properties-ssas-tabular"></a>Propriétés de table (SSAS Tabular)
  Cette rubrique décrit les propriétés de table d'un modèle tabulaire. Les propriétés décrites ici sont différentes de celles figurant dans la boîte de dialogue Modifier les propriétés de la table, lesquelles définissent les colonnes importées de la source.  
  
 Sections de cette rubrique :  
  
-   [Propriétés d’une table](#bkmk_properties)  
  
-   [Pour configurer les paramètres de propriété de table](#bkmk_config_prop)  
  
##  <a name="bkmk_properties"></a> Propriétés de la table  
 **De base**  
  
|Propriété|Paramètre par défaut|Description|  
|--------------|---------------------|-----------------|  
|**Nom de la connexion**|\<nom de la connexion >|Le nom de la connexion à la source de données de la table.<br /><br /> Pour modifier la connexion, cliquez sur le bouton.|  
|**Hidden**|False|Spécifie si la table est masquée dans les listes de champs de client de création de rapports.|  
|**Partitions**||Les partitions de la table ne peuvent pas être affichées dans la fenêtre **Propriétés** . Pour afficher, créer ou modifier des partitions, cliquez sur le bouton pour ouvrir le Gestionnaire de partition.|  
|**Données sources**||Les données sources de la table ne peuvent pas être affichées dans la fenêtre **Propriétés** . Pour afficher ou modifier les données sources, cliquez sur le bouton pour ouvrir la boîte de dialogue Modifier les propriétés de la table.|  
|**Description de la table**||Description textuelle de la table.<br /><br /> Dans [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], si un utilisateur positionne le curseur sur cette table dans la liste des champs, la description apparaît sous la forme d'une info-bulle.|  
|**Nom de la table**|\<nom convivial >|Spécifie le nom convivial de la table. Le nom de la table peut être spécifié lorsqu'une table est importée à l'aide de l'Assistant Importation de table ou à tout moment après l'importation. Le nom de la table dans le modèle peut être différent de la table associée à la source. Le nom convivial de la table s'affiche dans la liste de champs de l'application cliente de création de rapports ainsi que dans la base de données model dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
  
 **Propriétés de la création de rapports**  
  
 Pour obtenir des descriptions détaillées et des informations de configuration concernant les propriétés de génération de rapport, consultez [Propriétés de la génération de rapports Power View &#40;SSAS Tabulaire&#41;](properties-ssas-tabular.md).  
  
|Propriété|Paramètre par défaut|Description|  
|--------------|---------------------|-----------------|  
|**Ensemble de champs par défaut**|||  
|Comportement de la table|||  
  
###  <a name="bkmk_config_prop"></a> Pour configurer les paramètres de propriété de table  
  
1.  Dans le concepteur de modèles, dans la vue de données, cliquez sur une table (onglet) ou, dans la vue du diagramme, cliquez sur un en-tête de table.  
  
2.  Dans la fenêtre **Propriétés** , cliquez sur une propriété, puis tapez une valeur ou cliquez sur le bouton pour afficher des options de configuration supplémentaires.  
  
  
