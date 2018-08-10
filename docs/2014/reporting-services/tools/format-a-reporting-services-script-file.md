---
title: Mettre en forme un fichier de scripts Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], formats
- formats [Reporting Services], script files
ms.assetid: 85a207dd-4e0f-4d40-a41e-0c75f65d719c
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f54fb06c849655b8fbb7c60fd2b20117dff610f7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276045"
---
# <a name="format-a-reporting-services-script-file"></a>Formater un fichier de script Reporting Services
  Un script [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est un fichier de code [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET, écrit par rapport au proxy développé sur le service WSDL (Web Service Description Langage), qui définit l'API SOAP Reporting Services. Un fichier de script est stocké comme fichier texte Unicode ou UTF-8 avec l'extension .rss.  
  
 Le fichier de script agit comme un module [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] et peut contenir des procédures définies par l'utilisateur et des variables au niveau du module. Pour que le fichier de script exécute avec succès, il doit contenir une procédure Main. La procédure Main est la première procédure accédée lorsque votre fichier de script s'exécute. Cette procédure Main représente l'emplacement où vous pouvez ajouter vos opérations de service Web et exécuter vos sous-procédures définies par l'utilisateur. L'exemple de code suivant crée une procédure Main :  
  
```  
Public Sub Main()  
    ' Your code goes here.  
End Sub  
```  
  
 L’environnement de script se connecte automatiquement au serveur de rapports, crée la classe proxy web et génère une variable de référence (*rs*) à l’objet proxy de service web. Les instructions individuelles que vous créez ont uniquement besoin de faire référence à la variable de niveau module *rs* pour effectuer les opérations de service web qui sont disponibles dans la bibliothèque de service web. Le code [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] suivant appelle la méthode <xref:ReportService2010.ReportingService2010.ListChildren%2A> du service web à partir d’un fichier de script :  
  
```  
Public Sub Main()  
    Dim items() As CatalogItem  
    items = rs.ListChildren("/", True)  
  
    Dim item As CatalogItem  
    For Each item In items  
        Console.WriteLine(item.Name)  
    Next item  
End Sub   
```  
  
> [!IMPORTANT]  
>  Les informations d'identification de l'utilisateur sont gérées par l'environnement de script et transmises à travers les arguments d'invite de commandes au moyen de RS.exe. Bien que vous puissiez utiliser la variable *rs* pour définir l’authentification du service web, nous vous recommandons d’utiliser l’environnement de script. Vous n'avez pas besoin d'authentifier le service Web dans le fichier de script lui-même. Pour plus d’informations sur l’authentification de l’environnement de script, consultez [utilitaire RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md).  
  
 Vous ne déclarez pas d'espaces de noms dans le fichier de script. Grâce à l’environnement de script, plusieurs espaces de noms [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] sont disponibles : **System.Web.Services**, **System.Web.Services.Protocols**, **System.Xml**et **System.IO**.  
  
 Pour des exemples de scripts, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)(Exemples SQL Server Reporting Services).  
  
## <a name="see-also"></a>Voir aussi  
 [Service web Report Server](../report-server-web-service/report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../technical-reference-ssrs.md)   
 [Utilitaire RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md)  
  
  