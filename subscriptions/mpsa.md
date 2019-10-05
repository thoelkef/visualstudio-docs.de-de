---
title: Visual Studio-Abonnements in einer Microsoft-Vereinbarung für Produkte und Dienste (MPSA) | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/23/2019
ms.topic: conceptual
description: Visual Studio-Abonnements in einer Microsoft-Vereinbarung für Produkte und Dienste (MPSA)
ms.openlocfilehash: f87a77cdc19244ca24da1685c0b05372f6cc76d7
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605846"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Visual Studio-Abonnements in einer Microsoft-Vereinbarung für Produkte und Dienste (MPSA)
Wenn Sie Visual Studio-Abonnements über das MPSA-Programm erworben haben, müssen Sie einige Dinge beachten, bevor Sie ein Administrator von Visual Studio-Abonnements werden und Abonnements für Ihre Benutzer zuweisen können. Wenn Sie bereits Administratorrechte besitzen, können Sie direkt zum [Verwaltungsportal](https://manage.visualstudio.com/) für Visual Studio-Abonnements wechseln.

MPSA-Kunden verwalten ihre über MPSA erworbenen Ressourcen jetzt in einem neuen Portal namens [Business Center](https://businessaccount.microsoft.com/Customer), das ähnliche Funktionen unterstützt wie das Volume Licensing Service Center (VLSC). Dazu gehören die Anzeige Ihrer Lizenzzusammenfassung, Aufträge, Downloads, Schlüssel, Benutzer usw. Visual Studio-Abonnements in MPSA verhalten sich jedoch ähnlich wie Clouddienste. Das Business Center verwendet zudem Geschäftskonten statt Microsoft-Konten (MSA) zur Anmeldung. Wenn Ihre Organisation Clouddienste wie Office 365 oder Azure Active Directory verwendet und Ihre E-Mail-Adresse Teil eines dieser beiden Dienste ist, ist es bereits ein Geschäftskonto. Dadurch können Sie sich mit Ihrem vorhandenen Kennwort beim Business Center registrieren. Wenn Ihre Organisation keine Clouddienste verwendet und Ihre E-Mail-Adresse kein Geschäftskonto ist, können Sie die Adresse dennoch für die Registrierung beim Business Center verwenden.

Darüber hinaus ist das [Verwaltungsportal](https://manage.visualstudio.com/) für Visual Studio-Abonnements der Ort, an dem die Abonnements den Abonnenten zugewiesen werden, sobald Sie Administrator für Visual Studio-Abonnements sind. In MPSA müssen Visual Studio-Abonnements in ihrem jeweiligen Verwaltungsportal bereitgestellt werden, also im Verwaltungsportal für Visual Studio-Abonnements. Zu diesem Zweck müssen Sie Ihr Einkaufskonto einem Mandanten zuordnen (z.B. „contoso.onmicrosoft.com“).

Beachten Sie, dass es zwei Arten von Mandanten gibt: verwaltete und nicht verwaltete Mandanten. Der Begriff „verwalteter Mandant“ bezieht sich auf einen Mandanten, der bereits von internen Administratoren der Organisation verwaltet wird.

Ein nicht verwalteter Mandant ist ein Mandant ohne zugewiesene Administratoren und kann nicht für Onlinedienste wie Office 365 verwendet werden. Nicht verwaltete Mandanten werden auch erstellt, wenn die Registrierung beim Business Center mit einer E-Mail-Adresse durchgeführt wird, die kein Geschäftskonto ist. Wenn Sie während der Registrierung beim Business Center aufgefordert wurden, ein Kennwort zu erstellen, bedeutet dies, dass Ihre E-Mail-Adresse kein Geschäftskonto war und ein nicht verwalteter Mandant erstellt wurde.

Im Folgenden finden Sie einige Anforderungen/Schritte, die erforderlich sind, um Administrator für Visual Studio-Abonnements zu werden, bevor die Mandantenzuordnung abgeschlossen werden kann.

## <a name="pre-tenant-association-managed-tenant"></a>Vorabzuordnung des Mandanten (verwalteter Mandant)
- Sie müssen ein bei Business Center registrierter Benutzer sein.
- Sie müssen ein Benutzeradministrator (mindestens) oder ein globaler Administrator innerhalb des Mandanten sein, dem Sie angehören. (Dies gilt, wenn Ihr Unternehmen bereits Clouddienste verwendet). Die Rollen müssen Administratoren für Visual Studio-Abonnements sein.
- Sie müssen ein globaler Administrator des Mandanten sein, dem Sie angehören, um Ihr Einkaufskonto Ihrem Mandanten zuordnen zu können.
- Sie müssen ein Kontoadministrator oder Konto-Manager in Business Center sein.
- Das Feld „Land oder Region“ in Ihrem Benutzerprofil (sowie für alle anderen Benutzer) in [Azure](https://portal.azure.com/) muss abhängig von Ihrer Region (z.B. USA, Kanada usw.) ausgefüllt sein. 

> [!NOTE]
> Benutzer, die Sie zu Administratoren für Visual Studio-Abonnements machen möchten, müssen keine Benutzer im Business Center sein, da sie nur die Kriterien 2 und 5 erfüllen müssen.

Sobald Sie die oben genannten Kriterien erfüllen, können Sie damit fortfahren, Ihr Einkaufskonto Ihrem Mandanten zuzuordnen. Führen Sie dazu die folgenden Schritte aus.
1. Melden Sie sich bei [Business Center](https://businessaccount.microsoft.com/Customer) an.
2. Klicken Sie auf die Registerkarte **Konto**, und wählen Sie **Domänen zuordnen** aus.
3. Wählen Sie Ihr **Einkaufskonto** aus (falls mehrere vorhanden sind).
4. Wählen Sie Ihren **Mandanten** aus (z.B. „contoso.onmicrosoft.com“).
5. Klicken Sie auf **Domäne zuordnen**.

Nach der Zuordnung werden alle Benutzer, die die Kriterien erfüllen, in der Regel innerhalb weniger Minuten als Administratoren für Visual Studio Abonnements bereitgestellt. Manchmal kann es allerdings bis zu 24 Stunden dauern. Nach der Bereitstellung des Mandanten können Sie auf das Verwaltungsportal für Visual Studio-Abonnements zugreifen. Wenn es länger als 24 Stunden dauert, wenden Sie sich an den MPSA-Support.

> [!NOTE]
> Wenn es sich um neue Benutzer handelt, die (nach der Zuweisung) die Kriterien in den Schritten 2 und 5 erfüllen, müssen Sie sich an den MPSA-Support wenden. Der MPSA-Support bietet Unterstützung für die Bereitstellung der neuen Administratoren für Visual Studio-Abonnements.

## <a name="tenant-association-unmanaged"></a>Mandantenzuordnung (nicht verwaltet)
Wenn Sie sich beim Business Center mit einer E-Mail-Adresse registriert haben, die kein Geschäftskonto war (nicht in Azure Active Directory registriert), wie oben erläutert, verläuft die Mandantenzuordnung etwas anders. Sie müssen eine sogenannte „Domänenübernahme“ ausführen. Während dieses Vorgangs machen Sie sich selbst zum globalen Administrator. Dadurch wird Ihr Mandant von einem nicht verwalteten zu einem verwalteten.

Eine ausführlichere Erläuterung dieses Prozesses finden Sie in den [Schnellstartanleitungen](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx). Laden Sie das Handbuch *Setup and Use Your Online Services* (Einrichten und Verwenden Ihrer Onlinedienste) herunter, das Ihnen bei der Domänenübernahme hilft. Anschließend wird Ihr Einkaufskonto Ihrem Mandanten zugeordnet.

> [!NOTE]
> Nach der Domänenübernahme müssen Sie die Kriterien aus den fünf Schritten im Abschnitt „Vorabzuordnung des Mandanten (verwalteter Mandant)“ befolgen. Wenn die Kriterien erfüllt sind, müssen Sie sich nur an den MPSA-Support wenden, um weitere Administratoren für Visual Studio-Abonnements bereitzustellen.