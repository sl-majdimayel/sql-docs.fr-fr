---
title: Modifier les propriétés d’une table | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- editTabProps
ms.assetid: 95ea72ba-8e40-4177-a963-0fb4d10c56e3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 618a155390d8719e639d0e12d241b2f824e5375d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58390930"
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
  
    -   **Nouvelle Instance de Capture**: Dans ce cas une nouvelle instance de capture est enregistrée et l’ancienne instance de capture n’est pas supprimée.  
  
         **Remarque**: Vous pouvez avoir pas plus de deux instances de capture par table. S'il existe déjà deux instances de capture, cette option n'est pas disponible.  
  
    -   **Remplacez**: Dans ce cas, l’instance de capture actuelle est supprimée et remplacée par l’instance de capture que vous avez créé. Si deux instances de capture sont définies pour cette table, vous devez en sélectionner une à remplacer.  
  
 **Remarque**: Vous pouvez supprimer une instance de capture à partir de la liste des tables dans le **Table** onglet.  
  
 Une fois les informations entrées dans cette boîte de dialogue, cliquez sur **OK** pour accepter les modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : modifier les propriétés d'une instance de capture de données modifiées](how-to-edit-the-cdc-instance-properties.md)   
 [Apporter des modifications aux tables sélectionnées pour capturer les modifications](make-changes-to-the-tables-selected-for-capturing-changes.md)  
  
  
