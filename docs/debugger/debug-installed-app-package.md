---
title: Debuggen eines installierten app-Pakets (UWP) | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 3bb858f2ee20eb65c09dd4979f2bbba1470cbe0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908241"
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Debuggen eines installierten app-Pakets in Visual Studio (UWP)

Sie können alle installierten app-Paket debuggen, indem Sie auf **Debuggen > andere Debugziele > Debuggen Installed App Package**. Diese Methode Debuggen ist für die universelle Windows-Apps (UWP) auf diesen Geräten verfügbar:

* Windows 10 (auf Smartphones nicht unterstützt)
* XBox
* HoloLens
* Internet der Dinge

Weitere Informationen zu diesen Funktionen finden Sie im Blogbeitrag zu Updates für [Debuggen die app-Pakete installiert](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) und dem Beitrag auf [Erstellen universeller Windows-Apps (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Debuggen Sie ein installiertes App-Paket oder der ausgeführten App auf einem lokalen Computer oder Gerät

1. Ihr UWP-Projekt in Visual Studio geöffnet, und klicken Sie auf **Debuggen > andere Debugziele > Debuggen Installed App Package**.

2. Wählen Sie entweder **lokalen Computer** oder **Gerät**.

     Auf Wunsch **Gerät**, Ihr Computer muss Windows 10-Gerät physisch verbunden sein.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     Ausgeführten app-Pakete angezeigt wird, klicken Sie unter installiert die **ausführen** Knoten. Installierte app-Pakete, die anzeigen unter ausgeführt wird, werden nicht **nicht ausgeführt**.

3. Wählen Sie den Namen der app zu Debuggen unter **ausführen** oder **nicht ausgeführt.** , und wählen Sie **starten** oder, wenn die app bereits ausgeführt wird, wählen Sie **Anfügen**.

     Bei Auswahl von **nicht starten sondern Debuggen meinen Code**, dies führt dazu, dass Visual Studio-Debugger an Ihre app anfügen, wenn Sie dieses benutzerdefinierte gleichzeitig öffnen. Dies ist ein effektives Verfahren zum Debuggen von Steuerelementpfade von [Methoden zum Starten der verschiedenen](/windows/uwp/xbox-apps/automate-launching-uwp-apps), z.B. die protokollaktivierung mit benutzerdefinierten Parametern.

> [!NOTE]
> Visual Studio kann auch an jeden laufenden Prozess der UWP-app anfügen, indem Sie die Auswahl **Debuggen**, und klicken Sie dann **an den Prozess anhängen**. Anfügen an einen laufenden Prozess benötigt keine ursprünglichen Visual Studio-Projekts, jedoch des Prozesses Symbole laden erheblich helfen, wenn Sie einen Prozess zu debuggen, dem Sie nicht über den ursprünglichen Code verfügen.
  
## <a name="remote"></a> Debuggen einer App installierten oder ausgeführten, auf einem Remotecomputer 

Beim Debuggen eines installierten app-Pakets auf einem Remotecomputer zum ersten Mal installiert Visual Studio die richtige Version der Remotetools für das Zielgerät. Das Zielgerät muss ein Windows 10-Computer, XBox, HoloLens und IoT-Gerät.

1. Aktivieren Sie auf Ihrem Windows 10-Gerät [Entwicklermodus](/windows/uwp/get-started/enable-your-device-for-development).

2. Wenn Sie mit einem remote-PC vor creators Update-Version von Windows 10, zunächst manuell ausführen verbinden [installieren und starten Sie den Remotedebugger](../debugger/remote-debugging.md).

     Für ein XBox, HoloLens und IoT-Gerät und Windows-Geräte mit Windows 10 creators Update müssen Sie den Remotedebugger manuell zu installieren. Der Remoteserver-Verwaltungstools werden automatisch installiert, wenn Sie die app bereitstellen.

3. Klicken Sie auf **Debuggen > andere Debugziele > Stalliertes App-Paket**.

4. Wählen Sie in der ersten Dropdown-Liste **Remotecomputer**.

5. Geben Sie den Namen oder die IP-Adresse des Computers ein, die Sie zuordnen möchten.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Wenn Sie anfügen können nicht mit Computernamen (nach der Auswahl **starten**), verwenden Sie stattdessen die IP-Adresse. Verwenden Sie die IP-Adresse für XBox, HoloLens und IoT-Geräte.

6. Auswählen der Methode zum Authentifizieren, indem Sie eine Option in **Authentifizierungsmodus**.

    Behalten Sie den Standardwert für die meisten apps **universell (unverschlüsseltes Protokoll)**.

7. Wählen Sie den Namen der app zu Debuggen unter **ausführen** oder **nicht ausgeführt.** , und wählen Sie **starten** oder (bei Ausführung von apps) **Anfügen**.

     Bei Auswahl von **nicht starten sondern Debuggen meinen Code**, dies führt dazu, dass Visual Studio-Debugger an Ihre app-Paket angefügt werden soll, wenn Sie sie zu einem benutzerdefinierten Zeitpunkt starten. Dies ist ein effektives Verfahren zum Debuggen von Steuerelementpfade von [Methoden zum Starten der verschiedenen](/windows/uwp/xbox-apps/automate-launching-uwp-apps), z.B. die protokollaktivierung mit benutzerdefinierten Parametern.

     Beim Debuggen eines installierten app-Pakets auf einem verbundenen XBox, HoloLens und IoT-Gerät zum ersten Mal installiert Visual Studio die richtige Version des Remotedebuggers für das Zielgerät. Dieser Vorgang kann etwas Zeit dauern, und Sie sehen eine Meldung ``Starting remote debugger`` während dies passiert.

     > [!NOTE]
   > Klicken Sie am vorhanden ist, einer XBox oder HoloLens-Gerät wird ein Neustart der app mit dem Debugger angefügt, wenn er bereits ausgeführt wird.

Weitere Informationen zu erweiterten Optionen für die Remotebereitstellung von UWP-apps finden Sie unter [bereitstellen und Debuggen von UWP apps]((/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options). 
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)  
 [Remote Debugging](../debugger/remote-debugging.md)  
 [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Remotedebugger - Portzuweisungen](../debugger/remote-debugger-port-assignments.md)  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)