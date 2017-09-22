---
title: "Migrer des données sensibles protégées par Always Encrypted | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/04/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Always Encrypted, bulk import
ms.assetid: b2ca08ed-a927-40fb-9059-09496752595e
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: da73d0d20404f513e22dcdf0340e24fe85dc3184
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="migrate-sensitive-data-protected-by-always-encrypted"></a>Migrer des données sensibles protégées par Always Encrypted
  Pour charger des données chiffrées sans effectuer de contrôle des métadonnées sur le serveur pendant les opérations de copie en bloc, créez l’utilisateur avec l’option **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** . Cette option est destinée à être utilisée par les outils hérités à partir de versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] (par exemple, bcp.exe) ou à l’aide de flux de travail ETL (Extract-Transform-Load) tiers qui ne peuvent pas utiliser Always Encrypted. Cela permet à un utilisateur de déplacer des données en toute sécurité d’un ensemble de tables contenant des colonnes chiffrées vers un autre ensemble de tables avec des colonnes chiffrées (dans la même base de données ou dans une autre).  
  
## <a name="the-allowencryptedvaluemodifications-option"></a>L’option ALLOW_ENCRYPTED_VALUE_MODIFICATIONS  
 [CREATE USER](https://msdn.microsoft.com/library/ms173463.aspx) et [ALTER USER](https://msdn.microsoft.com/library/ms176060.aspx) comprennent l’option ALLOW_ENCRYPTED_VALUE_MODIFICATIONS. Si cette option est définie sur ON (la valeur par défaut est OFF), elle supprime les contrôles des métadonnées de chiffrement sur le serveur dans les opérations de copie en bloc, ce qui permet à l’utilisateur de copier en bloc des données chiffrées entre des tables ou des bases de données, sans déchiffrage des données.  
  
## <a name="data-migration-scenarios"></a>Scénarios de migration de données  
 Le tableau suivant présente les paramètres appropriés recommandés pour plusieurs scénarios de migration.  
  
 ![always-encrypted-migration](../../../relational-databases/security/encryption/media/always-encrypted-migration.PNG "always-encrypted-migration")  
  
## <a name="bulk-loading-of-encrypted-data"></a>Chargement en masse de données chiffrées  
 Procédez comme suit pour charger des données chiffrées.  
  
1.  Définissez l’option sur ON pour l’utilisateur dans la base de données qui est la cible de l’opération de copie en bloc. Exemple :  
  
    ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = ON;  
    ```  
  
2.  Exécutez votre application de copie en bloc ou l’outil de connexion avec l’identité de cet utilisateur. (Si votre application utilise un pilote client compatible avec Always Encrypted, assurez-vous que la chaîne de connexion pour la source de données ne contient pas **column encryption setting=enabled** (paramètre de chiffrement de colonne = activé) de sorte que les données récupérées à partir des colonnes chiffrées restent chiffrées. Pour plus d’informations, consultez [Always Encrypted &#40;développement client&#41;](../../../relational-databases/security/encryption/always-encrypted-client-development.md).  
  
3.  Redéfinissez l’option ALLOW_ENCRYPTED_VALUE_MODIFICATIONS sur OFF. Exemple :  
  
    ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = OFF;  
    ```  
  
## <a name="potential-for-data-corruption"></a>Risque d’altération des données  
 Une utilisation incorrecte de cette option peut entraîner une altération des données. L’option **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** permet à l’utilisateur d’insérer des données quelconques dans des colonnes chiffrées de la base de données, notamment des données chiffrées avec des clés différentes, chiffrées de manière erronée ou non chiffrées. Si l’utilisateur copie accidentellement des données qui ne sont pas correctement chiffrées à l’aide du schéma de chiffrement (clé de chiffrement de colonne, algorithme, type de chiffrement) défini pour la colonne cible, vous ne serez pas en mesure de déchiffrer les données (les données sont endommagées). Cette option doit être utilisée avec précaution, car il risque d’endommager les données dans la base de données.  
  
 Le scénario suivant indique comment une importation de données incorrecte peut entraîner un endommagement des données :  
  
1.  L’option est définie sur ON pour un utilisateur.  
  
2.  L’utilisateur exécute l’application qui se connecte à la base de données. L’application utilise des API en bloc pour insérer des valeurs en texte brut dans des colonnes chiffrées. L’application attend un pilote client compatible avec Always Encrypted pour chiffrer les données lors de l’insertion. Cependant, l’application est mal configurée. Et elle utilise finalement un pilote qui ne prend pas en charge Always Encrypted, ou la chaîne de connexion ne contient pas **column encryption setting=enabled**.  
  
3.  L’application envoie des valeurs en texte en clair au serveur. Les contrôles des métadonnées de chiffrement étant désactivés dans le serveur pour l’utilisateur, le serveur permet l’insertion de données incorrectes (texte brut au lieu de texte correctement chiffré) dans une colonne chiffrée.  
  
4.  La même application (ou une autre) se connecte à la base de données à l’aide d’un pilote compatible Always Encrypted et avec la présence de **column encryption setting=enabled** dans la chaîne de connexion, puis récupère les données. L’application s’attend à ce que les données soient déchiffrées en toute transparence. Toutefois, le pilote n’est pas en mesure de déchiffrer les données, car il s’agit de textes chiffrés incorrects.  
  
## <a name="best-practice"></a>Meilleure pratique  
  
-   Utilisez les comptes d’utilisateur désignés pour les charges de travail de longue durée utilisant cette option.  
  
-   Pour des applications ou des outils de copie en bloc à exécution courte qui doivent déplacer des données chiffrées sans déchiffrage, définissez l’option ON immédiatement avant d’exécuter l’application, et redésactivez-la (OFF) immédiatement après l’exécution de l’opération.  
  
-   N’utilisez pas cette option pour développer de nouvelles applications. Utilisez plutôt un pilote client (comme ADO 4.6.1) qui offre une API permettant de supprimer les contrôles de métadonnées de chiffrement pour une seule session.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE USER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-user-transact-sql.md)   
 [ALTER USER &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-user-transact-sql.md)   
 [Always Encrypted &#40;moteur de base de données&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Assistant Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-wizard.md)   
 [Always Encrypted &#40;développement client&#41;](../../../relational-databases/security/encryption/always-encrypted-client-development.md)  
  
  
