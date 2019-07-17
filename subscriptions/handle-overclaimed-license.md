---
title: Umgang mit zu häufig in Anspruch genommenen Lizenzen | Microsoft-Dokumentation
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 02/13/2018
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren mit zu häufig in Anspruch genommenen Abonnements umgehen.
ms.openlocfilehash: 23a0888a670c10af4447d7a097067ffe4fe70c0f
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783452"
---
# <a name="overallocated-subscriptions"></a>Zu viel zugewiesene Abonnements

Teilweise werden Bestellungen geändert, obwohl bereits Abonnenten hinzugefügt wurden, wodurch es dazu kommen kann, dass mehr Abonnements zugewiesen wurden als Lizenzen für Ihr Unternehmen vorhanden sind. Wenn dies der Fall ist, wird in der Registerkarte „Abonnenten“ eine Warnung mit zusätzlichen Informationen angezeigt.

> [!NOTE]
> In Open License-Programmen können Abonnements nicht zu häufig beansprucht werden.  Außerdem werden diese Informationen im Portal möglicherweise von anderen Programmen unterschiedlich angezeigt.
>
> [!div class="mx-imgBorder"]
> ![Benachrichtigung über zu häufig in Anspruch genommene Abonnements](_img/over-claimed/over-claimed-alert.png)

## <a name="resolving-overallocated-subscriptions"></a>Beheben von zu viel zugewiesenen Abonnements

So beheben Sie zu viel zugewiesene Lizenzen

1. Klicken Sie auf den Benachrichtigungstext. Dann werden eine filterbare Liste mit den Abonnenten, die der Abonnementstufe zugewiesen sind, und das zu häufig in Anspruch genommene Ablaufdatum angezeigt. 

2. Entfernen Sie so viele Abonnenten wie nötig, um die zu häufig in Anspruch genommenen Lizenzen zu bearbeiten. 

3. Die Übersicht im linken Bereich der Seite wird aktualisiert und zeigt an, dass die Kompatibilität wiederhergestellt wurde. Es werden keine Benachrichtigungen mehr über zu häufig in Anspruch genommene Abonnements angezeigt. 

## <a name="billing-and-true-up"></a>Abrechnung und True Up

Wenn Ihre Organisation über ein Enterprise Agreement (EA) verfügt, können Administratoren Abonnements zuweisen, ohne diese zu kaufen, und sie später durch einen Abgleichprozess bezahlen, der auch als „True Up“ bezeichnet wird.  Wenn Sie zu viel zuweisen, wird Ihrer Organisation die maximale Anzahl von Benutzern zugewiesenen Abonnements während des True Up in Rechnung gestellt.  Dies trifft auch zu, wenn Sie zum Zeitpunkt der Vornahme des True Ups nicht mehr die maximale Anzahl von Abonnements zugewiesen haben.  Weitere Informationen zum Überwachen Ihrer maximalen Verwendung finden Sie im Thema [Maximale Nutzung](maximum-usage.md).

> [!Important]
> Wenn Visual Studio-Abonnements mit GitHub Enterprise von Visual Studio-Abonnementadministratoren zugewiesen werden und nie ein Kauf dieser Abonnements stattgefunden hat, werden diese GitHub Enterprise-Administratoren innerhalb der Organisation nicht angezeigt. Um sicherzustellen, dass GitHub Enterprise-Abonnements sichtbar sind, sollte ein Kauf einschließlich **mindestens eines** Visual Studio Professional- mit GitHub Enterprise-Abonnements oder eines Visual Studio Enterprise- mit GitHub Enterprise-Abonnements getätigt werden, wenn die Abonnements zum ersten Mal zugewiesen werden.  
>
> Es liegt in der Verantwortung des Kunden sicherzustellen, dass für jedes zugewiesene GitHub-Abonnement ein entsprechendes Visual Studio- mit GitHub-Abonnement im Verwaltungsportal zugewiesen ist, damit die Lizenzierungsanforderungen für dieses Abonnement erfüllt sind.

Weitere Informationen zur Verwaltung von [Visual Studio-Abonnements mit GitHub Enterprise](assign-github.md).

## <a name="support-resources"></a>Supportressourcen

- Wenn Sie Unterstützung bei Vertrieb, Abonnements, Konten und Abrechnung für Visual Studio-Abonnements benötigen, wenden Sie sich an den [Abonnementsupport](https://visualstudio.microsoft.com/subscriptions/support/) für Visual Studio.
