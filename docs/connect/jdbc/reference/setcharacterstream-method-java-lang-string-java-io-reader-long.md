---
title: setCharacterStream, méthode (java.lang.String, java.io.Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 54fb2f13-f8d8-47b5-bec1-4a5af3e86a84
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3109c1ae9d751cb4eece04a7bc2dc241fdd84c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646527"
---
# <a name="setcharacterstream-method-javalangstring-javaioreader-long"></a>Méthode setCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet java.io.Reader spécifié, qui correspond au nombre de caractères spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setCharacterStream(java.lang.String parameterName  
                        java.io.Reader reader,  
                        long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *reader*  
  
 Objet Reader contenant les données Unicode.  
  
 *length*  
  
 Un **long** qui indique le nombre de caractères dans le flux.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setCharacterStream est spécifiée par la méthode setCharacterStream dans l’interface java.sql.CallableStatement.  
  
 Si la longueur du flux diffère de ce qui est spécifié dans le paramètre *length*, le pilote JDBC lève une exception lors de la mise à jour ou de l’insertion de la ligne.  
  
 Si la longueur du flux est inconnue, le paramètre *length* peut être défini sur -1 pour indiquer que le pilote doit accepter le flux, quelle que soit sa longueur. Avec sqljdbc4.jar, nous vous recommandons d’utiliser la méthode JDBC 4.0 [setCharacterStream, méthode (java.lang.String, java.io.Reader)](../../../connect/jdbc/reference/setcharacterstream-method-java-lang-string-java-io-reader.md) lorsque l’application veut mettre à jour la colonne à partir d’un flux de longueur inconnue.  
  
## <a name="see-also"></a> Voir aussi  
 [setCharacterStream, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
