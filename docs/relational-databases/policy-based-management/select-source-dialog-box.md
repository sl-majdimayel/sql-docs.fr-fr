---
title: "Sélectionner une source, boîte de dialogue | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.dmf.selectsource.f1
ms.assetid: d664c2e5-dd0c-4da8-b27d-aa4ee4fc0ffd
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a8ffe2ca7e33b741309b594c0a351825fee59b07
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="select-source-dialog-box"></a>Sélectionner une source, boîte de dialogue
  Utilisez cette boîte de dialogue pour sélectionner la source des stratégies à exécuter. Pour sélectionner un ou plusieurs fichiers XML qui contiennent des stratégies, sélectionnez **Fichiers**. Pour exécuter les stratégies détectées sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sélectionnez **Serveur**.  
  
 Vous pouvez ouvrir cette boîte de dialogue de plusieurs façons.  
  
 **Pour ouvrir cette boîte de dialogue**  
  
-   Dans Serveurs inscrits, cliquez avec le bouton droit sur **Groupes de serveurs locaux** ou sur un serveur répertorié sous **Groupes de serveurs locaux**ou encore sur un serveur répertorié sous **Serveurs de gestion centralisée**, puis sélectionnez **Évaluer les stratégies**. Dans la page **Sélection de la stratégie** de la boîte de dialogue **Évaluer les stratégies** , cliquez sur le bouton d’exploration (**...**).  
  
-   Dans l’Explorateur d’objets, développez **Gestion**, **Gestion de la stratégie**, cliquez avec le bouton droit sur **Stratégies**, puis sélectionnez **Importer une stratégie**. Dans la boîte de dialogue **Importer** , cliquez sur le bouton d’exploration (**...**).  
  
-   Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur, une base de données ou un objet de base de données, sélectionnez **Stratégies**, puis **Évaluer**. Dans la page **Sélection de la stratégie** de la boîte de dialogue **Évaluer les stratégies** , cliquez sur le bouton d’exploration (**...**).  
  
## <a name="options"></a>Options  
 **Fichiers**  
 Sélectionnez un ou plusieurs fichiers XML qui contiennent des stratégies.  
  
 **Serveur**  
 Vous permet de sélectionner un serveur qui contient les stratégies à exécuter.  
  
 **Type de serveur**  
 Seuls les serveurs du [!INCLUDE[ssDE](../../includes/ssde-md.md)] contiennent des stratégies. Cette zone est en lecture seule.  
  
 **Nom du serveur**  
 Sélectionnez l'instance de serveur à laquelle se connecter. Par défaut, la dernière instance de serveur à laquelle une connexion a été établie est affichée.  
  
 **Authentification**  
 Deux modes d'authentification sont disponibles lors de la connexion à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 **Mode d'authentification Windows (authentification Windows)**  
 Le mode d'authentification Windows permet à un utilisateur de se connecter au moyen d'un compte d'utilisateur Windows.  
  
 **Authentification SQL Server**  
 Quand un utilisateur se connecte avec un nom d’accès et un mot de passe spécifiés à partir d’une connexion non approuvée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réalise lui-même l’authentification en vérifiant si un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été défini et si le mot de passe spécifié correspond à celui enregistré précédemment. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne possède pas de compte de connexion, l'authentification échoue et un message d'erreur est envoyé à l'utilisateur.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, utilisez l'authentification Windows.  
  
 **Nom d'utilisateur**  
 Entrez le nom d'utilisateur avec lequel se connecter. Cette option est disponible uniquement si vous avez choisi la connexion avec l'authentification Windows.  
  
 **Connexion**  
 Entrez le nom d'accès avec lequel se connecter. Cette option est disponible uniquement si vous avez choisi d'établir une connexion à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Mot de passe**  
 Entrez le mot de passe utilisé avec la connexion. Ce mot de passe ne peut être modifié que si vous avez choisi la connexion avec l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Nœud Gestion de la stratégie &#40;Explorateur d’objets&#41;](../../relational-databases/policy-based-management/policy-management-node-object-explorer.md)   
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  