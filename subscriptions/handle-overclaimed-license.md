---
title: Umgang mit zu viel zugewiesenen Lizenzen | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 03/03/2020
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren mit Überbelegungen bei Abonnements umgehen.
ms.openlocfilehash: b518dc9300862e7c39af0489734734668097ef9f
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453728"
---
# <a name="over-allocated-subscriptions"></a>Überbelegte Abonnements
Teilweise werden Bestellungen geändert, obwohl bereits Abonnenten hinzugefügt wurden, wodurch es dazu kommen kann, dass mehr Abonnements zugewiesen wurden als Lizenzen für Ihr Unternehmen vorhanden sind. Dies wird als „Überbelegung“ bezeichnet.  

Klicken Sie auf das Symbol oben links, um den Zuweisungsbereich zu öffnen und Abonnementzuweisungen anzuzeigen.  

> [!NOTE]
> Überbelegungen sind in Open License-Programmen nicht zulässig.  Außerdem werden diese Informationen im Portal möglicherweise von anderen Programmen unterschiedlich angezeigt.
>
> [!div class="mx-imgBorder"]
> ![Benachrichtigung über zu häufig in Anspruch genommene Abonnements](_img/over-claimed/over-claimed-alert.png "Die Anzahl von Überbelegungen ist in der Übersicht aufgeführt und wird im Diagramm durch den schraffierten Balken für jeden Abonnementtyp dargestellt.")

Beachten Sie, dass überbelegte Abonnements mit einem schraffierten Balken dargestellt werden.  Die Anzahl der überbelegten Abonnements für alle Abonnementtypen wird oben im Bereich „Übersicht“ angegeben. Zudem zeigt jede Abonnementstufe einen eigenen Zuweisungsstatus an.  

## <a name="resolve-over-allocated-subscriptions"></a>Beheben von Abonnementüberbelegungen
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

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentation zu Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Azure-Dokumentation](https://docs.microsoft.com/azure/)
- [Dokumentation zu Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
- Weitere Informationen zur Verwaltung von [Visual Studio-Abonnements mit GitHub Enterprise](assign-github.md).
- Wenn Sie Unterstützung bei Vertrieb, Abonnements, Konten und Abrechnung für Visual Studio-Abonnements benötigen, wenden Sie sich an den [Abonnementsupport](https://visualstudio.microsoft.com/subscriptions/support/) für Visual Studio.