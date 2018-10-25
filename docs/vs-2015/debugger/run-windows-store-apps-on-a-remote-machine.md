---
title: Führen Sie Windows Store-apps auf einem Remotecomputer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f031e81911c9a36cd2c48abf7bd2b092bb5940f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886278"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Ausführen von Windows Store-Apps auf einem Remotecomputer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bezieht sich nur auf Windows] (.. /Image/windows_only_content.png "Windows_only_content")  
  
 Mit der App "Visual Studio-Remotetools" können Sie eine auf einem Gerät ausgeführte Windows Store-App von einem zweiten Computer, auf dem Visual Studio ausgeführt wird, ausführen, debuggen, für die Profilerstellung verwenden und testen. Die Ausführung auf einem Remotegerät kann besonders dann effektiv sein, wenn der Visual Studio-Computer keine für Windows Store-Apps spezifischen Funktionalitäten wie Fingereingabe, Geolocation und physische Ausrichtung unterstützt. In diesem Thema wird beschrieben, wie Sie eine Remotesitzung konfigurieren und starten.  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 erfahren Sie:  
  
 [Erforderliche Komponenten](#BKMK_Prerequisites)  
  
 [Sicherheit](#BKMK_Security)  
  
 [Herstellen einer direkten Verbindung mit einem Remotegerät](#BKMK_DirectConnect)  
  
 [Installieren der Remotetools](#BKMK_Installing_the_Remote_Tools)  
  
 [Starten des Remotedebugmonitors](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Konfigurieren des Remotedebuggers](#BKMK_ConfigureRemoteDebugger)  
  
 [Konfigurieren des Visual Studio-Projekts für das Remotedebuggen](#BKMK_ConnectVS)  
  
- [Auswählen des Remotegeräts für C#- und Visual Basic-Projekte](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [Auswählen des Remotegeräts für JavaScript- und C++-Projekte](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [Ausführen einer Remotedebugsitzung](#BKMK_RunRemoteDebug)  
  
##  <a name="BKMK_Prerequisites"></a> Erforderliche Komponenten  
 So debuggen Sie auf einem Remotegerät:  
  
-   Das Remotegerät und der Visual Studio-Computer müssen über ein Netzwerk verbunden oder mit einem Ethernetkabel direkt verbunden werden. Das Debugging über das Internet wird nicht unterstützt.  
  
-   Die Lizenz eines Entwicklers muss auf dem Remotegerät installiert sein.  
  
-   Das Remotegerät muss die Remotedebugkomponenten ausführen.  
  
-   Sie müssen Administrator auf dem Remotegerät sein, um die Firewall während der Installation zu konfigurieren. Sie müssen Benutzerzugriff auf das Remotegerät haben, um die Verbindung mit dem Remotedebugger herstellen oder ihn ausführen zu können.  
  
##  <a name="BKMK_Security"></a> Sicherheit  
 Standardmäßig verwendet der Remotedebugger die Windows-Authentifizierung.  
  
> [!WARNING]
>  Sie haben außerdem die Möglichkeit, den Remotedebugger im Modus "Keine Authentifizierung" auszuführen, hiervon wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie den Modus "Ohne Authentifizierung" nur aus, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.  
  
##  <a name="BKMK_DirectConnect"></a> Herstellen einer direkten Verbindung mit einem Remotegerät  
 Um eine direkte Verbindung mit einem Remotegerät herzustellen, schließen Sie den Visual Studio-Computer mit einem Standardethernetkabel an das Gerät an. Wenn das Gerät keinen Ethernet-Anschluss besitzt, können Sie für die Verbindung mit dem Kabel einen USB-Ethernet-Adapter verwenden.  
  
##  <a name="BKMK_Installing_the_Remote_Tools"></a> Installieren der Remotetools  
  
> [!NOTE]
>  **Versionen und Updates**  
>   
>  Die **Remotetools für Visual Studio 2015** werden für frühere Versionen von Visual Studio nicht unterstützt.  
>   
>  Es wird empfohlen, die Updateversion der Remotetools für Visual Studio 2015 zu installieren, die der Updateversion Ihrer Visual Studio-Installation entspricht.  
>   
>  Der Visual Studio-Debugger ist mit einer beliebigen Kombination von Versionen von Visual Studio 2015 und den Remotetools für Visual Studio 2015 kompatibel. Für die neuesten Funktionen in Visual Studio sind jedoch sowohl Visual Studio als auch die Remotetools in der jeweils aktuellsten Version erforderlich.  
>   
>  Für andere Diagnosetools sind möglicherweise die gleichen Versionen der Remotetools und von Visual Studio erforderlich.  
  
 **Installieren der Remotedebugkomponenten auf einem Remotegerät**  
  
 Zum Ausführen oder speichern das Installationsprogramm für die Remotetools, wählen Sie einen der Links in dieser Tabelle, die Ihrer Version von Visual Studio entspricht:  
  
|Version|Link|Hinweise|
|-|-|-|
|Visual Studio 2015 Update 3|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Wenn Sie dazu aufgefordert werden, die kostenlose Visual Studio Dev Essentials-Gruppe beitreten, oder Sie können melden Sie sich ein gültiges Visual Studio-Abonnement. Klicken Sie dann erneut öffnen Sie den Link bei Bedarf. Immer herunterladen Sie die Version, die übereinstimmende Ihr Betriebssystems des Geräts (x 86, X64 oder ARM-Version)|
|Visual Studio 2015 (älter)|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Wenn Sie dazu aufgefordert werden, die kostenlose Visual Studio Dev Essentials-Gruppe beitreten, oder Sie können melden Sie sich ein gültiges Visual Studio-Abonnement. Klicken Sie dann erneut öffnen Sie den Link bei Bedarf. Immer herunterladen Sie die Version, die übereinstimmende Ihr Betriebssystems des Geräts (x 86, X64 oder ARM-Version)|
|Visual Studio 2013|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Download-Seite in Visual Studio 2013-Dokumentation|
  
 Sie können auswählen, das Installationsprogramm herunterzuladen, oder Sie können es direkt ausführen. Wenn Sie das Installationsprogramm ausführen, stimmen Sie den Bedingungen zu, und wählen Sie dann **Installieren**aus.  
  
 Standardmäßig werden die Remotedebugkomponenten im Ordner **C:\Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger** installiert.  
  
##  <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Starten des Remotedebugmonitors  
  
> [!NOTE]
>  Da der Remotedebugger die Firewall konfiguriert, um die Kommunikation mit dem Visual Studio-Host zu ermöglichen, müssen Sie Administrator auf dem Remotegerät sein, wenn Sie den Remotedebugger zum ersten Mal starten.  
  
 Nachdem Sie die Remotetools installiert haben, wählen Sie **Remote Debugger** auf dem Bildschirm **Start** aus. Beim ersten Start des Remotedebuggers wird das Dialogfeld **Konfiguration für Remotedebugging** angezeigt.  
  
 Im Dialogfeld **Konfiguration für Remotedebugging** :  
  
1.  Wenn die Windows-Webdienste-API nicht installiert ist, wählen Sie **Installieren**aus.  
  
2.  In der Gruppe **Windows-Firewall konfigurieren** wählen Sie die Netzwerke aus, zu denen Sie Verbindungen zulassen möchten. Nur die Netzwerke, mit denen das Gerät aktuell verbunden ist, sind aktiviert. Sie müssen mindestens ein Netzwerk auswählen.  
  
3.  Wählen Sie **Remotedebugging konfigurieren** aus, um die Firewalloptionen festzulegen und den Remotedebugger zu starten.  Öffnen Sie das Dialogfeld **Visual Studio-Remotedebugmonitor** , um Benutzern Berechtigungen für die Remotetools zu geben und andere erweiterte Optionen festzulegen.  
  
4.  Das Dialogfeld **Visual Studio-Remotedebugmonitor** wird angezeigt. In diesem Dialogfeld können Sie Benutzern Berechtigungen für die Remotetools gewähren und andere erweiterte Optionen festlegen.  
  
##  <a name="BKMK_ConfigureRemoteDebugger"></a> Konfigurieren des Remotedebuggers  
 Zum Ändern der Konfiguration des Remotedebuggers verwenden Sie zwei Tools.  
  
1. Im Menü **Tools** von **Visual Studio-Remotedebugmonitor**:  
  
   1.  Wählen Sie **Optionen** aus, um die Portnummer, den Authentifizierungsmodus oder das Timeoutintervall des Remotedebuggers zu ändern.  
  
   2.  Wählen Sie **Berechtigungen** aus, um Benutzer mit Berechtigungen für das Remotedebuggen hinzuzufügen oder zu entfernen.  
  
       > [!NOTE]
       >  Berechtigungen müssen jedem Benutzerkonto gewährt werden, von dem ein Remotedebuggen vorgenommen wird.  
  
   Mit dem **Konfigurations-Assistent für Remote Debugger** können Sie erweiterte Optionen für den Remotedebugger fest. Um den Assistenten zu öffnen, wählen Sie im Startbildschirm **Konfigurations-Assistent für Remote Debugger** aus.  
  
2. Auf der Seite **Visual Studio-Remotedebugdienst konfigurieren** können Sie auswählen, dass der Remotedebugger als Dienst ausgeführt wird. In den meisten Fällen ist das Ausführen als Dienst nicht erforderlich.  
  
3. Auf der Seite **Windows-Firewall zum Debugging konfigurieren** können Sie die Netzwerktypen hinzufügen oder entfernen, mit denen der Remotedebugger eine Verbindung herstellen soll. Nur die Netzwerke, mit denen das Gerät aktuell verbunden ist, sind aktiviert. Sie müssen mindestens ein Netzwerk auswählen.  
  
##  <a name="BKMK_ConnectVS"></a> Konfigurieren des Visual Studio-Projekts für das Remotedebuggen  
 In den Eigenschaften des Projekts geben Sie das Remotegerät an, mit dem eine Verbindung hergestellt werden soll. Das Verfahren unterscheidet sich je nach Programmiersprache. Sie können entweder den Netzwerknamen des Remotegeräts eingeben, oder es im Dialogfeld "Remotedebuggerverbindung auswählen" auswählen.  
  
 ![Select Remotedebuggerverbindung Dialogfeld](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 Im Dialogfeld werden nur die Geräte aufgelistet, die sich im lokalen Teilnetz von Visual Studio-Computers befinden und die den Remotedebugger ausführen.  
  
> [!TIP]
>  Sollten Sie Probleme beim Herstellen einer Verbindung mit einem Remotegerät haben, versuchen Sie, die IP-Adresse des Geräts einzugeben. Um die IP-Adresse eines Geräts zu bestimmen, öffnen Sie ein Befehlsfenster, und geben Sie dann **ipconfig**ein. Die IP-Adresse wird als **IPv4 Address**aufgeführt.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Auswählen des Remotegeräts für C#- und Visual Basic-Projekte  
 ![Verwaltete Projekteigenschaften für Remotedebugging](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Wählen Sie im Projektmappen-Explorer den Projektnamen aus und gehen Sie anschließend im Kontextmenü auf **Eigenschaften** .  
  
2.  Wählen Sie **Debuggen**aus.  
  
3.  Wählen Sie in der Liste **Zielgerät** die Option **Remotecomputer** aus.  
  
4.  Geben Sie den Netzwerknamen des Remotegeräts im Feld **Remotecomputer** ein, oder wählen Sie **Suchen** aus, um das Gerät im Dialogfeld **Remotedebuggerverbindung auswählen** auszuwählen.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Auswählen des Remotegeräts für JavaScript- und C++-Projekte  
 ![C&#43; &#43; Projekteigenschaften für das Remotedebuggen](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Wählen Sie im Projektmappen-Explorer den Projektnamen aus und gehen Sie anschließend im Kontextmenü auf **Eigenschaften** .  
  
2.  Erweitern Sie den Knoten **Konfigurationseigenschaften** , und wählen Sie dann **Debuggen**aus.  
  
3.  Wählen Sie **Remote Debugger** in der Liste **Zu startender Debugger** aus.  
  
4.  Geben Sie im Feld **Computername** den Netzwerknamen des Remotegeräts ein, oder wählen Sie im Feld den Pfeil nach unten aus, um im Dialogfeld **Remotedebuggerverbindung auswählen** das Gerät auszuwählen.  
  
##  <a name="BKMK_RunRemoteDebug"></a> Ausführen einer Remotedebugsitzung  
 Sie starten, beenden und navigieren eine Remotedebugsitzung genauso wie eine lokale Sitzung. Bevor Sie mit dem Debuggen beginnen, stellen Sie sicher, dass der Remotedebugmonitor auf dem Remotegerät ausgeführt wird.  
  
 Wählen Sie anschließend im Menü **Debuggen** (Tastatur: F5) die Option **Debuggen starten** aus. Das Projekt wird neu kompiliert, anschließend für das Remotegerät bereitgestellt und darauf gestartet . An Haltepunkten unterbricht der Debugger die Ausführung, und Sie können Ihren Code schrittweise ausführen, ihn überspringen oder verlassen. Wählen Sie **Debuggen beenden** aus, um Ihre Debugsitzung zu beenden, und schließen Sie die Remoteapp. Weitere Informationen finden Sie unter [Debuggen von apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Testen von Store-Apps mit Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debuggen von Apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)



