---
title: Debuggen eines installierten UWP-App-Pakets | Microsoft-Dokumentation
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
ms.openlocfilehash: d5c2e94e9fa80145489bddfb005b7136bdff8a71
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211288"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Debuggen eines installierten UWP-App-Pakets in Visual Studio

Visual Studio kann installierte universelle Windows-Plattform (UWP)-app-Pakete auf Windows 10-Computern und Xbox-, hololens-und IOT-Geräten Debuggen.

>[!NOTE]
>Das Visual Studio-Debuggen für installierte UWP-apps wird auf Smartphones nicht unterstützt.

Weitere Informationen zum Debuggen von UWP-apps finden Sie in den Blogbeiträgen zum [Debuggen installierter App-Pakete](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) und zum entwickeln [universeller Windows-Apps (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Debuggen einer installierten UWP-App auf einem lokalen Computer

1. **Wählen Sie** > in Visual Studio die Option**andere debugziele** > Debuggen**installiertes App-Paket**

1. Wählen Sie im Dialogfeld **installiertes App-Paket Debuggen** unter **Verbindungstyp**die Option **lokaler Computer**.

1. Wählen Sie unter **installierte App-Pakete**die APP aus, die Sie debuggen möchten, oder geben Sie den Namen in das Suchfeld ein. Nicht ausgeführt installierte App-Pakete werden unter **nicht ausgeführt**angezeigt, und die Ausführung von apps wird derzeit **ausgeführt**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Ändern Sie ggf. den Codetyp unter **Debuggen Sie diesen Codetyp**, und wählen Sie andere Optionen aus.
   - Wählen Sie **eigenen Code nicht starten, sondern Debuggen, wenn er** mit dem Debuggen beginnt, wenn die APP gestartet wird. Das Starten des Debuggens beim Starten der APP ist eine effektive Möglichkeit zum Debuggen von Steuerungs Pfaden von [verschiedenen Startmethoden](/windows/uwp/xbox-apps/automate-launching-uwp-apps), z. b. die Protokoll Aktivierung mit benutzerdefinierten

1. Wählen Sie **Start**aus, oder klicken Sie auf **Anfügen**, wenn die app ausgeführt wird.

> [!NOTE]
> Sie können auch an alle laufenden UWP-oder anderen APP-Prozesse anfügen, indem Sie in Visual Studio **Debuggen** > **an den Prozess anhängen** auswählen. Das ursprüngliche Visual Studio-Projekt muss nicht an einen laufenden Prozess angefügt werden, aber das Laden der APP-Symbole hilft beim Debuggen eines Prozesses, für den Sie nicht über den ursprünglichen Code verfügen, erheblich. Weitere Informationen finden Sie [unter Angeben von Symbol-und Quelldateien im Debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="remote"></a>Debuggen einer installierten UWP-App auf einem Remote Computer oder-Gerät

Wenn Visual Studio zum ersten Mal eine installierte UWP-App auf einem Windows 10-Gerät oder auf einem Remote Computer mit Windows 10-Update eines Remote Erstellers debuggt, werden die remotedebuggingtools auf dem Zielgerät installiert.

1. [Aktivieren Sie den Entwicklermodus](/windows/uwp/get-started/enable-your-device-for-development) auf dem Visual Studio-Computer und dem Remote Gerät oder-Computer.

1. Wenn Sie eine Verbindung mit einem Remote Computer herstellen, auf dem das Windows 10-Update vor dem Ersteller ausgeführt wird, [Installieren und starten Sie den Remote Debugger manuell](../debugger/remote-debugging.md) auf dem Remote Computer.

1. **Wählen Sie** > auf dem Visual Studio-Computer die Option**andere debugziele** > Debuggen**installiertes App-Paket**

1. Wählen Sie im Dialogfeld **installiertes App-Paket Debuggen** unter **Verbindungstyp**die Option **Remote Computer** oder **Gerät**.

   Wenn Sie das **Gerät**auswählen, muss der Computer physisch mit einem Windows 10-Gerät verbunden sein.

   Wenn die Computer Adresse neben **Address**nicht angezeigt wird, wählen Sie für einen Remote Computer die Option **ändern**aus.

   1. Geben Sie im Dialogfeld **Remote Verbindung** neben **Adresse**den Namen oder die IP-Adresse des Computers ein, mit dem Sie eine Verbindung herstellen möchten.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Wenn der Debugger nicht mithilfe des Computer namens eine Verbindung mit einem Remote Computer herstellen kann, verwenden Sie stattdessen die IP-Adresse. Verwenden Sie die IP-Adresse für Xbox-, hololens-oder IOT-Geräte.
   1. Wählen Sie eine Authentifizierungs Option neben dem **Authentifizierungsmodus**aus.

      Behalten Sie für die meisten apps den Standardwert **Universal (unverschlüsseltes Protokoll)** bei.
   1. Wählen Sie **auswählen**aus.

1. Wählen Sie unter **installierte App-Pakete**die APP aus, die Sie debuggen möchten, oder geben Sie den Namen in das Suchfeld ein. Nicht ausgeführt installierte App-Pakete werden unter **nicht ausgeführt**angezeigt, und die Ausführung von apps wird derzeit **ausgeführt**.

1. Ändern Sie ggf. den Codetyp unter **Debuggen Sie diesen Codetyp**, und wählen Sie andere Optionen aus.
   - Wählen Sie **eigenen Code nicht starten, sondern Debuggen, wenn er** mit dem Debuggen beginnt, wenn die APP gestartet wird. Das Starten des Debuggens beim Starten der APP ist eine effektive Möglichkeit zum Debuggen von Steuerungs Pfaden von [verschiedenen Startmethoden](/windows/uwp/xbox-apps/automate-launching-uwp-apps), z. b. die Protokoll Aktivierung mit benutzerdefinierten

1. Wählen Sie **Start**aus, oder klicken Sie auf **Anfügen**, wenn die app ausgeführt wird.

Wenn Sie zum ersten Mal mit dem Debuggen eines installierten App-Pakets auf einem verbundenen Xbox-, hololens-oder IOT-Gerät beginnen, installiert Visual Studio die richtige Version des Remote Debuggers für das Zielgerät. Die Installation des Remote Debuggers kann einige Zeit in Anspruch nehmen, und die Meldung "der **Remote Debugger wird gestartet** " wird angezeigt.

>[!NOTE]
>Derzeit startet ein Xbox-oder hololens-Gerät die APP mit dem angefügten Debugger neu, wenn Sie bereits ausgeführt wurde.

Weitere Informationen zur Remote Bereitstellung von UWP-apps finden Sie unter Bereitstellen [und Debuggen von UWP-apps](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) und [Debuggen von UWP-apps auf Remote](run-windows-store-apps-on-a-remote-machine.md)

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Remotedebuggen](../debugger/remote-debugging.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)