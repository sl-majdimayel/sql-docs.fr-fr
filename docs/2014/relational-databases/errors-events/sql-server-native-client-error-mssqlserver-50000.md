---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 863f2caf2afa97b7550759dd5ae84ff47572a1bd
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431318"
---
# <a name="mssqlserver50000"></a>MSSQLSERVER_50000
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|Version du produit|11.0|  
|ID d'événement|50000|  
|Source de l'événement|SETUP|  
|Composant|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|Nom symbolique||  
|Texte du message|Erreur réseau lors de la tentative de lecture du fichier : '%. * ls'.|  
  
## <a name="explanation"></a>Explication  
 Tentative d'installation (ou de mise à jour) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sur un ordinateur où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est déjà installé, et où l'installation existante provenait d'un fichier MSI qui a été renommé de sqlncli.msi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, désinstallez la version existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Pour empêcher cette erreur, n'installez pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client à partir d'un fichier MSI qui n'est pas nommé sqlncli.msi.  
  
## <a name="internal-only"></a>Interne uniquement  
  