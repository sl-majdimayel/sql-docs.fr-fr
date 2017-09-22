---
title: Les curseurs statiques ODBC | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ODBC], static
- static cursors [ODBC]
ms.assetid: 28cb324c-e1c3-4b5c-bc3e-54df87037317
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aaddef08bfea9e1a1820727743e5212557d823d4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-static-cursors"></a>Curseurs statiques ODBC
Un curseur statique est un dans lequel le jeu de résultats semble être statique. Généralement, il ne détecte pas les modifications qui ont été apportées à l’appartenance, l’ordre ou les valeurs du jeu de résultats après l’ouverture du curseur. Par exemple, un curseur statique extrait une ligne et une autre application, puis met à jour cette ligne. Si le curseur statique réextrait la ligne, les valeurs sont identiques, malgré les modifications apportées par l’autre application.  
  
 Les curseurs statiques peuvent détecter leurs propres mises à jour, suppressions et insertions, bien qu’ils ne sont pas nécessaires pour cela. Indique si un curseur statique particulier détecte ces modifications est signalé via l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**. Les curseurs statiques détectent jamais les autres mises à jour, supprime et insère.  
  
 Le tableau d’état de ligne spécifié par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR peut contenir SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO ou SQL_ROW_ERROR pour n’importe quelle ligne. Elle retourne SQL_ROW_UPDATED, SQL_ROW_DELETED ou SQL_ROW_ADDED pour les lignes mises à jour, supprimées ou insérées par le curseur, en supposant que le curseur peut détecter ces modifications.  
  
 Les curseurs statiques sont généralement implémentées en verrouillant les lignes du jeu de résultats ou en effectuant une copie, ou instantané, du résultat définies. Bien que le verrouillage de lignes est relativement facile à faire, il a l’inconvénient de ce qui réduit considérablement la concurrence. Copie permet une plus grande concurrence et permet le curseur effectuer le suivi de ses propres mises à jour, suppressions et insère en modifiant la copie. Toutefois, une copie est plus onéreuse à effectuer et les données sous-jacentes peuvent diverger que ces données sont modifiées par d’autres.