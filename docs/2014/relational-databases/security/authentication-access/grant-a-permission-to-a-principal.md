---
title: Accorder une autorisation à un principal | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Grant permission to a principal
ms.assetid: 4107389d-05b6-4aa3-9fa8-95b40cdf05dc
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 9b0ff18a9b3c6ff338a2b827b91ff20bbc7b2ce9
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54134919"
---
# <a name="grant-a-permission-to-a-principal"></a>Accorder une autorisation à un principal
  Cette rubrique explique comment accorder une autorisation à un principal dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour accorder une autorisation à un principal, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Tenez compte des recommandations suivantes qui peuvent faciliter la gestion des autorisations.  
  
-   Accorder des autorisations à des rôles plutôt qu'à des connexions ou des utilisateurs. Lorsqu'un individu est remplacé par un autre, supprimez celui qui quitte le rôle et ajoutez le nouvel arrivant au rôle. Les nombreuses autorisations qui peuvent être associées au rôle seront automatiquement disponibles pour ce dernier. Si, dans une entreprise, plusieurs personnes ont besoin des mêmes autorisations, l'ajout de chacune d'entre elles au rôle leur accordera les mêmes autorisations.  
  
-   Configurez des éléments sécurisables similaires (tables, vues et procédures) qui seront détenus par un schéma, puis octroyez des autorisations au schéma. Par exemple, le schéma de registre du personnel peut détenir plusieurs tables, vues et procédures stockées. En accordant l'accès au schéma, toutes les autorisations nécessaires pour effectuer la fonction de gestion du personnel peuvent être accordées en même temps. Pour en savoir plus sur les éléments sécurisables auxquels accorder des autorisations, consultez [Securables](../securables.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Le fournisseur d'autorisations (ou le principal spécifié avec l'option AS) doit posséder l'autorisation elle-même avec l'option GRANT OPTION ou une autorisation plus élevée qui implique l'autorisation accordée. Les membres du rôle serveur fixe **sysadmin** peuvent accorder toutes les autorisations.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-grant-permission-to-a-principal"></a>Pour accorder une autorisation à un principal  
  
1.  Dans l'Explorateur d'objets, développez la base de données qui contient l'objet auquel vous souhaitez octroyer des autorisations.  
  
    > [!NOTE]  
    >  Ces étapes traitent spécifiquement de l'octroi d'autorisations à une procédure stockée, mais vous pouvez utiliser des étapes similaires pour ajouter des autorisations aux tables, aux vues, aux fonctions et aux assemblys, ainsi qu'à d'autres éléments sécurisables. Pour plus d’informations, consultez [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).  
  
2.  Développez le dossier **Programmabilité** .  
  
3.  Développez le dossier **Procédures stockées** .  
  
4.  Cliquez avec le bouton droit sur une procédure stockée, puis sélectionnez **Propriétés**.  
  
5.  Dans le **propriétés de la procédure stockée -**_nom_procédure_stockée_ boîte de dialogue, sous sélectionner une page, sélectionnez **autorisations**. Utilisez cette page pour ajouter des utilisateurs ou des rôles à la procédure stockée et spécifier les autorisations dont disposeront ces utilisateurs ou rôles.  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-grant-permission-to-a-principal"></a>Pour accorder une autorisation à un principal  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Grants EXECUTE permission on stored procedure HumanResources.uspUpdateEmployeeHireInfo to an application role called Recruiting11.   
    USE AdventureWorks2012;  
    GO  
    GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
        TO Recruiting11;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) et [Octroi d’autorisations d’objet &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Principaux &#40;moteur de base de données&#41;](principals-database-engine.md)  
  
  
