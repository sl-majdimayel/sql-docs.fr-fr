---
title: Prise en charge de FOR XML pour les types de données définis par l’utilisateur (UDT) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6731d73830fe4f79525e05110920c6a3e6c2a1e
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509856"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>Prise en charge de FOR XML pour les types de données définis par l'utilisateur (UDT)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  FOR XML ne prend pas en charge les types de données définis par l'utilisateur (UDT) du Common Language Runtime (CLR).  
  
 Pour utiliser FOR XML avec des types de données CLR définis par l'utilisateur, assurez-vous que le type de données a une sérialisation XML et utilisez un cast explicite en XML dans la clause select FOR XML.  
  
## <a name="see-also"></a> Voir aussi  
 [Prise en charge FOR XML des différents types de données SQL Server](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
