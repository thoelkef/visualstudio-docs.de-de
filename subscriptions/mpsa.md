---
title: Visual Studio-Abonnements in einer Microsoft-Vereinbarung für Produkte und Dienste (MPSA) | Microsoft-Dokumentation
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: Get-Started-Article
description: Visual Studio-Abonnements in einer Microsoft-Vereinbarung für Produkte und Dienste (MPSA)
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: a18565a97c0cd85ce42109961592a57c490d92a1
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2018
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Visual Studio-Abonnements in einer Microsoft-Vereinbarung für Produkte und Dienste (MPSA)

Wenn Sie Visual Studio-Abonnements über das MPSA-Programm erworben haben, müssen Sie einige Dinge beachten, bevor Sie ein Administrator von Visual Studio-Abonnements werden und Abonnements für Ihre Benutzer zuweisen können. Wenn Sie bereits Administratorrechte besitzen, können Sie direkt zum [Administratorportal](https://manage.visualstudio.com/) für Visual Studio-Abonnements wechseln. 

Als MPSA-Kunde lernen Sie ein Portal kennen, in dem Sie Ihre über MPSA erworbenen Ressourcen verwalten können. Dieses neue Portal heißt [Business Center](https://businessaccount.microsoft.com/). Es unterstützt einige der Volume Licensing Service Center-Funktionen (VLSC) und neue Funktionen. Dazu gehören die Anzeige Ihrer Lizenzzusammenfassung, Aufträge, Downloads, Schlüssel, Benutzer usw. Visual Studio-Abonnements in MPSA verhalten sich jedoch ähnlich wie Clouddienste. Business Center verwendet zudem Geschäftskonten statt Microsoft-Konten zur Anmeldung. Wenn Ihre Organisation Clouddienste wie Office 365 oder Azure Active Directory verwendet und Ihre E-Mail-Adresse Teil eines dieser beiden Dienste ist, ist es bereits ein Geschäftskonto. Dadurch können Sie Business Center mit Ihrem vorhandenen Kennwort registrieren, das Ihre Organisation für Sie festgelegt hat. Auch wenn Ihre Organisation keine Clouddienste verwendet und Ihre E-Mail-Adresse kein Geschäftskonto ist, können Sie sie für die Registrierung beim Business Center verwenden.

Darüber hinaus ist das [Verwaltungsportal](https://manage.visualstudio.com/) für Visual Studio-Abonnements der Ort, an dem die Abonnements den Abonnenten zugewiesen werden, sobald Sie ein Visual Studio-Administrator sind. In MPSA müssen Visual Studio-Abonnements in ihrem jeweiligen Verwaltungsportal bereitgestellt werden, also im Verwaltungsportal für Visual Studio-Abonnements. Zu diesem Zweck müssen Sie Ihr Einkaufskonto einem Mandanten zuordnen (z.B. „contoso.onmicrosoft.com“). 

Beachten Sie, dass es zwei Arten von Mandanten gibt (verwaltete Mandanten und nicht verwaltete Mandanten). Ein verwalteter Mandant bezieht sich auf ein Mandanten, der bereits von der Organisation von internen Administratoren verwaltet wird. 

Ein nicht verwalteter Mandant ist ein Mandant ohne interne Administratoren, und er kann nicht für Onlinedienste wie Office 365 verwendet werden. Nicht verwaltete Mandanten werden auch erstellt, wenn die Registrierung bei Business Center mit einer E-Mail-Adresse durchgeführt wird, die kein Geschäftskonto ist. Wenn Sie während der Registrierung bei Business Center aufgefordert wurden, ein Kennwort zu erstellen, bedeutet dies, dass Ihre E-Mail-Adresse kein Geschäftskonto war und dass ein nicht verwalteter Mandant erstellt wurde.

Vor dem Abschließen der Mandantenzuordnung sind hier einige Anforderungen/Schritte erforderlich, um ein Administrator für Visual Studio-Abonnements zu werden.

## <a name="pre-tenant-association-managed-tenant"></a>Vorabzuordnung des Mandanten (verwalteter Mandant)
-   Sie müssen ein bei Business Center registrierter Benutzer sein.
-   Sie müssen ein Benutzeradministrator (mindestens) oder ein globaler Administrator innerhalb des Mandanten sein, dem Sie angehören. (Dies gilt, wenn Ihr Unternehmen bereits Clouddienste verwendet). Die Rollen müssen Administratoren für Visual Studio-Abonnements sein.
-   Sie müssen ein globaler Administrator des Mandanten sein, dem Sie angehören, um Ihr Einkaufskonto Ihrem Mandanten zuordnen zu können.
-   Sie müssen ein Kontoadministrator oder Konto-Manager in Business Center sein.
-   Das Feld „Land oder Region“ in Ihrem Benutzerprofil (sowie für alle anderen Benutzer) in [Azure](https://portal.azure.com/) muss abhängig von Ihrer Region (z.B. USA, Kanada usw.) ausgefüllt sein. 

> [!NOTE]
> Benutzer, die Sie zu Administratoren für Visual Studio-Abonnements machen möchten, müssen keine Benutzer in Business Center sein, da sie nur die Kriterien in den Schritten 2 und 5 erfüllen müssen.

Sobald Sie die Kriterien in den vorherigen fünf Schritten erfüllen, können Sie damit fortfahren, Ihr Einkaufskonto mit den folgenden Schritten Ihrem Mandanten zuzuordnen.
1.  Melden Sie sich bei [Business Center](https://businessaccount.microsoft.com/) an.
2.  Klicken Sie auf die Registerkarte **Konto**, und wählen Sie **Domänen zuordnen** aus.
3.  Wählen Sie Ihr **Einkaufskonto** aus (falls mehrere vorhanden sind).
4.  Wählen Sie Ihren **Mandanten** aus (z.B. „contoso.onmicrosoft.com“).
5.  Klicken Sie auf **Domäne zuordnen**.

Nach der Zuordnung werden alle Benutzer, die die erforderlichen Kriterien erfüllen, in der Regel innerhalb von Minuten als Administratoren für Visual Studio Abonnements bereitgestellt. Manchmal kann es allerdings bis zu 24 Stunden dauern. Nach der Bereitstellung können Sie auf das Verwaltungsportal für Visual Studio-Abonnements zugreifen. Wenn es länger als 24 Stunden dauert, wenden Sie sich an den MPSA-Support.

> [!NOTE]
> Wenn neue Benutzer (nach der Zuweisung) die Kriterien in den Schritten 2 und 5 erfüllen, müssen Sie sich an den MPSA-Support wenden. Der MPSA-Support bietet Unterstützung für die Bereitstellung der neuen Administratoren für Visual Studio-Abonnements.

## <a name="tenant-association-unmanaged"></a>Mandantenzuordnung (nicht verwaltet)

Wenn Sie sich bei Business Center mit einer E-Mail-Adresse registriert haben, die kein Geschäftskonto war (nicht in Azure Active Directory (Azure AD) registriert), wie im Absatz fünf oben erläutert, verläuft die Mandantenzuordnung etwas anders. Sie müssen eine sogenannte „Domänenübernahme“ ausführen. Während dieses Vorgangs machen Sie sich selbst zum globalen Administrator. Dadurch wird Ihr Mandant von einem nicht verwalteten zu einem verwalteten.

Eine ausführlichere Erläuterung dieses Prozesses finden Sie in den [Schnellstartanleitungen](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx). Laden Sie das Handbuch *Setup and Use Your Online Services* (Einrichten und Verwenden Ihrer Onlinedienste) herunter, das Ihnen bei der Domänenübernahme hilft. Anschließend wird Ihr Einkaufskonto Ihrem Mandanten zugeordnet.

> [!NOTE]
> Nach der Domänenübernahme müssen Sie die Kriterien aus den fünf Schritten im Abschnitt „Vorabzuordnung des Mandanten (verwalteter Mandant)“ befolgen. Wenn die Kriterien erfüllt sind, müssen Sie sich nur an den MPSA-Support wenden, um weitere Administratoren für Visual Studio-Abonnements bereitzustellen.

Wenn Sie Unterstützung benötigen oder Fragen haben, erreichen Sie den Support per Telefon oder E-Mail.

MPSA-Support: **1-866-200-9611**, Montag bis Freitag, 5:30 Uhr bis 17:30 Uhr (Pacific Time)

E-Mail: ngvlsup@microsoft.com
