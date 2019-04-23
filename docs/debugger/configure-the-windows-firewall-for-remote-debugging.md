---
title: Windows-Firewall für Remotedebuggen konfigurieren | Microsoft-Dokumentation
ms.date: 10/31/2018
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff64735e1711a18bd7c55c6e052fa8579bd12e16
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100357"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Windows-Firewall für Remotedebuggen konfigurieren

In einem Netzwerk, das von der Windows-Firewall geschützt muss die Firewall zum Zulassen von remote-Debuggen konfiguriert werden. Visual Studio und der remote-debugging-Tools testen, um die entsprechenden Firewallports zu öffnen, während der Installation oder beim Start, aber Sie müssen auch Ports öffnen oder manuell apps zulassen.

In diesem Thema wird beschrieben, wie zum Konfigurieren der Windows-Firewall zum Aktivieren des Remotedebuggens auf Windows 10, 8/8.1 und 7 werden; und WindowsServer 2012 R2, 2012 und 2008 R2-Computer. Der Visual Studio und dem Remotecomputer nicht das gleiche Betriebssystem ausgeführt werden müssen. Zum Beispiel kann auf dem Visual Studio-Computer Windows 10 und auf dem Remotecomputer Windows Server 2012 R2 ausgeführt werden.

>[!NOTE]
>Die Anweisungen zum Konfigurieren der Windows-Firewall unterscheiden sich geringfügig unter verschiedenen Betriebssystemen und für ältere Versionen von Windows. Einstellungen für Windows 8/8.1, Windows 10 und Windows Server 2012 verwenden, das Wort *app*, während Windows 7 und Windows Server 2008, das Wort verwenden *Programm*.

## <a name="configure-ports-for-remote-debugging"></a>Konfigurieren von Ports für das Remotedebuggen

Visual Studio und den Remotedebugger versuchen Sie die richtigen Ports während der Installation oder beim Start zu öffnen. In einigen Szenarien, z. B. eine Drittanbieter-Firewall, müssen Sie jedoch, Ports manuell öffnen.

**Zum Öffnen eines Ports:**

1. In Windows **starten** im Menü "," Suchen "und" Open **Windows-Firewall mit erweiterter Sicherheit**. Dies ist in Windows 10, **Windows Defender Firewall mit erweiterter Sicherheit**.

1. Wählen Sie für einen neuen eingehenden Port, **Eingangsregeln** und wählen Sie dann **neue Regel**. Wählen Sie für eine ausgehende Regel **Ausgangsregeln** stattdessen.

1. In der **Assistenten für neue eingehende Regel**Option **Port**, und wählen Sie dann **Weiter**.

1. Wählen Sie entweder **TCP** oder **UDP**, je nachdem, auf die Portnummer in den folgenden Tabellen.

1. Klicken Sie unter **bestimmte lokale Ports**, geben Sie eine Portnummer aus den folgenden Tabellen aus, und wählen **Weiter**.

1. Wählen Sie **Verbindung zulassen,**, und wählen Sie dann **Weiter**.

1. Wählen Sie eine oder mehrere Netzwerktypen aktiviert werden, einschließlich des Netzwerktyps für die remote-Verbindung, und wählen Sie dann **Weiter**.

1. Fügen Sie einen Namen für die Regel (z. B. **"msvsmon"**, **IIS**, oder **Web Deploy**), und wählen Sie dann **Fertig stellen**.

   Die neue Regel sollte angezeigt werden und ausgewählt werden, der **Eingangsregeln** oder **ausgehende Regeln** Liste.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Ports auf dem Remotecomputer, die das Remotedebuggen ermöglichen

Für das Remotedebuggen, müssen die folgenden Ports auf dem Remotecomputer geöffnet sein:

::: moniker range="vs-2017"

|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|
|-|-|-|-|
|4022|Eingehend|TCP|Für VS 2017. Der Port Number Schritten durch 2 für jede Visual Studio-Version. Weitere Informationen finden Sie unter [Visual Studio remote debugger port assignments (Visual Studio-Remotedebugger – Portzuweisungen)](../debugger/remote-debugger-port-assignments.md).|
|4023|Eingehend|TCP|Für VS 2017. Der Port Number Schritten durch 2 für jede Visual Studio-Version. Dieser Port wird nur verwendet, um remote Debuggen von 64-Bit-Version des Remotedebuggers eine 32-Bit-Prozess. Weitere Informationen finden Sie unter [Visual Studio remote debugger port assignments (Visual Studio-Remotedebugger – Portzuweisungen)](../debugger/remote-debugger-port-assignments.md).|
|3702|Ausgehend|UDP|(Optional) Erforderlich für die remotedebuggerermittlung.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|
|-|-|-|-|
|4024|Eingehend|TCP|Für VS 2019. Der Port Number Schritten durch 2 für jede Visual Studio-Version. Weitere Informationen finden Sie unter [Visual Studio remote debugger port assignments (Visual Studio-Remotedebugger – Portzuweisungen)](../debugger/remote-debugger-port-assignments.md).|
|4025|Eingehend|TCP|Für VS 2019. Der Port Number Schritten durch 2 für jede Visual Studio-Version. Dieser Port wird nur verwendet, um remote Debuggen von 64-Bit-Version des Remotedebuggers eine 32-Bit-Prozess. Weitere Informationen finden Sie unter [Visual Studio remote debugger port assignments (Visual Studio-Remotedebugger – Portzuweisungen)](../debugger/remote-debugger-port-assignments.md).|
|3702|Ausgehend|UDP|(Optional) Erforderlich für die remotedebuggerermittlung.|

