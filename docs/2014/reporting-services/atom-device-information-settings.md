---
title: Paramètres d’informations de périphérique ATOM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b20d11ac8a07632e9105c3963d19f7936832aec4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020644"
---
# <a name="atom-device-information-settings"></a>Paramètres d'informations de périphérique ATOM
  Les paramètres d'informations de périphériques pour l'extension de rendu Atom prennent en charge la soumission du nom d'un flux Atom et de l'encodage de caractères à utiliser.  
  
 Le tableau suivant répertorie les paramètres des informations de périphériques pour le rendu dans un document de service de données.  
  
|Paramètre|Value|  
|-------------|-----------|  
|`DataFeed`|Si spécifié, restitue le flux Atom correspondant au nom de flux fourni dans ce paramètre. Dans le cas contraire, restitue le document de service Atom pour le rapport. Identificateur unique de la source de données générée automatiquement. Cette valeur est utilisée en interne et vous ne devez pas le modifier.|  
|**Encodage**|Nom IANA (Internet Assigned Numbers Authority) d'un encodage de caractères pris en charge par le .NET Framework. La valeur par défaut est `UTF-8`. Les exemples d'autres valeurs incluent ASCII, UTF-7 et UTF-16.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
