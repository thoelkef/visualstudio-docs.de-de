---
title: Verwenden des Features „Maximum Usage“ (Maximale Auslastung) im Verwaltungsportal
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/24/2019
ms.topic: conceptual
description: Erfahren Sie, wie Sie sich die maximale Anzahl zugewiesener Abonnements im Visual Studio-Verwaltungsportal anzeigen lassen können.
ms.openlocfilehash: 368ca1ad0373267e9753ab223c2e200cbc87f1e0
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491720"
---
# <a name="use-the-maximum-usage-feature-to-track-the-number-of-assigned-subscriptions"></a>Verwenden des Features „Maximum Usage“ (Maximale Auslastung) zur Übersicht der Anzahl zugewiesener Abonnements
Mithilfe eines neuen Features im Verwaltungsportal für Visual Studio-Abonnements haben Sie immer im Blick, wie viele Abonnements Sie erworben und zugewiesen haben, und wissen, wie viele Abonnements auf jeder Stufe Sie sowohl während des vergangenen Jahres als auch über die gesamte Dauer Ihrer Vereinbarung hinweg maximal zugewiesen hatten. 

## <a name="view-your-maximum-usage"></a>Anzeigen der maximalen Auslastung
So können Sie sich die maximale Anzahl zugewiesener Abonnements für jede Vereinbarung und für jede Abonnementstufe anzeigen lassen:
1. Wählen Sie oben links im Portal aus der Dropdownliste die Vereinbarung aus, die Sie sich ansehen möchten. (Wenn Sie nur eine Vereinbarung haben, ist diese bereit ausgewählt.)
2. Klicken Sie auf die Registerkarte **Maximum Usage** (Maximale Auslastung).  
    > [!div class="mx-imgBorder"]
    > ![Screenshot: Menü „Maximum Usage“ (Maximale Auslastung)](_img/maximum-usage/maximum-usage-menu.png)
3. Die „Maximum Usage Summary“ (Zusammenfassung der maximalen Auslastung) wird angezeigt. Unter dieser sehen Sie die höchste Zahl an Abonnements, die Sie im vergangenen Jahr für jede Stufe zugewiesen hatten, zusammen mit dem Datum, an dem dieser Höchstwert erreicht wurde.  Wenn der Höchstwert mehr als einmal erreicht wurde, wird das Datum angezeigt, an dem Sie ihn das erste Mal erreicht haben. 
    > [!div class="mx-imgBorder"]
    > ![Screenshot: „Maximum Usage Summary“ (Zusammenfassung der maximalen Auslastung)](_img/maximum-usage/maximum-usage-summary.png)
4. Wenn Sie sich die höchste Zahl an zugewiesenen Abonnements währen der gesamten Dauer der Vereinbarung ansehen möchten, klicken Sie auf die Registerkarte **Full-Term** (Gesamte Dauer).

## <a name="view-your-assignment-history"></a>Anzeigen Ihres Zuweisungsverlaufs
Zusätzlich zu den Höchstwerten von Zuweisungen für jede Abonnementstufe können Sie sich auch einen Überblick über die Aktivitäten im Rahmen der Vereinbarung ansehen, z.B. Käufe und Zuweisungen. Klicken Sie dazu auf die Schaltfläche **Export full report** (Vollständigen Bericht exportieren).  

> [!div class="mx-imgBorder"]
> ![Screenshot: Vollständiger Bericht über die maximale Auslastung](_img/maximum-usage/maximum-usage-full-report.png)

Im Bericht werden für jede Abonnementstufe das Datum angezeigt, an dem ein neuer Höchstwert an Zuweisungen erreicht wurde, sowie die Anzahl von Abonnements, die Sie bis zu diesem Datum erworben hatten. So sehen Sie problemlos, an welchen Tagen es zu Überlastungen kam.  

In der Tabelle oben können Sie z.B. sehen, dass am 13.12.2018 von den 123 im Rahmen der Vereinbarung verfügbaren Visual Studio Enterprise-Abonnements insgesamt 120 zugewiesen waren.  Am 8.1.2019 wurde ein weiteres Abonnement zugewiesen, insgesamt also 121.  Am nächsten Tag wurden sechs weitere Abonnements zugewiesen, und der Vereinbarung wurden vier weitere Abonnements hinzugefügt, um die neuen Zuweisungen abdecken zu können.  

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
### <a name="q-how-is-the-information-in-the-maximum-usage-different-from-the-assignment-information-available-in-the-overview-section-on-the-left-side-of-the-portal"></a>Frage: Inwiefern unterscheiden sich die Informationen, die durch das Feature „Maximum Usage“ (Maximale Auslastung) gewonnen werden können, von den Zuweisungsinformationen, die auf der linken Seite des Portals im Bereich „Overview“ (Übersicht) verfügbar sind?
Antwort:  Die Informationen in der Übersicht zeigen die *aktuellen* Zuweisungen und die verfügbaren Abonnements für jede Abonnementebene an.  Diese Zahlen können stark von der maximalen Anzahl von Abonnements abweichen, die dem Abonnement während des laufenden Jahres oder während der Laufzeit der Vereinbarung zugewiesen werden.  Mithilfe des Features „Maximale Nutzung“ können Sie sich anzeigen lassen, wann diese Höchstwerte für Zuweisungen erreicht wurden, und wie hoch diese waren.  Dieser Unterschied ist entscheidend, da die Abrechnung für Abonnements während des Abgleichs auf der maximalen Zahl von Abonnements basiert, die zu einem beliebigen Zeitpunkt im Jahr zugewiesen waren. 

## <a name="resources"></a>Ressourcen
- [Whitepaper zur Lizenzierung von Visual Studio](https://aka.ms/vslicensing)
- [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Nutzungsbedingungen für die Volumenlizenzierung](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="next-steps"></a>Nächste Schritte
- Wenn Sie Fragen zu Abonnementzuweisungen oder zu anderen Bereichen des Visual Studio-Verwaltungsportals haben, finden Sie unter https://visualstudio.microsoft.com/subscriptions/support/ weitere Informationen. 
- Erfahren Sie, was Sie tun müssen, wenn Sie mehr Abonnements zuweisen, als Sie erworben haben – dies wird als [Überbelegung](handle-overclaimed-license.md) bezeichnet.
