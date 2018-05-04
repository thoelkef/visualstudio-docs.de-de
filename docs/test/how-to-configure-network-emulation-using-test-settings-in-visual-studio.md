---
title: Konfigurieren von Netzwerkemulation mithilfe von Testeinstellungen in Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 66877397912fca0fbd3996c2dab146b040a047b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Gewusst wie: Konfigurieren von Netzwerkemulation mithilfe von Testeinstellungen in Visual Studio

Sie können den Adapter für diagnostische Daten für das Testen einer Anwendung in verschiedenen Netzwerkumgebungen von Visual Studio konfigurieren. Er kann auch so konfiguriert werden, dass eine künstliche Netzwerklast oder ein Engpass beim Ausführen der Tests getestet wird.

> [!WARNING]
> Wenn Sie die Tests auf einem realen Netzwerk ausführen, das langsamer ist als das Netzwerk, das Sie emulieren, wird der Test weiterhin mit der langsameren Netzwerkgeschwindigkeit ausgeführt. Die Emulation kann die Netzwerkumgebung nur verlangsamen, sie jedoch nicht schneller machen.

 Im folgenden Verfahren wird beschrieben, wie die Netzwerkemulation über den Konfigurations-Editor konfiguriert wird. Diese Schritte gelten für den Konfigurations-Editor in Microsoft Test Manager und Visual Studio.

> [!NOTE]
> Der Adapter für diagnostische Daten für die Netzwerkemulation gilt nur für Visual Studio-Testeinstellungen. Er wird nicht für Testeinstellungen in Microsoft Test Manager verwendet.

Für die Netzwerkemulation muss ein Konto mit Administratorrechten verwendet werden. Wenn Sie die Netzwerkemulation für eine lokale Rolle ausgewählt haben, mit der manuelle Tests ausgeführt werden, müssen Sie Microsoft Test Manager mit Administratorrechten starten. Wenn Sie Netzwerkemulation für eine beliebige andere Rolle ausgewählt haben, müssen Sie überprüfen, ob der Test-Agent auf dem Computer für diese Rolle ein Benutzerkonto verwendet, das Mitglied der Administratorgruppe ist. Weitere Informationen über das Einrichten des Kontos für Ihren Test-Agent finden Sie unter[Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).

> [!NOTE]
> Das Netzwerkdienstkonto, das das Standardkonto für den Test-Agent ist, ist kein Mitglied der Administratorgruppe.

 **Wahre Netzwerkemulation**

 Visual Studio verwendet softwarebasierte wahre Netzwerkemulation für alle Testtypen. Das gilt auch für Auslastungstests. Wahre Netzwerkemulation simuliert Netzwerkbedingungen durch direkte Bearbeitung der Netzwerkpakete. Der wahre Netzwerkemulator kann das Verhalten von Kabel- und Funknetzwerken mit einem zuverlässigen physischen Kanal (z. B. einem Ethernet) emulieren. Die folgenden Netzwerkattribute werden in wahre Netzwerkemulation integriert:

-   Roundtripzeit für das Netzwerk (Wartezeit)

-   Die Menge an verfügbarer Bandbreite

-   Warteschlangenverhalten

-   Paketverlust

-   Neuanordnung von Paketen

-   Fehlerweitergabe

 Wahre Netzwerkemulation bietet auch Flexibilität beim Filtern von Netzwerkpaketen auf Grundlage von IP-Adressen oder Protokollen, z. B. TCP, UDP und ICMP.

 Wahre Netzwerkemulation kann von netzwerkbasierten Entwicklern und Testern dazu verwendet werden, eine gewünschte Testumgebung zu emulieren, die Leistung zu bewerten, die Auswirkungen auf Änderung zu prognostizieren oder Entscheidungen zur Technologieoptimierung zu treffen. Im Vergleich zu Hardwareprüfständen ist wahre Netzwerkemulation eine weitaus günstigere und flexiblere Lösung.

