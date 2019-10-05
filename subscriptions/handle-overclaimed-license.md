---
title: Umgang mit zu viel zugewiesenen Lizenzen | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren mit zu viel zugewiesenen Abonnements umgehen.
ms.openlocfilehash: 924f6fb2c513d70aefd28c1d4ff18d1af62178c2
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605505"
---
# <a name="overallocated-subscriptions"></a>Zu viel zugewiesene Abonnements
Teilweise werden Bestellungen geändert, obwohl bereits Abonnenten hinzugefügt wurden, wodurch es dazu kommen kann, dass mehr Abonnements zugewiesen wurden als Lizenzen für Ihr Unternehmen vorhanden sind. Dies wird als „Überbelegung“ bezeichnet.  Wenn dies der Fall ist, wird in der Registerkarte „Abonnenten“ eine Warnung mit zusätzlichen Informationen zur Anzahl der zu viel zugewiesenen Abonnements angezeigt.

> [!NOTE]
> Überbelegungen sind in Open License-Programmen nicht zulässig.  Außerdem werden diese Informationen im Portal möglicherweise von anderen Programmen unterschiedlich angezeigt.
>
> [!div class="mx-imgBorder"]
> ![Benachrichtigung über zu häufig in Anspruch genommene Abonnements](_img/over-claimed/over-claimed-alert.png)

## <a name="resolve-overallocated-subscriptions"></a>Beheben von Abonnementüberbelegungen
Es gibt mehrere Möglichkeiten, Überbelegungen zu beheben:
- Wenden Sie sich an Ihren Handelspartner, um weitere Abonnements zu erwerben.
- Warten Sie bis zur jährlichen Abgleichperiode, und bezahlen Sie die zu viel zugewiesenen Abonnements zu diesem Zeitpunkt. 
- Löschen Sie einige Abonnementzuweisungen.  (Auch in diesem Fall ist eine Zahlung der Überbelegungen beim jährlichen Abgleich notwendig, da der Abgleich auf der maximalen Anzahl von Abonnements basiert, die zu einem beliebigen Zeitpunkt während des Jahrs zugewiesen waren.)

## <a name="billing-and-true-up"></a>Abrechnung und True Up
Wenn Ihre Organisation über ein Enterprise Agreement (EA) verfügt, können Administratoren Abonnements zuweisen, ohne diese zu kaufen, und sie später durch einen Abgleichprozess bezahlen, der auch als „True Up“ bezeichnet wird.  Wenn Sie zu viel zuweisen, wird Ihrer Organisation die maximale Anzahl von Benutzern zugewiesenen Abonnements während des True Up in Rechnung gestellt.  Dies trifft auch zu, wenn Sie zum Zeitpunkt der Vornahme des True Ups nicht mehr die maximale Anzahl von Abonnements zugewiesen haben.  Weitere Informationen zum Überwachen Ihrer maximalen Verwendung finden Sie im Thema [Maximale Nutzung](maximum-usage.md).

> [!Important]
> Wenn Visual Studio-Abonnements mit GitHub Enterprise von Visual Studio-Abonnementadministratoren zugewiesen werden und nie ein Kauf dieser Abonnements stattgefunden hat, werden diese GitHub Enterprise-Administratoren innerhalb der Organisation nicht angezeigt. Um sicherzustellen, dass GitHub Enterprise-Abonnements sichtbar sind, sollte ein Kauf einschließlich **mindestens eines** Visual Studio Professional- mit GitHub Enterprise-Abonnements oder eines Visual Studio Enterprise- mit GitHub Enterprise-Abonnements getätigt werden, wenn die Abonnements zum ersten Mal zugewiesen werden.
>
> Es liegt in der Verantwortung des Kunden sicherzustellen, dass für jedes zugewiesene GitHub-Abonnement ein entsprechendes Visual Studio- mit GitHub-Abonnement im Verwaltungsportal zugewiesen ist, damit die Lizenzierungsanforderungen für dieses Abonnement erfüllt sind.

## <a name="next-steps"></a>Nächste Schritte
- Weitere Informationen zur Verwaltung von [Visual Studio-Abonnements mit GitHub Enterprise](assign-github.md).
- Wenn Sie Unterstützung bei Vertrieb, Abonnements, Konten und Abrechnung für Visual Studio-Abonnements benötigen, wenden Sie sich an den [Abonnementsupport](https://visualstudio.microsoft.com/subscriptions/support/) für Visual Studio.
