---
title: Limitations de sécurité pour SQL Server sur Linux | Microsoft Docs
description: Cet article décrit SQL Server sur les restrictions de Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 9c58592568ca841df270190970fb76fefe43d96d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711717"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Limitations de sécurité pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Actuellement, SQL Server sur Linux présente les limitations suivantes :

* Une stratégie de mot de passe standard est fournie. La seule option que vous pouvez configurer est l’option MUST_CHANGE.  
* La gestion de clés extensible (EKM) n’est pas prise en charge. 
* Le stockage des clés dans Azure Key Vault n’est pas pris en charge.
* SQL Server génère son propre certificat auto-signé pour sécuriser le processus de connexion. Pour SSL ou TLS, SQL Server peut être configuré pour utiliser un certificat fourni par l'utilisateur. 

Pour plus d’informations sur les fonctionnalités de sécurité disponibles dans SQL Server, consultez le [centre de sécurité pour le moteur de base de données SQL Server et Azure SQL Database](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Étapes suivantes

Pour les tâches de sécurité courantes, consultez [prise en main des fonctionnalités de sécurité de SQL Server sur Linux](sql-server-linux-security-get-started.md). Pour obtenir un script pour modifier numéro de port TCP, les répertoires de SQL Server et configurer des traceflags ou le classement, consultez [configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md)
