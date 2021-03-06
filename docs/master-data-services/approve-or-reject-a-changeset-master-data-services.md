---
title: Approuver ou rejeter un ensemble de modifications (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 45bd01f9-ae15-4fc5-a2ba-eee565a26ef8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 0b065c878217f52f2cffaff05b4e6a9f28312dd4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52759131"
---
# <a name="approve-or-reject-a-changeset-master-data-services"></a>Approuver ou rejeter un ensemble de modifications (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Un ensemble de modifications regroupe des modifications en attente, qui portent sur les données de référence. Si des modifications de l’entité requièrent l’approbation d’un administrateur et si un ensemble de modifications est soumis pour approbation, vous pouvez examiner puis approuver ou rejeter cet ensemble de modifications.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** . Pour plus d’informations, consultez [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Vous devez disposer d’une autorisation administrateur pour l’entité.  
  
-   Les modifications de l’entité nécessitent l’approbation d’un administrateur.  
  
-   Si l’état de l’ensemble de modifications est en attente, vous pouvez examiner puis approuver ou rejeter cet ensemble de modifications.  
  
-   Les utilisateurs ne sont pas autorisés à approuver leurs propres modifications. Si vous êtes l’administrateur de l’entité, vous devez affecter un administrateur secondaire qui approuvera votre propre ensemble de modifications.  
  
## <a name="to-approve-or-reject-a-changeset"></a>Pour approuver ou rejeter un ensemble de modifications  
  
1.  Sur la page d’accueil [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , sélectionnez le modèle et la version, puis cliquez sur **Explorateur**.  
  
2.  Cliquez sur une entité dans le menu **Entités** .  
  
3.  Dans le volet droit, sélectionnez **Ensembles de modifications** , puis double-cliquez sur l’ensemble de modifications à approuver ou à rejeter.  
  
4.  Cliquez sur **Appliquer** pour appliquer l’ensemble de modifications et vérifier les modifications en attente.  
  
5.  Cliquez sur **Rejeter** pour rejeter l’ensemble de modifications et le renvoyer au propriétaire.  
  
6.  Cliquez sur **Approuver** pour approuver l’ensemble de modifications. L’ensemble de modifications est automatiquement validé.  
  
## <a name="see-also"></a> Voir aussi  
 [Créer un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [Appliquer et mettre à jour un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [Valider ou envoyer un ensemble de modifications &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
  
