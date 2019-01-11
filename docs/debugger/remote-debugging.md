---
title: Remotedebuggen | Microsoft-Dokumentation
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84ba15ddbfdb6e3bbcf7a9f7c3ee3dd7e0f89c9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866334"
---
# <a name="remote-debugging"></a>Remote Debugging
Sie können eine Visual Studio-Anwendung debuggen, die auf einem anderen Computer bereitgestellt wurde. Dazu verwenden Sie den Visual Studio Remote Debugger.

Detaillierte Anweisungen zum Remotedebuggen finden Sie unter folgenden Themen.

|Szenario|Link|
|-|-|-|
|Azure App Service|[Snapshot-Debugger](../debugger/debug-live-azure-applications.md) oder [Remote Debuggen von ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Azure-VM|[Remotedebuggen von ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Debuggen einer Azure Service Fabric-Anwendung](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Remotedebuggen für ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) oder [Remotedebuggen von ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# oder Visual Basic|[Remotedebuggen eines C#- oder Visual Basic-Projekts](../debugger/remote-debugging-csharp.md)|
|C++|[Remotedebuggen eines C++-Projekts](../debugger/remote-debugging-cpp.md)|
|Universelle Windows-Apps (UWP)|[Ausführen von UWP-apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md) oder [Debuggen eines installierten app-Pakets](../debugger/debug-installed-app-package.md)|

Wenn Sie nur herunterladen und Installieren des Remotedebuggers möchten und alle zusätzlichen Anweisungen wird für Ihr Szenario nicht benötigt, führen Sie die Schritte in diesem Artikel.

## <a name="download-and-install-the-remote-tools"></a>Herunterladen und Installieren der Remotetools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements_msvsmon"></a> Anforderungen

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="fileshare_msvsmon"></a> (Optional) Zum Ausführen des Remotedebuggers aus einer Dateifreigabe

Sie finden den Remotedebugger (*msvsmon.exe*) auf einem Computer mit Visual Studio Community, Professional oder Enterprise bereits installiert. Die einfachste Möglichkeit zum Einrichten des Remotedebuggens werden für einige Szenarien führen Sie den Remotedebugger (msvsmon.exe) über eine Dateifreigabe. Einschränkungen bezüglich der, finden Sie den Remotedebugger-Hilfeseite (**Hilfe > Verwendung** in den Remotedebugger).

1. Suchen *msvsmon.exe* in das Verzeichnis, das Ihrer Version von Visual Studio entspricht. Für Visual Studio Enterprise 2017:

      *Programm Dateien (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

      *Programm Dateien (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

2. Freigabe der **Remotedebugger** Ordner auf dem Visual Studio-Computer.

3. Führen Sie auf dem Remotecomputer *msvsmon.exe* aus dem freigegebenen Ordner. Führen Sie die [Anweisungen zur Einrichtung des](#bkmk_setup).

> [!TIP]
> Installation über die Befehlszeile und Befehlszeilenreferenz-finden Sie auf die Hilfeseite für *msvsmon.exe* durch Eingabe ``msvsmon.exe /?`` in der Befehlszeile auf dem Computer mit Visual Studio installiert (oder wechseln Sie zu **Hilfe > Verwendung**in den Remotedebugger).

## <a name="bkmk_setup"></a>Einrichten des Remotedebuggers

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a>Konfigurieren des Remotedebuggers
Sie können einige Aspekte der Konfiguration des Remotedebuggers ändern, nachdem Sie ihn zum ersten Mal gestartet haben.

-   Wenn Sie zum Hinzufügen von Berechtigungen für andere Benutzer eine Verbindung mit dem Remotedebugger herstellen, wählen müssen **Extras > Berechtigungen**. Sie müssen Administratorrechte besitzen, um Berechtigungen zu gewähren oder zu verweigern.

     > [!IMPORTANT]
     > Sie können den Remotedebugger unter einem Benutzerkonto, das unterscheidet sich über das Benutzerkonto auf dem Visual Studio-Computer verwendeten ausführen, jedoch müssen Sie das andere Benutzerkonto die Berechtigungen des Remotedebuggers hinzufügen.

     Alternativ können Sie den Remotedebugger starten, über die Befehlszeile mit der **/ allow \<Benutzername >** Parameter: **Msvsmon / allow \< username@computer>**.

-   Wenn Sie den Authentifizierungsmodus oder die Portnummer ändern, oder geben Sie einen Timeoutwert für den Remoteserver-Verwaltungstools müssen: Wählen Sie **Tools > Optionen**.

     Eine Liste der standardmäßig verwendeten Portnummern, finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     >  Sie haben die Möglichkeit, die Remotetools im Modus "Keine Authentifizierung" auszuführen, hiervon wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie den Modus „Ohne Authentifizierung“ nur aus, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.

##  <a name="bkmk_configureService"></a> (Optional) Konfigurieren des Remotedebuggers als Dienst
Für das Debuggen in ASP.NET und anderen serverumgebungen, müssen Sie den Remotedebugger als Administrator ausführen oder, soll es immer ausgeführt, den den Remotedebugger als Dienst ausführen.

 Wenn Sie den Remotedebugger als Dienst konfigurieren möchten, gehen Sie wie folgt vor.

1. Suchen Sie den **Konfigurations-Assistenten für Remote Debugger** (rdbgwiz.exe). (Dies ist eine vom Remotedebugger getrennte Anwendung.) Der Konfigurations-Assistent steht nur zur Verfügung, wenn Sie die Remotetools installieren, und wird nicht mit Visual Studio installiert.

2. Starten Sie den Konfigurations-Assistenten. Wenn die erste Seite angezeigt wird, klicken Sie auf **Weiter**.

3. Aktivieren Sie das Kontrollkästchen **Visual Studio 2015 Remote Debugger als Dienst ausführen** .

4. Fügen Sie den Namen des Benutzerkontos und das Kennwort hinzu.

    Müssen Sie möglicherweise hinzufügen der **Anmelden als Dienst** Benutzer direkt auf dieses Konto (Suchen **Local Security Policy** (secpol.msc) in der **starten** Seite bzw. im Fenster (oder Typ  **"secpol"** an einer Eingabeaufforderung). Wenn das Fenster angezeigt wird, doppelklicken Sie auf **Zuweisen von Benutzerrechten**, und suchen Sie dann **Anmelden als Dienst** im rechten Bereich. Doppelklicken Sie darauf. Fügen Sie das Benutzerkonto zum Fenster **Eigenschaften** hinzu, und klicken Sie auf **OK**. Klicken Sie auf **Weiter**.

5. Wählen Sie den Typ des Netzwerks aus, über das die Remotetools kommunizieren sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, sollten Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, sollten Sie das zweite bzw. dritte Element auswählen. Klicken Sie auf **Weiter**.

6. Wenn der Dienst gestartet werden kann, wird **Der Konfigurations-Assistent für Visual Studio Remote Debugger wurde erfolgreich abgeschlossen**angezeigt. Wenn der Dienst nicht gestartet werden kann, wird **Fehler beim Abschließen des Assistenten zum Konfigurieren von Visual Studio Remote Debugger**angezeigt. Die Seite bietet auch Tipps, wie Sie den Dienst ans Laufen bringen können.

7. Klicken Sie auf **Fertig stellen**.

   An diesem Punkt wird der Remotedebugger als Dienst ausgeführt. Sie können dies überprüfen, indem Sie zu **Systemsteuerung > Dienste** navigieren und nach **Visual Studio 2015 Remote Debugger** suchen.

   Sie können den Remotedebugger-Dienst über **Systemsteuerung > Dienste** beenden und starten.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Siehe auch

- [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger - Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen von ASP.NET Core auf einem Remotecomputer mit IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)