---
title: "Modifier les propriétés de la Table | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- editTabProps
ms.assetid: 95ea72ba-8e40-4177-a963-0fb4d10c56e3
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5213e0c5757afd3a74c8b76f43bf1a2c88ced7e4
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="edit-the-table-properties"></a>Modifier les propriétés d'une table
  Cette boîte de dialogue permet de modifier des colonnes spécifiques de la table sélectionnée où les modifications sont capturées. Vous pouvez également modifier les informations du **Rôle de sécurité** et de l' **Instance de capture** .  
  
### <a name="to-edit-the-columns-to-include-in-the-cdc-instance"></a>Pour modifier les colonnes à inclure dans l'instance CDC.  
  
1.  Effectuez une des actions suivantes ou les deux :  
  
    -   Activez la case à cocher en regard des colonnes supplémentaires à inclure.  
  
    -   Désactivez la case à cocher en regard des colonnes que vous ne souhaitez plus inclure.  
  
### <a name="to-edit-the-security-role"></a>Pour modifier le rôle de sécurité  
  
1.  Tapez un nouveau nom ou modifiez le nom du rôle de sécurité dans le champ **Rôle de sécurité** .  
  
### <a name="to-create-a-new-capture-instance"></a>Pour créer une instance de capture  
  
1.  Dans le champ **Nom** de la section **Rôle de sécurité** entrez un nom pour l'instance de capture. Par défaut, le nom entré dans le champ est le nom de l’instance de capture actuelle avec **_NEW** ajouté à la fin du nom (par exemple, **ancienne_instance_NEW**).  
  
2.  Enregistrez l'instance de capture comme un des éléments suivants :  
  
    -   **Nouvelle instance de capture**: dans ce cas, une nouvelle instance de capture est enregistrée et l'ancienne instance de capture n'est pas supprimée.  
  
         **Remarque**: vous ne pouvez pas avoir plus de deux instances de capture par table. S'il existe déjà deux instances de capture, cette option n'est pas disponible.  
  
    -   **Remplacer l'instance de capture existante**: dans ce cas, l'instance de capture actuelle est supprimée et remplacée par l'instance de capture que vous avez créée. Si deux instances de capture sont définies pour cette table, vous devez en sélectionner une à remplacer.  
  
 **Remarque**: vous pouvez supprimer une instance de capture de la liste des tables sous l'onglet **Table** .  
  
 Une fois les informations entrées dans cette boîte de dialogue, cliquez sur **OK** pour accepter les modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment modifier les propriétés d’Instance de capture de données modifiées](../../integration-services/change-data-capture/how-to-edit-the-cdc-instance-properties.md)   
 [Apporter des modifications aux Tables sélectionnées pour capturer les modifications](../../integration-services/change-data-capture/make-changes-to-the-tables-selected-for-capturing-changes.md)  
  
  