## <a name="configure-network-emulation-for-your-test-settings"></a>Konfigurieren der Netzwerkemulation für die Testeinstellungen
 Bevor Sie die Schritte in diesem Verfahren ausführen, müssen Sie die Testeinstellungen in Visual Studio öffnen und dann die Seite **Daten und Diagnose** auswählen.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>So konfigurieren Sie die Netzwerkemulation für die Testeinstellungen

1.  Wählen Sie die Rolle aus, die für das Emulieren eines bestimmten Netzwerks verwendet werden soll.

    > [!NOTE]
    > Sie müssen den Netzwerkemulationsadapter nur entweder für die Clientrolle oder die Serverrolle konfigurieren. Sie müssen den Adapter nicht bei beiden Rollen verwenden. Der Adapter emuliert Netzwerkrauschen, das sich auf die Kommunikation zwischen beiden Rollen auswirkt. Daher muss der Adapter nicht bei beiden Rollen verwendet werden. Sofern dies nicht notwendig ist, sollten Sie eine Clientrolle für den Netzwerkemulationsadapter auswählen, um Mehraufwand bei der Serverrolle zu vermeiden.

2.  Klicken Sie auf **Netzwerkemulation** und dann auf **Konfigurieren**.

     Das Dialogfeld zum Konfigurieren der Netzwerkemulation wird angezeigt.

3.  Klicken Sie auf den Pfeil neben **Zu verwendendes Netzwerkprofil auswählen**, und wählen Sie den Netzwerktyp aus, den Sie beim Ausführen eines Tests emulieren möchten (z.B. **Kabel/DSL mit 768 KBit/s**).

    > [!WARNING]
    > Wenn Sie die Tests auf einem realen Netzwerk ausführen, das langsamer ist als das Netzwerk, das Sie emulieren, wird der Test mit der langsameren Netzwerkgeschwindigkeit ausgeführt. Die Emulation kann die Netzwerkumgebung nur verlangsamen, sie jedoch nicht schneller machen.

4.  Wenn Sie den Adapter für diagnostische Daten für die Netzwerkemulation in die Testeinstellungen einschließen und beabsichtigen, den Adapter auf dem lokalen Computer zu verwenden, müssen Sie auch den Netzwerkemulationstreiber an einen Netzwerkadapter des Computers binden. Der Netzwerkemulationstreiber ist erforderlich, damit der Adapter für diagnostische Daten für die Netzwerkemulation funktioniert. Sie haben zwei Möglichkeiten, den Netzwerkemulationstreiber zu installieren und an den Adapter zu binden:

    -   **Installation des Netzwerkemulationstreibers mit Microsoft Visual Studio Test Agent:** Microsoft Visual Studio Test Agent kann sowohl auf Remotecomputern als auch auf dem lokalen Computer verwendet werden. Wenn Sie Visual Studio Test Agent installieren, schließt der Installationsvorgang einen Konfigurationsschritt ein, bei dem der Netzwerkemulationstreiber an die Netzwerkkarte gebunden wird. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).

    -   **Installation des Netzwerkemulationstreibers mit Microsoft Visual Studio Test Professional:** Wenn Sie die Netzwerkemulation zum ersten Mal verwenden, werden Sie aufgefordert, den Netzwerkemulationstreiber an eine Netzwerkkarte zu binden.

    > [!TIP]
    > Sie können den Netzwerkemulationstreiber auch über die Befehlszeile auf dem lokalen Computer installieren, ohne Visual Studio Test Agent zu installieren. Verwenden Sie hierzu folgenden Befehl: **VSTestConfig NETWORKEMULATION /install**.

## <a name="see-also"></a>Siehe auch

- [Collect Diagnostic Information Using Test Settings (Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md)
- [Run manual tests (VSTS) (Ausführen manueller Tests (VSTS))](/vsts/manual-test/getting-started/run-manual-tests)