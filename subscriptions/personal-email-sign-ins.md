---
title: Im VLSC angezeigte persönliche E-Mail-Nachrichten
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Visual Studio-Abonnements – Warum sehe ich Hotmail- oder Gmail-Adressen für meine Abonnenten?
ms.openlocfilehash: 8418a177e793f0b4fe9a5019d2cf62fa724312ff
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605751"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio-Abonnements – Warum sehe ich Hotmail- oder Gmail-Adressen für meine Abonnenten?
Nachdem Unternehmen vom Volume Licensing Service Center (VLSC) zum neuen [Abonnementverwaltungsportal](https://manage.visualstudio.com) von Visual Studio migriert haben, stellen Administratoren möglicherweise fest, dass als „Anmelde-E-Mail-Adresse“ für manche Abonnenten eine E-Mail-Adresse von Drittanbietern wie Hotmail, Gmail oder Yahoo angezeigt wird.  Weitere Informationen finden Sie [in diesem Video](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Ursache
Grund für dieses Szenario sind Anmeldeprozesse, die mit dem älteren MSDN-Abonnentenprozess verknüpft waren. Benutzer wurden ohne Änderungen aus dem Volume Licensing-Servicecenter (VLSC) zum Verwaltungsportal für Visual Studio-Abonnements migriert. Den Administratoren war möglicherweise nicht bewusst, dass Benutzer persönliche Konten verwendet hatten, um auf ihre Abonnementvorteile zuzugreifen. Vor den Visual Studio-Abonnentenmigrationen, die 2016 abgeschlossen wurden, waren zur erfolgreichen Verwendung eines Visual Studio-Abonnements zwei Aktionen erforderlich:
1. Der Administrator „wies“ das Abonnement einem einzelnen Abonnenten unter Verwendung seiner Geschäfts- oder Schul-E-Mail-Adresse zu.
2. Der Abonnent „aktivierte“ das Abonnement.

Während der Aktivierung des Abonnenten galt: Ein Microsoft-Konto (MSA) war zum Anmelden erforderlich. Wenn der Abonnent nicht versuchte, sein Geschäfts- oder Schulkonto (z.B. tasha@contoso.com) zu einem MSA zu machen, konnte er ein neues MSA erstellen oder ein vorhandenes nutzen. Dies führte dazu, dass seine „Anmelde-E-Mail-Adresse“ sich von seiner „‘Zugewiesen an‘-E-Mail-Adresse" unterschied.

> [!NOTE]
> Der neue Abonnentenprozess in [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) unterstützt sowohl Geschäfts-, Uni- und Schulkonto- als auch Microsoft-Kontoidentitätstypen (MAA).

Bei der Administratormigration wurden aus dem VLSC stammende Daten zu den Anmelde-E-Mail-Adressen der Abonnenten in den neuen Abonnentenverwaltungsprozess übernommen. Daher sehen kürzlich migrierte Administratoren diese zuvor nicht bemerkten persönlichen Konten möglicherweise auf der neuen Benutzeroberfläche, die diese Informationen besser sichtbar macht.

## <a name="solution"></a>Lösung
Um das Problem zu beheben, müssen Sie Abonnenteninformationen bearbeiten, um ihre Anmelde-E-Mail-Adressen zu aktualisieren.  Bearbeitungen können für einzelne Abonnenten oder mehrere gleichzeitig vorgenommen werden. Vollständige Informationen finden Sie unter [Bearbeiten von Abonnements](edit-license.md).

##  <a name="next-steps"></a>Nächste Schritte
- Wenn Sie die E-Mail-Adressen der Abonnenten aktualisiert haben, sollten Sie ihnen mitteilen, dass ihre Anmeldeinformationen geändert wurden.  Sie erhalten auch eine E-Mail mit den aktualisierten Informationen.
- Es kann hilfreich sein, die [Liste der Abonnenten in Ihrer Organisation zu filtern](search-license.md), um nach Anmelde-E-Mail-Adressen zu suchen, die möglicherweise geändert werden müssen.  

