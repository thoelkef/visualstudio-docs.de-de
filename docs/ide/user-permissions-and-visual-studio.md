---
title: "Benutzerberechtigungen und Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Administratorrechte"
  - "Berechtigungen"
  - "Benutzerberechtigungen"
  - "Visual Studio, Benutzerberechtigungen"
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Benutzerberechtigungen und Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aus Sicherheitsgründen sollten Sie Visual Studio möglichst als normaler Benutzer ausführen.  
  
> [!WARNING]
>  Sie sollten auch sicherstellen, dass Sie keine Visual Studio\-Projektmappe kompilieren, starten oder debuggen, die nicht von einer vertrauenswürdigen Person oder einem vertrauenswürdigen Speicherort stammt.  
  
 Sie können nahezu alles in der Visual Studio\-IDE als normaler Benutzer ausführen. Für die folgenden Aufgaben benötigen Sie allerdings Administratorberechtigungen:  
  
|Bereich|Aufgabe|Weitere Informationen|  
|-------------|-------------|---------------------------|  
|Installation|Installieren von Visual Studio.|[Installieren von Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)|  
||Aktualisieren von einer Testversion von Visual Studio.|[Gewusst wie: Aktualisieren von einer Visual Studio\-Testversion](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|  
||Installieren, Aktualisieren oder Entfernen der lokalen Hilfeinhalte.|[Installieren und Verwalten von lokalen Inhalten](../ide/install-and-manage-local-content.md)|  
|Anwendungstypen|Entwickeln von Lösungen für SharePoint 2010.|[Anforderungen für die Entwicklung von SharePoint\-Lösungen](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||Erwerben einer Entwicklerlizenz für [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Erwerben einer Entwicklerlizenz \(Windows Store\-Apps\)](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|Toolbox|Hinzufügen von klassischen COM\-Steuerelementen zum **Werkzeugkasten**.|[Verwenden der Toolbox](../ide/using-the-toolbox.md)|  
|Add\-Ins|Installieren und Verwenden von Add\-Ins, die mit klassischem COM in der IDE geschrieben wurden.|[Erstellen von Add\-Ins und Assistenten](../Topic/Creating%20Add-ins%20and%20Wizards.md)|  
|Erstellung|Verwenden von Postbuildereignissen, die eine Komponente registrieren.|[Grundlagen benutzerdefinierter Buildschritte und Buildereignisse](/visual-cpp/ide/understanding-custom-build-steps-and-build-events)|  
||Einschließen eines Registrierungsschritts beim Erstellen von C\+\+\-Projekten.|[Grundlagen benutzerdefinierter Buildschritte und Buildereignisse](/visual-cpp/ide/understanding-custom-build-steps-and-build-events)|  
|Debuggen|Debuggen von Anwendungen, die mit höheren Berechtigungen ausgeführt werden.|[Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)|  
||Debuggen von Anwendungen, die unter einem anderen Benutzerkonto, wie ASP.NET\-Websites, ausgeführt werden.|[Debuggen von ASP.NET\- und AJAX\-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)|  
||Debuggen in der Zone für XAML\-Browseranwendungen \(XBAP\).|[WPF\-Host \(PresentationHost.exe\)](../Topic/WPF%20Host%20\(PresentationHost.exe\).md)|  
||Verwenden des Emulators zum Debuggen von Cloud\-Dienstprojekten für Microsoft Azure.|[Debuggen eines Cloud\-Diensts in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|  
||Konfigurieren einer Firewall für das Remotedebuggen.|[Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)|  
|Leistungstools|Profilerstellung für eine Anwendung|[Einführung in die Leistungsprofilerstellung](../profiling/beginners-guide-to-performance-profiling.md)|  
|Bereitstellung|Bereitstellen einer Webanwendung auf Internetinformationsdienste \(IIS\) auf einem lokalen Computer.|[Bereitstellen einer ASP.NET\-Webanwendung für einen Hostinganbieter, der Visual Studio oder Visual Web Developer verwendet: Bereitstellen in IIS als Testumgebung](http://go.microsoft.com/fwlink/?LinkId=266478)|  
|Bereitstellen von Feedback für Microsoft|Ändern der Teilnahme am Visual Studio\-Programm zur Verbesserung der Benutzerfreundlichkeit.|[Gewusst wie: Senden von Feedback](../misc/how-to-send-feedback-about-visual-studio.md)|  
  
## Ausführen von Visual Studio als Administrator  
 Sie können Visual Studio bei jedem Starten der IDE mit Administratorberechtigungen starten, oder Sie können die Anwendungsverknüpfung so ändern, dass sie immer mit Administratorberechtigungen ausgeführt werden muss.  Weitere Informationen finden Sie in der Windows\-Hilfe.  
  
#### So führen Sie Visual Studio mit Administratorberechtigungen in [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] oder [!INCLUDE[winblue_server_2](../ide/includes/winblue_server_2_md.md)] aus  
  
1.  Geben Sie im Bildschirm **Start** Visual Studio ein.  Sie sollten die Version oder die Versionen von Visual Studio sehen, die Sie installiert haben.  
  
2.  Wählen Sie die Version von Visual Studio, die Sie starten möchten, und öffnen Sie dann das Kontextmenü \(es wird am unteren Bildschirmrand angezeigt\).  Wählen Sie **Als Administrator ausführen**.  
  
     Beim Starten von Visual Studio wird **\(Administrator\)** nach dem Produktnamen in der Titelleiste angezeigt.  
  
#### So führen Sie Visual Studio mit Administratorberechtigungen in [!INCLUDE[win7](../debugger/includes/win7_md.md)] oder [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] aus  
  
1.  Wählen Sie im Menü **Start** die Option **Alle Programme** aus.  
  
2.  Wählen Sie im **Microsoft Visual Studio**  *Version*\-Ordner **Visual Studio** *Version* aus, öffnen Sie das Kontextmenü und wählen Sie **Als Administrator ausführen** aus.  
  
     Beim Starten von Visual Studio wird **\(Administrator\)** nach dem Produktnamen in der Titelleiste angezeigt.  
  
## Siehe auch  
 [Portieren, Migrieren und Aktualisieren von Visual Studio\-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Installieren von Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)