::: moniker-end

Bei Auswahl von **verwalteten Kompatibilitätsmodus verwenden** unter **Tools** > **Optionen** > **Debuggen**öffnen Diese zusätzliche Remotedebugger-Ports. Debugger verwalteter Kompatibilitätsmodus ermöglicht eine Vorgängerversion, die Visual Studio 2010-Version des Debuggers.

|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|
|-|-|-|-|
|135, 139, 445|Ausgehend|TCP|Erforderlich.|
|137, 138|Ausgehend|UDP|Erforderlich.|

Wenn die Domänenrichtlinie die Netzwerkkommunikation über IPSec ausgeführt werden muss, müssen Sie auf der Visual Studio und dem Remotecomputer zusätzliche Ports öffnen. Öffnen Sie Port 80 auf dem Remotecomputer, um das Debuggen auf einem remote-IIS-Webserver.

|**Ports**|**Eingehend/Ausgehend**|**Protokoll**|**Beschreibung**|
|-|-|-|-|
|500, 4500|Ausgehend|UDP|Erforderlich, wenn die Domänenrichtlinie die Netzwerkkommunikation über IPSec vorschreibt.|
|80|Ausgehend|TCP|Erforderlich für das Webserverdebuggen.|

Um bestimmte apps über die Windows-Firewall zu ermöglichen, finden Sie unter [Konfigurieren des Remotedebuggings über Windows-Firewall](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Konfigurieren des Remotedebuggings über Windows-firewall

Sie können der remote-debugging-Tools auf dem Remotecomputer installieren, oder führen Sie sie aus einem freigegebenen Ordner. In beiden Fällen muss die Remotecomputer Firewall ordnungsgemäß konfiguriert werden.

Auf einem Remotecomputer befindet sind der remote-debugging-Tools in:

*\<Visual Studio-Installationsverzeichnis\>\\Common7\\IDE\\Remotedebugger\\\<X86*, *X64*, oder  *AppX*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Zulassen Sie, und konfigurieren Sie des Remotedebuggers über Windows-Firewall

1. In Windows **starten** im Menü "," Suchen "und" Open **Windows-Firewall**, oder **Windows Defender Firewall**.

1. Wählen Sie **eine app durch die Windows-Firewall zulassen**.

1. Wenn **Remotedebugger** oder **Visual Studio Remote Debugger** nicht angezeigt, unter **zugelassene apps und Features**Option **Ändern der Einstellungen**, und wählen Sie dann **andere app zulassen**.

1. Wenn die Remotedebugger app immer noch in aufgeführt ist die **fügen Sie eine app** wählen Sie im Dialogfeld **Durchsuchen**, und navigieren Sie zu  *\<Visual Studio-Installationsverzeichnis\> \\Common7\\IDE\\Remotedebugger\\\<X86*, *X64*, oder *Appx* \> , abhängig von der geeigneten Architektur für Ihre app. Wählen Sie *msvsmon.exe*, und wählen Sie dann **hinzufügen**.

1. In der **Apps** Liste der **Remotedebugger** , die Sie gerade hinzugefügt haben. Wählen Sie **Netzwerktypen**, und wählen Sie dann eine oder mehrere Netzwerktypen, einschließlich des Netzwerktyps für die Remoteverbindung.

1. Wählen Sie **hinzufügen**, und wählen Sie dann **OK**.

## <a name="troubleshooting"></a>Problembehandlung bei der remotedebugverbindung

Wenn Sie zu Ihrer app mit dem Remotedebugger Anfügen nicht möglich, stellen Sie sicher die remote Debuggen Firewall-Ports, Protokolle, Typen von Netzwerken und app-Einstellungen richtig sind.

- In der Windows **starten** Menüs, suchen und öffnen Sie **Windows-Firewall**, und wählen Sie **eine app durch die Windows-Firewall zulassen**. Stellen Sie sicher, dass **Remotedebugger** oder **Visual Studio Remote Debugger** wird in der **zugelassene apps und Features** Liste ein aktiviertes Kontrollkästchen, und die entsprechende Netzwerk-Typen sind ausgewählt. Wenn dies nicht der Fall ist, [fügen Sie die richtigen apps und Einstellungen](#configure-remote-debugging-through-windows-firewall).

- In der Windows **starten** im Menü "," Suchen "und" Open **Windows-Firewall mit erweiterter Sicherheit**. Stellen Sie sicher, dass **Remotedebugger** oder **Visual Studio Remote Debugger** wird unter **Eingangsregeln** (und optional **Ausgangsregeln**) mit einem grünen Häkchen, und dass sind alle Einstellungen richtig.

  - Zum Anzeigen oder ändern Sie die regeleinstellungen, Maustaste den **Remote Debugger** -app in der Liste aus und wählen Sie **Eigenschaften**. Verwenden der **Eigenschaften** Registerkarten zu aktivieren oder deaktivieren Sie die Regel, oder ändern zu portieren, Zahlen, Protokolle oder Netzwerktypen.
  - Wenn die Remotedebugger-app nicht, in der Liste der Regeln angezeigt wird [hinzufügen und konfigurieren Sie die richtigen Ports](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Siehe auch

- [Remotedebuggen](../debugger/remote-debugging.md)
- [Visual Studio-Remotedebugger-portzuweisungen](../debugger/remote-debugger-port-assignments.md)
