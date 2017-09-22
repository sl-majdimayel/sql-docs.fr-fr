---
title: Le fournisseur OLE DB pour la publication Internet | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
ms.assetid: 4869aafa-7401-4ce1-93ce-45406a60274f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c19f0a93a5f7f685d7cd8dcdf6d916ae3955cff8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="the-ole-db-provider-for-internet-publishing"></a>Le fournisseur OLE DB pour la publication Internet
ADO [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) et [flux](../../../ado/reference/ado-api/stream-object-ado.md) objets peuvent être utilisés avec le fournisseur Microsoft OLE DB pour la publication Internet (fournisseur de publication Internet) pour accéder à et manipuler les ressources, telles que les dossiers ou fichiers Web pris en charge par Microsoft FrontPage. Avec ADO, vous pouvez spécifier la source d’un **enregistrement**, **flux**, ou [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) être une URL. Vous pouvez ensuite télécharger, télécharger, déplacer, copier et supprimer des ressources ou manipuler directement des propriétés de ressource.  
  
 Par exemple le code qui utilise **enregistrements** et **flux** avec le fournisseur de publication Internet, consultez le [scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md).  
  
 Le fournisseur de publication Internet est installé avec Microsoft Windows 2000. Les versions antérieures du fournisseur de publication Internet sont également disponibles avec Microsoft Office 2000 et Microsoft Internet Explorer 5.0.  
  
 Il existe trois façons de connecter ADO au fournisseur de publication Internet :  
  
-   Spécifiez « URL = » dans la chaîne de connexion. Exemple :  
  
    ```  
    objConn.Open "URL=http://servername"  
    ```  
  
-   Spécifiez Msdaipp.dso pour le *fournisseur* mot clé de la chaîne de connexion. Exemple :  
  
    ```  
    objConn.Open "provider=MSDAIPP.DSO;data source=http://servername"  
    ```  
  
-   Spécifiez Msdaipp.dso pour le [fournisseur](../../../ado/reference/ado-api/provider-property-ado.md) propriété de la [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet. Exemple :  
  
    ```  
    objConn.Provider = "MSDAIPP.DSO"  
    objConn.Open "http://servername"  
    ```  
  
> [!NOTE]
>  Si Msdaipp.dso est explicitement spécifié comme valeur du fournisseur, à l’aide de la *fournisseur* mot clé de chaîne de connexion ou le **fournisseur** propriété, vous ne pouvez pas utiliser « URL = » dans la chaîne de connexion. Si vous le faites, une erreur se produit. Au lieu de cela, spécifiez simplement l’URL comme indiqué précédemment.  
  
 Pour plus d’informations sur le fournisseur de publication Internet, consultez [fournisseur Microsoft OLE DB pour Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), ou la documentation fournie avec l’application source avec laquelle le fournisseur OLE DB pour Publication Internet a été installé : Windows 2000, Office 2000 ou Internet Explorer 5.0.