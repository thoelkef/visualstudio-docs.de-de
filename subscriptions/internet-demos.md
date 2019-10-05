---
title: Verwenden von Product Keys zur Unterstützung von Internetdemonstrationen über Terminaldienste | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Informationen zum Verwenden von Product Keys zur Unterstützung von Internetdemonstrationen über Terminaldienste und zum Aktivieren des RDS-Zugriffs
ms.openlocfilehash: 19faa64b7eeaebc1b92ca965f686795b31e00e7e
ms.sourcegitcommit: 9fc8b144d4ed1c46aba87c0b7e1d24454e0eea9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68493384"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Internetdemonstrationen über Terminaldienste
Mit einem Visual Studio-Abonnement sind Sie berechtigt, Benutzern den Zugriff auf Internetdemonstrationen Ihrer Programme über Terminaldienste (Windows Server 2003 oder Windows Server 2008) oder Remotedesktopdienste (Windows Server 2008 R2 und höher) zu ermöglichen. So können bis zu 200 anonyme Benutzer gleichzeitig auf Ihre Demonstration zugreifen. In Ihrer Demonstration dürfen keine Produktionsdaten verwendet werden. Visual Studio-Abonnenten sind berechtigt, Benutzern ihre Anwendungen zu demonstrieren. Allerdings können bei dieser Internetdemonstration Benutzer ohne Visual Studio-Abonnement nur über Terminaldienste (Terminal Services, TS) oder Remotedesktopdienste (Remote Desktop Services, RDS) mit der Demonstrationsanwendung interagieren, solange die Software mittels Visual Studio-Abonnements lizenziert ist.

Dies ist eine Ergänzung der Entwicklungs-/Testrechte, gemäß denen Visual Studio-Abonnenten so viele RDS- oder TS-Verbindungen wie nötig verwenden können.

## <a name="enabling-rds-access"></a>Aktivieren des RDS-Zugriffs
Visual Studio-Abonnenten können die Anzahl der Benutzer mit Zugriff auf Windows Server über RDS erhöhen, indem Sie im [Abonnentenportal](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) auf der Registerkarte [Produkt Keys](https://my.visualstudio.com?wt.mc_id=o~msft~docs) einen Product Key eingeben. Öffnen Sie zum Abrufen eines Product Key die Seite „Product Keys“, und scrollen Sie nach unten zur der Version von Windows Server, die Sie ausführen. Suchen Sie „Windows Server <Version> R2-Remotedesktopdienste <Benutzer oder Gerät>-Verbindungen“, und klicken Sie auf die Schaltfläche **Claim Key** (Schlüssel in Anspruch nehmen). Wenn Sie beispielsweise RDS unter Windows Server 2012 R2 verwenden und Ihre Bereitstellung Benutzer-Clientzugriffslizenzen umfasst, wählen Sie „Windows Server 2012 > Remotedesktopdienste > Benutzerverbindungen (50)“ aus.
Für Windows Server 2008 R2 stehen für jeden Typ fünf Schlüssel zur Verfügung, die jeweils 20 Verbindungen unterstützen. Für Windows Server 2012 R2 stehen für jeden Typ vier Schlüssel zur Verfügung, die jeweils 50 Verbindungen unterstützen.

## <a name="to-enable-additional-connections-in-windows-server"></a>So aktivieren Sie unter Windows Server weitere Verbindungen:
1. Öffnen Sie den Server-Manager.
2. Öffnen Sie im linken Navigationsbereich die Liste „Server“.
3. Klicken Sie mit der rechten Maustaste auf Ihren Lizenzserver, und wählen Sie „Lizenzen installieren“ aus.
4. Folgen Sie den Anweisungen des Assistenten.  Wählen Sie bei der Auswahl des Vertragstyps „Vollprodukterwerb“ aus, und geben Sie den Product Key ein, den Sie unter „Mein Portal“ erhalten haben.

Benutzer können über RDS auf Anwendungen zugreifen, wenn die folgenden Bedingungen erfüllt sind:
- Die Benutzer müssen anonym (nicht authentifiziert) sein.
- Verbindungen müssen über das Internet erfolgen.
- Für Demonstrationen der Anwendung sind bis zu 200 gleichzeitige Verbindungen möglich.
- Die Product Keys zum Aktivieren von Benutzerverbindungen müssen von einem Visual Studio-Abonnenten abgerufen werden.

## <a name="next-steps"></a>Nächste Schritte
Besuchen Sie über https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf die mehrteilige Blogserie zur **RDS 2012-Sitzungsbereitstellung (Remote Desktop Services, Remotedesktopdienste)** für Anleitungen zur Bereitstellung von RDS. 

Falls Sie Fragen haben, besuchen Sie das [Forum für Microsoft-Remotdesktopdienste](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS).
