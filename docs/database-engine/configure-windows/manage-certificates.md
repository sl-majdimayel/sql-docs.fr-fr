---
title: Gestion des certificats (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/16/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 88e35bc2589f30a0fa3d6b707d66aa25325dc89e
ms.sourcegitcommit: b51edbe07a0a2fdb5f74b5874771042400baf919
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55088989"
---
# <a name="certificate-management-sql-server-configuration-manager"></a>Gestion des certificats (Gestionnaire de configuration SQL Server)

Cette rubrique décrit comment déployer et gérer des certificats sur votre topologie de groupe de disponibilité ou cluster de basculement SQL Server Always On.

Les certificats SSL/TLS sont largement utilisés pour sécuriser l’accès à SQL Server. Avec les versions antérieures de SQL Server, les organisations avec de grandes infrastructures SQL Server devaient consacrer d’importants efforts à la gestion de leur infrastructure de certificats SQL Server, souvent en développant des scripts et en exécutant des commandes manuelles. Avec SQL Server 2019, la gestion des certificats est intégrée au Gestionnaire de configuration SQL Server, ce qui simplifie les tâches courantes telles que les suivantes : 

* Affichage et validation des certificats installés dans une instance SQL Server. 
* Identification des certificats arrivant à expiration. 
* Déploiement de certificats sur plusieurs machines de groupes de disponibilité à partir du nœud contenant le réplica principal. 
* Déploiement de certificats sur plusieurs machines participant à une instance de cluster de basculement à partir du nœud actif.

> [!NOTE]
> Vous pouvez utiliser la gestion des certificats dans le Gestionnaire de configuration SQL Server avec des versions inférieures de SQL Server, à partir de SQL Server 2008.

##  <a name="provision-single-server-cert"></a> Pour installer un certificat pour une seule instance SQL Server  
  
1. Dans le Gestionnaire de configuration SQL Server, dans le volet de la console, développez **Configuration du réseau SQL Server**.  
  
2. Cliquez avec le bouton droit sur **Protocoles pour** *&lt;nom de l’instance&gt;*, puis sélectionnez **Propriétés**.  
  
3. Choisissez l’onglet **Certificat**, puis sélectionnez **Importer**.  
  
4. Sélectionnez **Parcourir**, puis le fichier de certificat.  
  
5. Sélectionnez **Suivant** pour valider le certificat. Si aucune erreur ne se produit, sélectionnez **Suivant** pour importer le certificat dans l’instance locale.  
  
 
##  <a name="provision-failover-cluster-cert"></a> Pour installer un certificat dans une configuration de cluster de basculement  
  
1. Dans le Gestionnaire de configuration SQL Server, dans le volet de la console, développez **Configuration du réseau SQL Server**.
  
2. Cliquez avec le bouton droit sur **Protocoles pour** *&lt;nom de l’instance&gt;*, puis choisissez **Propriétés**. 

3. Choisissez l’onglet **Certificat**, puis sélectionnez **Importer**.

4. Sélectionnez le type de certificat et indiquez si vous voulez procéder à l’importation uniquement pour le nœud actuel ou pour chaque nœud de cluster.

5. Dans le cas d’une installation pour un nœud unique, choisissez **Parcourir**, puis le fichier de certificat. Passez ensuite à l’étape 8.

6. Dans le cas de l’installation d’un certificat pour chaque nœud, sélectionnez **Suivant** pour lister les nœuds propriétaires possibles. Les propriétaires possibles pour l’instance de cluster de basculement SQL Server actuelle sont présélectionnés.

7. Choisissez **Suivant** pour sélectionner le certificat à importer.

8. Entrez le mot de passe quand vous y êtes invité. Recherchez les éventuels avertissements ou erreurs après la validation.

9. Sélectionnez **Suivant** pour importer les certificats sélectionnés.

> [!NOTE]
> Effectuez ces étapes dans le nœud actif de l’instance de cluster de basculement SQL Server. L’utilisateur doit disposer des autorisations d’administrateur sur tous les nœuds de cluster.

##  <a name="provision-availability-group-cert"></a>Pour installer un certificat dans une configuration de groupe de disponibilité  
  
1. Dans le Gestionnaire de configuration SQL Server, dans le volet de la console, développez **Configuration du réseau SQL Server**.
  
2. Cliquez avec le bouton droit sur **Protocoles pour** *&lt;nom de l’instance&gt;*, puis sélectionnez **Propriétés**.  
  
3. Choisissez l’onglet **Certificat**, puis sélectionnez **Importer**.  
  
4. Choisissez le type de certificat et sélectionnez **Suivant** pour sélectionner dans la liste des groupes de disponibilité connus.  

5. Sélectionnez **Suivant** pour choisir des certificats pour chaque nœud de réplica. Les certificats doivent avoir un nom de fichier qui correspond au nom NetBIOS des nœuds.

6. Sélectionnez **Suivant** pour importer le certificat sur chaque nœud.


> [!NOTE]
> Effectuez ces étapes à partir du nœud contenant le réplica principal du groupe de disponibilité. L’utilisateur doit disposer des autorisations d’administrateur sur tous les nœuds de cluster.

