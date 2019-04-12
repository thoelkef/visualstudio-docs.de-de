---
title: Debuggen ein installierten UWP-app-Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/07/2018
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 4bf9306ea1604d032ce9f4436759b11c4d17c343
ms.sourcegitcommit: 7eb85d296146186e7a39a17f628866817858ffb0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59504340"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Debuggen eines installierten UWP-app-Pakets in Visual Studio

Installierte app-Pakete mit universellen Windows-Plattform (UWP) auf Windows 10-Computern und Xbox, HoloLens und IoT-Geräte können von Visual Studio debuggen.

>[!NOTE]
>Visual Studio-debugging für installierten UWP-apps wird auf Smartphones nicht unterstützt.

Weitere Informationen zum Debuggen von UWP-apps finden Sie in den Blogbeiträgen auf [Debuggen die app-Pakete installiert](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) und [Erstellen universeller Windows-Apps (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Debuggen einer installierten UWP-app auf einem lokalen Computer

1. Wählen Sie in Visual Studio **Debuggen** > **andere Debugziele** > **Debuggen Installed App Package**.

1. In der **Debuggen Installed App Package** Dialogfeld unter **Verbindungstyp**Option **lokalen Computer**.

1. Klicken Sie unter **installierte App-Pakete**, wählen Sie die app, die Sie debuggen möchten, oder geben Sie seinen Namen in das Suchfeld. Nicht ausgeführte app-Pakete installiert werden, unter **nicht ausgeführt.**, und das Ausführen von apps befinden sich unter **ausführen**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Ändern Sie bei Bedarf den Codetyp unter **diesen Codetyp Debuggen**, und wählen Sie andere Optionen.
   - Wählen Sie **nicht starten sondern Debuggen meinen Code** So debuggen Sie die app gestartet wird. Starten des Debuggens die beim Starten der app ist eine effektive Möglichkeit zum Debuggen von Steuerelementpfade von [Methoden zum Starten der verschiedenen](/windows/uwp/xbox-apps/automate-launching-uwp-apps), z.B. die protokollaktivierung mit benutzerdefinierten Parametern.

1. Wählen Sie **starten**, oder wenn die app ausgeführt wird, wählen Sie **Anfügen**.

> [!NOTE]
> Sie können auch alle ausgeführten UWP oder andere app-Prozess anfügen, indem Sie auswählen **Debuggen** > **an den Prozess anhängen** in Visual Studio. Ist nicht erforderlich, den ursprüngliche Visual Studio-Projekt an einen laufenden Prozess anfügen, aber der app-Symbole werden geladen erheblich helfen wird, wenn Sie einen Prozess zu debuggen, dem Sie nicht über den ursprünglichen Code verfügen. Finden Sie unter [angeben von Symbol-und Quelldateien im Debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="remote"></a> Debuggen einer installierten UWP-app auf einem Remotecomputer oder-Gerät

Beim ersten Visual Studio mit eine installierte UWP-app auf einem Windows 10-Gerät oder eine remote-Ersteller des Postings des aktualisieren Sie Windows 10-Computer, debuggt wird es der remote-debugging-Tools auf dem Zielgerät installiert.

1. [Aktivieren Sie den Entwicklermodus](/windows/uwp/get-started/enable-your-device-for-development) auf Visual Studio-Computer und Geräte oder Computer.

1. Wenn Sie die Verbindung mit einem Remotecomputer unter Prä-Creator Update Windows 10, herstellen [manuell installieren und starten Sie den Remotedebugger](../debugger/remote-debugging.md) auf dem Remotecomputer.

1. Wählen Sie auf dem Visual Studio-Computer **Debuggen** > **andere Debugziele** > **Debuggen Installed App Package**.

1. In der **Debuggen Installed App Package** Dialogfeld unter **Verbindungstyp**Option **Remotecomputer** oder **Gerät**.

   Bei Auswahl von **Gerät**, Ihr Computer muss Windows 10-Gerät physisch verbunden sein.

   Für einen Remotecomputer, wenn die Adresse des Computers nicht neben angezeigt wird **Adresse**Option **Änderung**.

   1. In der **Remoteverbindung** Dialogfeld neben **Adresse**, geben Sie den Namen oder die IP-Adresse des Computers, um eine Verbindung herstellen möchten.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Wenn der Debugger kann nicht mit einem Remotecomputer mit den Namen des Computers verbunden sind, verwenden Sie stattdessen die IP-Adresse. Verwenden Sie die IP-Adresse für Xbox, HoloLens und IoT-Geräte.
   1. Wählen Sie eine Authentifizierungsoption neben **Authentifizierungsmodus**.

      Behalten Sie den Standardwert für die meisten apps **universell (unverschlüsseltes Protokoll)**.
   1. Wählen Sie **wählen**.

1. Klicken Sie unter **installierte App-Pakete**, wählen Sie die app, die Sie debuggen möchten, oder geben Sie seinen Namen in das Suchfeld. Nicht ausgeführte app-Pakete installiert werden, unter **nicht ausgeführt.**, und das Ausführen von apps befinden sich unter **ausführen**.

1. Ändern Sie bei Bedarf den Codetyp unter **diesen Codetyp Debuggen**, und wählen Sie andere Optionen.
   - Wählen Sie **nicht starten sondern Debuggen meinen Code** So debuggen Sie die app gestartet wird. Starten des Debuggens die beim Starten der app ist eine effektive Möglichkeit zum Debuggen von Steuerelementpfade von [Methoden zum Starten der verschiedenen](/windows/uwp/xbox-apps/automate-launching-uwp-apps), z.B. die protokollaktivierung mit benutzerdefinierten Parametern.

1. Wählen Sie **starten**, oder wenn die app ausgeführt wird, wählen Sie **Anfügen**.

Wenn Sie das Debuggen eines installierten app-Pakets auf einem verbundenen Xbox, HoloLens und IoT-Gerät zum ersten Mal starten, installiert Visual Studio die richtige Version des Remotedebuggers für das Zielgerät. Installieren des Remotedebuggers dauert einige Zeit, und die Nachricht **Remotedebugger wird gestartet** zeigt an, während diese durchgeführt wird.

>[!NOTE]
>Derzeit ein Xbox oder HoloLens-Gerät die app neu gestartet mit dem Debugger angefügt wird, wenn er bereits ausgeführt wurde.

Weitere Informationen zu Remotebereitstellung von UWP-apps, finden Sie unter [bereitstellen und Debuggen von UWP-apps](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) und [Debuggen von UWP-apps auf Remotecomputern](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Remotedebuggen](../debugger/remote-debugging.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)