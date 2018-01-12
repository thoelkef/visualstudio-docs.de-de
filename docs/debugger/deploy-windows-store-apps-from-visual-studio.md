---
title: Bereitstellen von uwp-apps aus Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 95f009ca761d4d978fb5e5a9323722e5dfc34cb8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Bereitstellen von uwp-apps aus Visual Studio
![Gilt nur für Windows](../debugger/media/windows_only_content.png "Windows_only_content")  
  
 Die Bereitstellungsfunktion von Visual Studio erstellt und registriert uwp-apps, die mit Visual Studio auf einem Zielgerät erstellt werden. Wie genau die App registriert wird, hängt davon ob, ob sich das Zielgerät lokal oder remote befindet:  
  
-   Handelt es sich bei dem Ziel um einen lokalen Visual Studio-Computer, registriert Visual Studio die App vom Erstellungsordner aus.  
  
-   Handelt es sich bei dem Ziel um ein Remotegerät, kopiert Visual Studio die erforderlichen Dateien auf den Remotecomputer und registriert anschließend die App auf dem Gerät.  
  
 Bereitstellung erfolgt automatisch, wenn Ihre app aus Visual Studio zu debuggen, mit der **Debuggen** Option (Tastatur: F5) oder die **Starten ohne Debugging** Option (Tastatur: STRG + F5). Sie können die App auch manuell bereitstellen. Die manuelle Bereitstellung ist in folgenden Szenarios nützlich:  
  
-   Ad-Hoc-Tests auf einem lokalen oder Remotecomputer.  
  
-   Bereitstellen einer App, die eine andere App startet, welche Sie debuggen möchten.  
  
-   Bereitstellen einer App, deren Debugging beim Start durch eine andere App oder Methode erfolgen soll.
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>Gewusst wie: Bereitstellen eine uwp-app  
 Das manuelle Bereitstellen einer App ist ein einfacher Vorgang:  
  
1.  Wenn Sie ein Remotegerät bereitstellen, geben Sie den Namen oder die IP-Adresse des Geräts auf der Projekteigenschaftenseite des Startprojekts der App an. (Die entsprechenden Schritte sind weiter unten in diesem Thema aufgelistet.)  
  
