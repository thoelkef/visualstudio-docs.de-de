---
title: Remote-Debugging | Microsoft Docs
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301056"
---
# <a name="remote-debugging"></a>Remotedebugging
Sie können eine Visual Studio-Anwendung debuggen, die auf einem anderen Computer bereitgestellt wurde. Dazu verwenden Sie den Visual Studio Remote Debugger.

Ausführliche Anweisungen zum Remote-Debuggen finden Sie in diesen Themen.

|Szenario|Link|
|-|-|-|
|Azure App Service|[Snapshot-Debugger](../debugger/debug-live-azure-applications.md) oder [Remote-Debug-ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Azure VM|[Remotedebuggen von ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Debuggen einer Azure Service Fabric-Anwendung](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Remote-Debug-ASP.NET Core-](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) oder [Remote-Debug-ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# oder Visual Basic|[Remotedebuggen eines C#- oder Visual Basic-Projekts](../debugger/remote-debugging-csharp.md)|
|C++|[Remotedebuggen eines C++-Projekts](../debugger/remote-debugging-cpp.md)|
|Universelle Windows-Apps (UWP)|[Ausführen von UWP-Apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md) oder [Debuggen eines installierten App-Pakets](../debugger/debug-installed-app-package.md)|

Wenn Sie nur den Remote-Debugger herunterladen und installieren möchten und keine zusätzlichen Anweisungen für Ihr Szenario benötigen, führen Sie die Schritte in diesem Artikel aus.

## <a name="download-and-install-the-remote-tools"></a>Herunterladen und Installieren der Remotetools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>Anforderungen

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>(Optional) So führen Sie den Remotedebugger von einer Dateifreigabe aus aus

Sie können den Remotedebugger (*msvsmon.exe*) auf einem Computer finden, auf dem Visual Studio Community, Professional oder Enterprise bereits installiert ist. In einigen Szenarien ist es am einfachsten, Remotedebugging einzurichten, wenn der Remotedebugger (msvsmon.exe) von einer Dateifreigabe ausgeführt wird. Informationen zu Verwendungseinschränkungen finden Sie auf der Hilfeseite des Remotedebuggers **(Hilfe > Verwendung** im Remotedebugger).

1. Suchen Sie *msvsmon.exe* im Verzeichnis, das Ihrer Version von Visual Studio entspricht:

   ::: moniker range=">=vs-2019"

   *Programmdateien (x86) , Microsoft Visual Studio, 2019, Enterprise, Common7, IDE, Remote-Debugger, X86,msvsmon.exe*

   *Programmdateien (x86) , Microsoft Visual Studio, 2019, Enterprise, Common7, IDE, Remote-Debugger, X64,msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Programmdateien (x86) , Microsoft Visual Studio, 2017, Enterprise, Common7, IDE, Remote-Debugger, X86,msvsmon.exe*

   *Programmdateien (x86) , Microsoft Visual Studio, 2017, Enterprise, Common7, IDE, Remote-Debugger, X64,msvsmon.exe*

   ::: moniker-end

2. Geben Sie den **Ordner Remote-Debugger** auf dem Visual Studio-Computer frei.

3. Führen Sie auf dem Remotecomputer *msvsmon.exe* aus dem freigegebenen Ordner aus. Folgen Sie den [Einrichtungsanweisungen](#bkmk_setup).

> [!TIP]
> Informationen zur Befehlszeileninstallation und Befehlszeilenreferenz finden Sie ``msvsmon.exe /?`` auf der Hilfeseite für *msvsmon.exe,* indem Sie die Befehlszeile auf dem Computer eingeben, auf dem Visual Studio installiert ist (oder gehen Sie zu Hilfe > **Verwendung** im Remotedebugger).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Einrichten des Remotedebuggers

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a>Konfigurieren des Remotedebuggers
Sie können einige Aspekte der Konfiguration des Remotedebuggers ändern, nachdem Sie ihn zum ersten Mal gestartet haben.

- Wenn Sie Berechtigungen für andere Benutzer hinzufügen müssen, um eine Verbindung mit dem Remotedebugger herzustellen, wählen Sie **Extras > Berechtigungen**aus. Sie müssen Administratorrechte besitzen, um Berechtigungen zu gewähren oder zu verweigern.

     > [!IMPORTANT]
     > Sie können den Remotedebugger unter einem Benutzerkonto ausführen, das sich von dem Benutzerkonto unterscheidet, das Sie auf dem Visual Studio-Computer verwenden.

     Alternativ können Sie den Remote-Debugger über die Befehlszeile mit dem Parameter **/allow \<username>** starten: **msvsmon \< username@computer /allow>**.

- Wenn Sie den Authentifizierungsmodus oder die Portnummer ändern oder einen Timeoutwert für die Remotetools angeben müssen: Wählen Sie **Tools > Options**.

     Eine Liste der standardmäßig verwendeten Portnummern finden Sie unter [Remote-Debugger-Portzuweisungen](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Sie haben die Möglichkeit, die Remotetools im Modus "Keine Authentifizierung" auszuführen, hiervon wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie den Modus „Ohne Authentifizierung“ nur aus, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>(Optional) Konfigurieren des Remotedebuggers als Dienst
Zum Debuggen in ASP.NET und anderen Serverumgebungen müssen Sie entweder den Remotedebugger als Administrator ausführen oder, wenn Sie möchten, dass er immer ausgeführt wird, den Remotedebugger als Dienst ausführen.

 Wenn Sie den Remotedebugger als Dienst konfigurieren möchten, führen Sie die folgenden Schritte aus.

1. Suchen Sie den **Konfigurations-Assistenten für Remote Debugger** (rdbgwiz.exe). (Dies ist eine separate Anwendung vom Remotedebugger.) Sie ist nur verfügbar, wenn Sie die Remotetools installieren. und wird nicht mit Visual Studio installiert.

2. Starten Sie den Konfigurations-Assistenten. Wenn die erste Seite angezeigt wird, klicken Sie auf **Weiter**.

3. Aktivieren Sie das Kontrollkästchen **Visual Studio 2015 Remote Debugger als Dienst ausführen** .

4. Fügen Sie den Namen des Benutzerkontos und das Kennwort hinzu.

    Möglicherweise müssen Sie diesem Konto das **Benutzerrecht "Anmelden als Dienstbenutzer"** hinzufügen **(Lokale Sicherheitsrichtlinie** (secpol.msc) auf der Startseite oder im **Startfenster** suchen (oder **secpol** an einer Eingabeaufforderung eingeben). Wenn das Fenster angezeigt wird, doppelklicken Sie auf **Zuweisen von Benutzerrechten**, und suchen Sie dann **Anmelden als Dienst** im rechten Bereich. Doppelklicken Sie darauf. Fügen Sie das Benutzerkonto zum Fenster **Eigenschaften** hinzu, und klicken Sie auf **OK**. Klicken Sie auf **Weiter**.

5. Wählen Sie den Typ des Netzwerks aus, über das die Remotetools kommunizieren sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, sollten Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, sollten Sie das zweite bzw. dritte Element auswählen. Klicken Sie auf **Weiter**.

6. Wenn der Dienst gestartet werden kann, wird **Der Konfigurations-Assistent für Visual Studio Remote Debugger wurde erfolgreich abgeschlossen**angezeigt. Wenn der Dienst nicht gestartet werden kann, wird **Fehler beim Abschließen des Assistenten zum Konfigurieren von Visual Studio Remote Debugger**angezeigt. Die Seite bietet auch Tipps, wie Sie den Dienst ans Laufen bringen können.

7. Klicken Sie auf **Fertig stellen**.

   An diesem Punkt wird der Remotedebugger als Dienst ausgeführt. Sie können dies überprüfen, indem Sie zu **Systemsteuerung > Dienste** navigieren und nach **Visual Studio 2015 Remote Debugger** suchen.

   Sie können den Remotedebugger-Dienst über **Systemsteuerung > Dienste** beenden und starten.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggens mit Remotesymbolen

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Weitere Informationen

- [Erster Blick auf den Debugger](../debugger/debugger-feature-tour.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remote-Debugging ASP.NET Core auf einem Remote-IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Remote Debugging Errors and Troubleshooting (Remotedebuggen – Fehler und Problembehandlung)](../debugger/remote-debugging-errors-and-troubleshooting.md)