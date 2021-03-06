---
title: Guide pratique pour modifier les propriétés d’une instance CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7a6c719a-3735-43b7-b3ab-dfadd325eca2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 42cc80b22f5daae0deeaa355b4c8d23d2c888455
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58289845"
---
# <a name="how-to-edit-the-cdc-instance-properties"></a>Procédure : modifier les propriétés d'une instance de capture de données modifiées
  Cette procédure décrit comment utiliser la console du concepteur CDC pour modifier les propriétés de configuration d'une instance de capture de données modifiées.  
  
### <a name="to-edit-the-cdc-instance-configuration-properties"></a>Pour modifier les propriétés de configuration de l'instance de capture de données modifiées  
  
1.  Dans le menu **Démarrer** , sélectionnez **Console du concepteur de capture de données modifiées**.  
  
2.  Dans le volet gauche, développez **Capture de données modifiées** , puis le service qui contient l'instance avec les propriétés à modifier.  
  
3.  Sélectionnez le nom de l'instance où vous souhaitez modifier les propriétés.  
  
4.  Dans le volet Actions à droite de la console du concepteur CDC, cliquez sur **Propriétés**.  
  
     Vous pouvez aussi cliquer avec le bouton droit sur l’instance dont vous voulez modifier les propriétés et cliquer sur **Propriétés**.  
  
5.  Dans l'éditeur de propriétés, modifiez les propriétés dans les onglets suivants :  
  
    -   **Oracle** : Utilisez l'onglet **Oracle** de l'éditeur de propriétés pour apporter des modifications à la description que vous avez fournie dans la page Créer une base de données CDC de l'Assistant Nouvelle instance et pour apporter des modifications aux informations de connexion à la base de données d'exploration de données de journaux Oracle.  
  
         Pour plus d'informations sur ce que vous pouvez modifier dans cet onglet, consultez [Edit the Oracle Database Properties](../../integration-services/change-data-capture/edit-the-oracle-database-properties.md).  
  
    -   **Tables** : Utilisez l'onglet **Tables** pour apporter des modifications aux tables et aux colonnes sélectionnées dans la base de données source Oracle.  
  
         Pour plus d'informations sur ce que vous pouvez modifier dans cet onglet, consultez [Edit Tables](../../integration-services/change-data-capture/edit-tables.md).  
  
    -   **Scripts** : L’onglet **Scripts** permet d’exécuter ou de réexécuter un script sur la base de données source Oracle qui configure une journalisation supplémentaire.  
  
         Pour plus d'informations sur ce que vous pouvez faire dans cet onglet, consultez [Review and Generate Supplemental Logging Scripts](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md).  
  
    -   **Avancé** : Utilisez l'onglet **Avancé** pour ajouter des propriétés spéciales à l'instance de capture de données modifiées.  
  
         Pour plus d'informations sur ce que vous pouvez faire dans cet onglet, consultez [Edit the Advanced Properties](../../integration-services/change-data-capture/edit-the-advanced-properties.md).  
  
  
