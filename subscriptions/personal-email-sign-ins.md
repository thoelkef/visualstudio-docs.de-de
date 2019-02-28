---
title: Persönliche E-Mail-Nachrichten, die im VLSC angezeigt werden
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: conceptual
description: Visual Studio-Abonnements – Warum sehe ich Hotmail- oder Gmail-Adressen für meine Abonnenten?
searchscope: VS Subscription
ms.openlocfilehash: 0ba4029fcec0c8d35a58def14ab38afbb79e2fee
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843376"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio-Abonnements – Warum sehe ich Hotmail- oder Gmail-Adressen für meine Abonnenten?

Wenn Unternehmen vom Volume Licensing Service Center (VLSC) zum neuen [Abonnementverwaltungsportal](https://manage.visualstudio.com) von Visual Studio migrieren, stellen Administratoren möglicherweise überrascht fest, dass als „Anmelde-E-Mail-Adresse“ für manche Abonnenten eine E-Mail-Adresse von Drittanbietern wie Hotmail, Gmail oder Yahoo angezeigt wird.  Weitere Informationen finden Sie [in diesem Video](https://www.youtube.com/watch?v=1op-i1zEMfY&t=0s&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=6).

## <a name="cause"></a>Ursache

Grund für dieses Szenario sind Anmeldeprozesse, die mit dem älteren MSDN-Abonnentenprozess verknüpft waren. Benutzer wurden ohne Änderungen aus dem Volume Licensing-Servicecenter (VLSC) zum neuen Portal migriert. Den Administratoren war möglicherweise nicht bewusst, dass Benutzer persönliche Konten verwendet hatten, um auf ihre Abonnementvorteile zuzugreifen. Vor den Visual Studio-Abonnentenmigrationen, die 2016 abgeschlossen wurden, waren zur erfolgreichen Verwendung eines Visual Studio-Abonnements zwei Aktionen erforderlich:
1. Der Administrator „wies“ das Abonnement einem einzelnen Abonnenten unter Verwendung seiner Geschäfts- oder Schul-E-Mail-Adresse zu.
2. Der Abonnent „aktivierte“ das Abonnement.

Während der Aktivierung des Abonnenten galt: Ein Microsoft-Konto (MSA) war zum Anmelden erforderlich. Wenn der Abonnent nicht versuchte, sein Geschäfts- oder Schulkonto (z.B. tasha@contoso.com) zu einem MSA zu machen, konnte er ein neues MSA erstellen oder ein vorhandenes nutzen. Dies führte dazu, dass seine „Anmelde-E-Mail-Adresse“ sich von seiner „‘Zugewiesen an‘-E-Mail-Adresse" unterschied.

> [!NOTE]
> Der neue Abonnentenprozess in [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) unterstützt sowohl Geschäfts-, Uni- und Schulkonto- als auch Microsoft-Kontoidentitätstypen (MAA).

Da die Administratormigration Daten aus dem VLSC bezüglich der „Anmelde-E-Mail-Adresse“ des Abonnenten für den neuen Abonnentenverwaltungsprozess verwendet, können schließlich möglicherweise vor kurzem migrierte Administratoren diese zuvor nicht bemerkten persönlichen Konten aufgrund von Änderungen an der Benutzeroberfläche sehen, die diese Informationen besser sichtbar machen.

## <a name="solution"></a>Lösung

Um das Problem zu beheben, müssen Sie Abonnenteninformationen bearbeiten, um ihre Anmelde-E-Mail-Adressen zu aktualisieren.  Bearbeitungen können für einzelne Abonnenten oder mehrere gleichzeitig vorgenommen werden. Ausführliche Informationen finden Sie unter [Bearbeiten von Visual Studio-Abonnementzuweisungen](edit-license.md).

Nachdem Sie die E-Mail-Adressen der Abonnenten aktualisiert haben, sollten Sie ihnen mitteilen, dass ihre Anmeldeinformationen geändert wurden.  Sie erhalten auch eine E-Mail mit den aktualisierten Informationen.