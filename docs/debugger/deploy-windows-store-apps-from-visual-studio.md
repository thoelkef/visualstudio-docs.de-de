---
title: "Bereitstellen von Windows Store-Apps aus Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Bereitstellen von Windows Store-Apps aus Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Gilt nur für Windows](~/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Die Bereitstellungsfunktion von Visual Studio erstellt und registriert Windows Store\-Apps, die mit Visual Studio erstellt wurden, auf einem Zielgerät. Wie genau die App registriert wird, hängt davon ob, ob sich das Zielgerät lokal oder remote befindet:  
  
-   Handelt es sich bei dem Ziel um einen lokalen Visual Studio\-Computer, registriert Visual Studio die App vom Erstellungsordner aus.  
  
-   Handelt es sich bei dem Ziel um ein Remotegerät, kopiert Visual Studio die erforderlichen Dateien auf den Remotecomputer und registriert anschließend die App auf dem Gerät.  
  
 Die Bereitstellung erfolgt automatisch, wenn Sie die App von Visual Studio aus mit der Option **Debuggen starten** \(Tastatur: F5\) oder der Option **Starten ohne Debuggen** \(Tastatur: STRG \+ F5\) debuggen. Sie können die App auch manuell bereitstellen. Die manuelle Bereitstellung ist in folgenden Szenarios nützlich:  
  
-   Ad\-Hoc\-Tests auf einem lokalen oder Remotecomputer.  
  
-   Bereitstellen einer App, die eine andere App startet, welche Sie debuggen möchten.  
  
-   Bereitstellen einer App, deren Debugging beim Start durch eine andere App oder Methode erfolgen soll.  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 Hier erfahren Sie Folgendes:  
  
 [Bereitstellen von Windows Store-Apps](#BKMK_How_to_deploy_a_Windows_Store_app)  
  
 [Festlegen eines Remotegeräts](#BKMK_How_to_specify_a_remote_device)  
  
 [Bereitstellungsoptionen](#BKMK_Deployment_options)  
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Bereitstellen von Windows Store\-Apps  
 Das manuelle Bereitstellen einer App ist ein einfacher Vorgang:  
  
1.  Wenn Sie ein Remotegerät bereitstellen, geben Sie den Namen oder die IP\-Adresse des Geräts auf der Projekteigenschaftenseite des Startprojekts der App an. \(Die entsprechenden Schritte sind weiter unten in diesem Thema aufgelistet.\)  
  
2.  Wählen Sie auf der Debugger\-Symbolleiste von Visual Studio das Bereitstellungsziel aus der Dropdownliste neben der Schaltfläche **Debuggen starten** aus.  
  
     ![Ausführen auf lokalem Computer](../debugger/media/vsrun_f5_local.png "VSRUN\_F5\_Local")  
  
3.  Klicken Sie im Menü **Erstellen** auf **Bereitstellen**.  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> Festlegen eines Remotegeräts  
 **Erforderliche Komponenten**  
  
 So stellen Sie eine App auf einem Remotegerät bereit:  
  
-   Die Lizenz eines Entwicklers muss auf dem Remotegerät installiert sein.  
  
-   Die Visual Studio Remote Tools müssen auf dem Remotegerät installiert sein, außerdem muss der Remotedebugmonitor ausgeführt werden.  
  
     Bei der Bereitstellung wird der Remotedebugger\-Netzwerkkanal verwendet, um die App\-Dateien an das Remotegerät zu senden.  
  
#### So legen Sie ein Remotegerät fest  
  
1.  Geben Sie auf der Debugeigenschaftenseite für das Startprojekt den Namen oder die IP\-Adresse des Remotebereitstellungsziels an.  
  
2.  Wählen Sie zum Öffnen der Debugeigenschaftenseite das Projekt im Projektmappen\-Explorer aus, und klicken Sie dann im Kontextmenü auf **Eigenschaften**.  
  
3.  Wählen Sie dann den Knoten **Debuggen** im Eigenschaftenseitenfenster aus.  
  
4.  Sie können den Namen oder die IP\-Adresse des Remotegeräts eingeben, oder es im Dialogfeld **Remotedebuggerverbindung auswählen** auswählen.  
  
     ![Dialogfeld "Remotedebuggerverbindung auswählen"](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
     Im Dialogfeld **Remotedebuggerverbindung auswählen** werden die Geräte im Subnetz des lokalen Netzwerks sowie solche Geräte angezeigt, die direkt mit dem Visual Studio\-Computer durch ein Ethernetkabel verbunden sind.  
  
 **Angeben des Remotegeräts auf einer JavaScript\- oder Visual C\+\+\-Projektseite**  
  
 ![C&#43;&#43;&#45;Projekteigenschaften für Remotedebugging](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN\_CPP\_ProjProp\_Remote")  
  
1.  Wählen Sie **Remotedebugger** auf der Liste **Zu startender Debugger** aus.  
  
2.  Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Computername** ein. Oder verwenden Sie den nach unten weisenden Pfeil im Feld, um das Gerät im Dialogfeld "Remotedebuggerverbindung auswählen" auszuwählen.  
  
 **Angeben des Remotegeräts auf einer Visual C\#\- oder Visual Basic\-Projektseite**  
  
 ![Verwaltete Projekteigenschaften für Remotedebugging](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN\_Managed\_ProjProp\_Remote")  
  
1.  Wählen Sie **Remotecomputer** auf der **Zielgeräteliste** aus.  
  
2.  Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Remotecomputer** ein oder klicken Sie auf **Suchen**, um das Gerät im Dialogfeld **Remotedebuggerverbindung auswählen** auszuwählen.  
  
##  <a name="BKMK_Deployment_options"></a> Bereitstellungsoptionen  
 Sie können die folgenden Bereitstellungsoptionen auf der Debugeigenschaftenseite für das Startprojekt festlegen.  
  
 **Netzwerkloopback zulassen**  
 Aus Sicherheitsgründen wird einer im Standardverfahren installierten [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]\-App nicht erlaubt, Netzwerkaufrufe an das Gerät auszuführen, auf dem sie installiert wurde. Standardmäßig wird durch die Visual Studio\-Bereitstellung eine Ausnahme von dieser Regel für die bereitgestellte App erstellt. Diese Ausnahme ermöglicht das Testen von Kommunikationsverfahren auf einem einzelnen Computer. Bevor Sie die App an [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] senden, sollten Sie die App ohne die Ausnahme testen.  
  
 So entfernen Sie die Netzwerkloopbackausnahme aus der App:  
  
-   Deaktivieren Sie auf der Debugeigenschaftenseite für C\# und VB das Kontrollkästchen **Netzwerkloopback zulassen**.  
  
-   Legen Sie auf der Debugeigenschaftenseite für JavaScript den Wert für **Netzwerkloopback zulassen** auf **Nein** fest.  
  
 **Eigenen Code zunächst nicht starten sondern debuggen \(C\# und VB\) \/ Anwendung starten \(JavaScript und C\+\+\)**  
 So konfigurieren Sie den automatischen Start einer Debugsitzung beim Starten der Anwendung für die Bereitstellung:  
  
-   Aktivieren Sie auf der Debugeigenschaftenseite für C\# und VB das Kontrollkästchen **Eigenen Code zunächst nicht starten sondern debuggen**.  
  
-   Legen Sie auf der Debugeigenschaftenseite für JavaScript den Wert für **Anwendung starten** auf **Ja** fest.  
  
## Siehe auch  
 [Ausführen von Apps aus Visual Studio](../debugger/run-store-apps-from-visual-studio.md)