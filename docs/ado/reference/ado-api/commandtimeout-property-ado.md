---
title: CommandTimeout, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5bb74384e043130ccfe4c3399b363b25d40737c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632157"
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout, propriété (ADO)
Indique le délai d’attente lors de l’exécution d’une commande avant d’abandonner la tentative et de générer une erreur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Long** valeur qui indique, en secondes, la durée d’attente d’une commande à exécuter. Valeur par défaut est 30.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **CommandTimeout** propriété sur un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet ou [commande](../../../ado/reference/ado-api/command-object-ado.md) objet pour permettre l’annulation d’une [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) (méthode) Appelez, en raison des délais de réseau du trafic ou serveur une utilisation intensive. Si l’intervalle défini le **CommandTimeout** propriété s’écoule avant que la commande a été exécutée, une erreur se produit et ADO annule la commande. Si vous définissez la propriété sur zéro, ADO attend indéfiniment que l’exécution est terminée. Assurez-vous que la fournisseur et source de données à laquelle vous écrivez prise en charge du code la **CommandTimeout** fonctionnalité.  
  
 Le **CommandTimeout** définition sur un **connexion** objet n’a aucun effet le **CommandTimeout** définition sur un **commande** de l’objet sur le même **connexion**; autrement dit, le **commande** l’objet **CommandTimeout** propriété n’hérite pas de la valeur de la **connexion** l’objet **CommandTimeout** valeur.  
  
 Sur un **connexion** objet, le **CommandTimeout** propriété reste en lecture/écriture après le **connexion** est ouvert.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, taille et Direction, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout, propriété (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
