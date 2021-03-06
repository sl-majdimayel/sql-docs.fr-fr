---
title: Paramètres d’informations de périphérique Word | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 494bf45f2aeb4fce5ed3b259665b1e7759879184
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56022340"
---
# <a name="word-device-information-settings"></a>Paramètres d'informations de périphérique Word
  Le tableau suivant répertorie les paramètres d'informations de périphérique qui permettent un rendu au format [!INCLUDE[ofprword](../includes/ofprword-md.md)] .  
  
|Paramètre|Value|  
|-------------|-----------|  
|`AutoFit`|`False` . L'ajustement automatique a la valeur `false` sur tous les tableaux Word.<br /><br /> `True` . L'ajustement automatique a la valeur `true` sur chaque tableau Word.<br /><br /> `Never` . Les valeurs d'ajustement automatique ne sont pas définies sur les tableaux Word et le comportement par défaut de Word est rétabli.<br /><br /> `Default` . L'ajustement automatique est défini sur les tableaux qui sont plus étroits que la zone de dessin physique (largeur de page physique, marges exclues) par page logique.|  
|`ExpandToggles`|Indique si tous les éléments pouvant être activés ou désactivés doivent être rendus dans leur état complètement développé. La valeur par défaut est `false`.|  
|`FixedPageWidth`|Indique si la largeur de page écrite dans le fichier DOC peut croître pour accommoder la largeur de la page la plus grande dans le corps du rapport. La valeur par défaut est `false`.|  
|**OmitHyperlinks**|Indique s'il faut omettre l'action de lien hypertexte sur tous les éléments dans lesquels elle est définie. La valeur par défaut est `false`|  
|`OmitDrillthroughs`|Indique s'il faut omettre l'action d'extraction sur tous les éléments dans lesquels elle est définie. La valeur par défaut est `false`|  
  
## <a name="see-also"></a>Voir aussi  
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
