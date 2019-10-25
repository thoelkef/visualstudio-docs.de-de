---
title: Bereitstellen von UWP-apps | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: d902403b111e92f302ff907a29eaaa99ee181058
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737987"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Bereitstellen von UWP-Apps aus Visual Studio

Mit der Visual Studio-Bereitstellungs Funktionalität werden UWP-apps, die mit Visual Studio erstellt wurden, auf einem Zielgerät erstellt und registriert. Wie genau die App registriert wird, hängt davon ob, ob sich das Zielgerät lokal oder remote befindet:

- Handelt es sich bei dem Ziel um einen lokalen Visual Studio-Computer, registriert Visual Studio die App vom Erstellungsordner aus.

- Handelt es sich bei dem Ziel um ein Remotegerät, kopiert Visual Studio die erforderlichen Dateien auf den Remotecomputer und registriert anschließend die App auf dem Gerät.

Die Bereitstellung erfolgt automatisch, wenn Sie die App von Visual Studio aus mit der Option **Debuggen starten** (Tastatur: F5) oder der Option **Starten ohne Debuggen** (Tastatur: STRG + F5) debuggen. Sie können die App auch manuell bereitstellen. Die manuelle Bereitstellung ist in folgenden Szenarios nützlich:

- Ad-Hoc-Tests auf einem lokalen oder Remotecomputer.

- Bereitstellen einer App, die eine andere App startet, welche Sie debuggen möchten.

- Bereitstellen einer App, deren Debugging beim Start durch eine andere App oder Methode erfolgen soll.

## <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>Bereitstellen einer UWP-App
 Das manuelle Bereitstellen einer App ist ein einfacher Vorgang:

1. Wenn Sie ein Remotegerät bereitstellen, geben Sie den Namen oder die IP-Adresse des Geräts auf der Projekteigenschaftenseite des Startprojekts der App an. (Die entsprechenden Schritte sind weiter unten in diesem Thema aufgelistet.)

2. Wählen Sie auf der Debugger-Symbolleiste von Visual Studio das Bereitstellungsziel aus der Dropdownliste neben der Schaltfläche **Debuggen starten** aus.

     ![Auf lokalem Computer ausführen](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. Klicken Sie im Menü **Erstellen** auf **Bereitstellen**.

## <a name="BKMK_How_to_specify_a_remote_device"></a> Festlegen eines Remotegeräts

**Erforderliche Komponenten**

Auf einem Windows 10-Remote Gerät müssen Sie den [Entwicklermodus](/windows/uwp/get-started/enable-your-device-for-development)aktivieren. Auf Windows 10-Geräten, auf denen das Update von Creator oder höher ausgeführt wird, werden die Remote Tools automatisch installiert, wenn Sie die APP bereitstellen. Weitere Informationen finden Sie unter [Debuggen eines installierten App-Pakets](../debugger/debug-installed-app-package.md).

> [!NOTE]
> In den Update Versionen von Windows 10 vor dem Ersteller müssen die Remotetools für Visual Studio auf dem Remote Gerät installiert sein, und der Remote Debugger muss ausgeführt werden.

Bei der Bereitstellung wird der Remotedebugger-Netzwerkkanal verwendet, um die App-Dateien an das Remotegerät zu senden.

#### <a name="to-specify-a-remote-device"></a>So legen Sie ein Remotegerät fest

1. Geben Sie auf der Debugeigenschaftenseite für das Startprojekt den Namen oder die IP-Adresse des Remotebereitstellungsziels an.

2. Wählen Sie zum Öffnen der Debugeigenschaftenseite das Projekt im Projektmappen-Explorer aus, und klicken Sie dann im Kontextmenü auf **Eigenschaften** .

3. Wählen Sie dann den Knoten **Debuggen** im Eigenschaftenseitenfenster aus.

4. Wählen Sie für **Zielgerät**die Option **Remote Computer**aus.

5. Klicken Sie unter **Remote Computer**auf **Suchen**.

6. Sie können den Namen oder die IP-Adresse des Remote Geräts eingeben, oder Sie können das Gerät im Dialogfeld **Remote Verbindung** auswählen.

    ![Dialogfeld "remotedebuggerverbindung auswählen"](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    Im Dialogfeld **Remote Verbindung** werden die Geräte im Subnetz des lokalen Netzwerks und jedes Gerät angezeigt, das über ein Ethernet-Kabel direkt mit dem Visual Studio-Computer verbunden ist.

   **Angeben des Remote Geräts auf einer C++ Projektseite**

   ![C&#43; &#43; -Projekteigenschaften für Remote Debugging](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Wählen Sie **Remote Debugger** in der Liste **Zu startender Debugger** aus.

8. Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Computername** ein. Oder verwenden Sie den nach unten weisenden Pfeil im Feld, um das Gerät im Dialogfeld "Remotedebuggerverbindung auswählen" auszuwählen.

   **Angeben des Remotegeräts auf einer Visual C#- oder Visual Basic-Projektseite**

   ![Verwaltete Projekteigenschaften für Remote Debugging](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Wählen Sie in der Liste **Zielgerät** die Option **Remotecomputer** aus.

10. Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Remotecomputer** ein oder klicken Sie auf **Suchen** , um das Gerät im Dialogfeld **Remotedebuggerverbindung auswählen** auszuwählen.

## <a name="BKMK_Deployment_options"></a> Bereitstellungsoptionen

Sie können die folgenden Bereitstellungsoptionen auf der Debugeigenschaftenseite für das Startprojekt festlegen.

**Netzwerkloopback zulassen**

Aus Sicherheitsgründen ist eine UWP-oder [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-APP, die standardmäßig installiert wird, nicht berechtigt, Netzwerk Aufrufe an das Gerät vorzunehmen, auf dem Sie installiert ist. Standardmäßig wird durch die Visual Studio-Bereitstellung eine Ausnahme von dieser Regel für die bereitgestellte App erstellt. Diese Ausnahme ermöglicht das Testen von Kommunikationsverfahren auf einem einzelnen Computer. Bevor Sie die App an [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]senden, sollten Sie die App ohne die Ausnahme testen.

So entfernen Sie die Netzwerkloopbackausnahme aus der App:

- Deaktivieren Sie C# auf der Eigenschaften Seite für und Visual Basic Debuggen das Kontrollkästchen **Netzwerk Loop Back zulassen** .

- Legen Sie C++ auf der Eigenschaften Seite Debuggen den Wert **Netzwerk Loopback zulassen** auf **Nein**fest.

**Eigenen Code nicht starten, sondern Debuggen, wenn erC# gestartet wird (und Visual Basic)/C++Anwendung starten ()**

So konfigurieren Sie den automatischen Start einer Debugsitzung beim Starten der Anwendung für die Bereitstellung:

- Aktivieren Sie C# auf der Eigenschaften Seite für und Visual Basic Debuggen das Kontrollkästchen **eigenen Code beim Starten nicht starten, sondern Debuggen** .

- Legen Sie C++ auf der Eigenschaften Seite Debuggen den Wert für **Anwendung starten** auf **Ja**fest.

## <a name="see-also"></a>Siehe auch

- [Advanced remote deployment options (Erweiterte Optionen für die Remotebereitstellung)](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Debuggen eines installierten App-Pakets](../debugger/debug-installed-app-package.md)
- [Ausführen von Apps aus Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
