---
title: Relire jusqu'à un curseur (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5956e4872695f796ac0367ad45f90cbc20a91e1e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732147"
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a>Relire jusqu'à un curseur (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique indique comment relire des fichiers ou des tables de trace suspendus lorsqu'un curseur est atteint à l'aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. La suspension de traces sur des curseurs simplifie le débogage car vous pouvez ainsi fractionner la relecture de longs scripts de trace en courts segments se prêtant à l'analyse incrémentielle.  
  
### <a name="to-replay-to-the-cursor"></a>Pour relire jusqu'au curseur  
  
1.  Ouvrez le fichier de trace ou la table de trace à relire. Pour plus d’informations, consultez [Ouvrir un fichier de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) ou l'Assistant Paramétrage du [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Vérifiez que le fichier de trace ou la table de trace que vous ouvrez contient les classes d'événements nécessaires pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  Dans la fenêtre de trace, cliquez sur un événement.  
  
3.  Dans le menu **Relire** , cliquez sur **Exécuter jusqu’au curseur**, puis connectez-vous au serveur où vous souhaitez relire la trace.  
  
4.  Dans la boîte de dialogue **Configuration de relecture** , vérifiez les paramètres, puis cliquez sur **OK**.  
  
     La relecture commence, puis marque une pause lorsque le premier curseur est atteint.  
  
5.  Appuyez sur F5 pour reprendre la trace.  
  
6.  Répétez l'étape 5 jusqu'à la fin de la trace.  
  
## <a name="see-also"></a> Voir aussi  
 [Relire jusqu’à un point d’arrêt &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)   
 [Relire des traces](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