2.  Wählen Sie auf der Debugger-Symbolleiste von Visual Studio das Bereitstellungsziel aus der Dropdownliste neben der Schaltfläche **Debuggen starten** aus.  
  
     ![Führen Sie auf dem lokalen Computer](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
3.  Klicken Sie im Menü **Erstellen** auf **Bereitstellen**.  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> Festlegen eines Remotegeräts  

**Erforderliche Komponenten**  
  
Sie müssen auf einem Windows 10-Remotegerät aktivieren [Entwicklermodus](/windows/uwp/get-started/enable-your-device-for-development). Auf Windows 10-Geräten, die mit der Ersteller des Update oder später, die Remoteserver-Verwaltungstools werden automatisch installiert, wenn Sie Ihre app bereitstellen. Weitere Informationen finden Sie unter [eine installierte app-Paket Debuggen](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Unter Windows 8.1 und Pre-Ersteller-Update-Versionen von Windows 10 müssen den Remotetools für Visual Studio muss auf dem Remotegerät installiert sein, und der Remotedebugger ausgeführt werden muss. Auf Windows 8.1 müssen Sie auch eine Entwicklerlizenz installieren.
  
Bei der Bereitstellung wird der Remotedebugger-Netzwerkkanal verwendet, um die App-Dateien an das Remotegerät zu senden.  
  
#### <a name="to-specify-a-remote-device"></a>So legen Sie ein Remotegerät fest  
  
1.  Geben Sie auf der Debugeigenschaftenseite für das Startprojekt den Namen oder die IP-Adresse des Remotebereitstellungsziels an.  
  
2.  Wählen Sie zum Öffnen der Debugeigenschaftenseite das Projekt im Projektmappen-Explorer aus, und klicken Sie dann im Kontextmenü auf **Eigenschaften** .  
  
3.  Wählen Sie dann den Knoten **Debuggen** im Eigenschaftenseitenfenster aus.

4. Für **Zielgerät**Option **Remotecomputer**.

5. Klicken Sie unter **Remotecomputer**, klicken Sie auf **suchen**.
  
4.  Sie können den Namen oder die IP-Adresse des Remotegeräts eingeben, oder Sie können das Gerät aus der **Remoteverbindung** (Dialogfeld).  
  
     ![Wählen Sie Remote Debugger-Verbindung (Dialogfeld)](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
     Die **Remoteverbindung** Dialogfeld zeigt die Geräte im Subnetz des lokalen Netzwerks sowie solche Geräte, die durch ein Ethernetkabel direkt mit dem Visual Studio-Computer verbunden ist.  
  
 **Angeben des Remotegeräts auf einer JavaScript- oder Visual C++-Projektseite**  
  
 ![C# 43; &#43; Projekteigenschaften für das Remotedebuggen](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Wählen Sie **Remote Debugger** in der Liste **Zu startender Debugger** aus.  
  
2.  Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Computername** ein. Oder verwenden Sie den nach unten weisenden Pfeil im Feld, um das Gerät im Dialogfeld "Remotedebuggerverbindung auswählen" auszuwählen.  
  
 **Angeben des Remotegeräts auf einer Visual C#- oder Visual Basic-Projektseite**  
  
 ![Verwaltete Projekteigenschaften für Remotedebugging](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Wählen Sie in der Liste **Zielgerät** die Option **Remotecomputer** aus.  
  
2.  Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Remotecomputer** ein oder klicken Sie auf **Suchen** , um das Gerät im Dialogfeld **Remotedebuggerverbindung auswählen** auszuwählen.  
  
##  <a name="BKMK_Deployment_options"></a> Bereitstellungsoptionen  
 Sie können die folgenden Bereitstellungsoptionen auf der Debugeigenschaftenseite für das Startprojekt festlegen.  
  
 **Netzwerkloopback zulassen**  
 Aus Sicherheitsgründen einer uwp-App oder [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] im Standardverfahren installierten app ist nicht zulässig, Netzwerkaufrufe an das Gerät auszuführen, es installiert ist. Standardmäßig wird durch die Visual Studio-Bereitstellung eine Ausnahme von dieser Regel für die bereitgestellte App erstellt. Diese Ausnahme ermöglicht das Testen von Kommunikationsverfahren auf einem einzelnen Computer. Bevor Sie die App an [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]senden, sollten Sie die App ohne die Ausnahme testen.  
  
 So entfernen Sie die Netzwerkloopbackausnahme aus der App:  
  
-   Deaktivieren Sie auf der Debugeigenschaftenseite für C# und VB das Kontrollkästchen **Netzwerkloopback zulassen** .  
  
-   Legen Sie auf der Debugeigenschaftenseite für JavaScript den Wert für **Netzwerkloopback zulassen** auf **Nein**fest.  
  
 **Eigenen Code zunächst nicht starten sondern debuggen (C# und VB) / Anwendung starten (JavaScript und C++)**  
 So konfigurieren Sie den automatischen Start einer Debugsitzung beim Starten der Anwendung für die Bereitstellung:  
  
-   Aktivieren Sie auf der Debugeigenschaftenseite für C# und VB das Kontrollkästchen **Eigenen Code zunächst nicht starten sondern debuggen** .  
  
-   Legen Sie auf der Debugeigenschaftenseite für JavaScript den Wert für **Anwendung starten** auf **Ja**fest.  
  
## <a name="see-also"></a>Siehe auch  
 [Eine installierte app-Paket Debuggen](../debugger/debug-installed-app-package.md).   
 [Ausführen von apps aus Visual Studio](../debugger/run-store-apps-from-visual-studio.md)