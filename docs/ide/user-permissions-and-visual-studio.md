---
title: Benutzerberechtigungen und Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 0dc9fed1e5fc5a827e836310175d558b14cd41b4
ms.lasthandoff: 04/05/2017

---
# <a name="user-permissions-and-visual-studio"></a>Benutzerberechtigungen und Visual Studio
Aus Sicherheitsgründen sollten Sie Visual Studio möglichst als normaler Benutzer ausführen.  

> [!WARNING]
>  Sie sollten auch sicherstellen, dass Sie keine Visual Studio-Projektmappe kompilieren, starten oder debuggen, die nicht von einer vertrauenswürdigen Person oder einem vertrauenswürdigen Speicherort stammt.  

 Sie können nahezu alles in der Visual Studio-IDE als normaler Benutzer ausführen. Für die folgenden Aufgaben benötigen Sie allerdings Administratorberechtigungen:  

|Bereich|Aufgabe|Weitere Informationen|  
|----------|----------|--------------------------|  
|Installation|Installieren von Visual Studio.|[Installieren von Visual Studio](../install/install-visual-studio.md)|  
||Installieren, Aktualisieren oder Entfernen der lokalen Hilfeinhalte.|[Installieren und Verwalten von lokalen Inhalten](../ide/install-and-manage-local-content.md)|  
|Anwendungstypen|Entwickeln von Lösungen für SharePoint.|[Anforderungen für die Entwicklung von SharePoint-Projektmappen](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||Erwerben einer Entwicklerlizenz für [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Anfordern einer Entwicklerlizenz (Windows Store-Apps)](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|Werkzeugkasten|Hinzufügen von klassischen COM-Steuerelementen zur **Toolbox**.|[Verwenden der Toolbox](../ide/using-the-toolbox.md)|  
|Add-Ins|Installieren und Verwenden von Add-Ins, die mit klassischem COM in der IDE geschrieben wurden.|[Erstellen von Add-Ins und Assistenten](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|  
|Erstellung|Verwenden von Postbuildereignissen, die eine Komponente registrieren.|[Grundlagen benutzerdefinierter Buildschritte und Buildereignisse](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
||Einschließen eines Registrierungsschritts beim Erstellen von C++-Projekten.|[Grundlagen benutzerdefinierter Buildschritte und Buildereignisse](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
|Debuggen|Debuggen von Anwendungen, die mit höheren Berechtigungen ausgeführt werden.|[Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)|  
||Debuggen von Anwendungen, die unter einem anderen Benutzerkonto, wie ASP.NET-Websites, ausgeführt werden.|[Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)|  
||Debuggen in der Zone für XAML-Browseranwendungen (XBAP).|[WPF-Host (PresentationHost.exe)](http://msdn.microsoft.com/Library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|  
||Verwenden des Emulators zum Debuggen von Cloud-Dienstprojekten für Microsoft Azure.|[Debuggen eines Clouddiensts in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|  
||Konfigurieren einer Firewall für das Remotedebuggen.|[Remotedebuggen](../debugger/remote-debugging.md)|  
|Leistungstools|Profilerstellung für eine Anwendung|[Einführung in die Leistungsprofilerstellung](../profiling/beginners-guide-to-performance-profiling.md)|  
|Bereitstellung|Bereitstellen einer Webanwendung auf Internetinformationsdienste (IIS) auf einem lokalen Computer.|[Deploying an ASP.NET Web Application to a Hosting Provider using Visual Studio or Visual Web Developer: Deploying to IIS as a Test Environment (Bereitstellen einer ASP.NET-Webanwendung für einen Hostinganbieter, der Visual Studio oder Visual Web Developer verwendet: Bereitstellen in IIS als Testumgebung)](http://go.microsoft.com/fwlink/?LinkId=266478)|

## <a name="running-visual-studio-as-an-administrator"></a>Ausführen von Visual Studio als Administrator  
 Sie können Visual Studio bei jedem Starten der IDE mit Administratorberechtigungen starten, oder Sie können die Anwendungsverknüpfung so ändern, dass sie immer mit Administratorberechtigungen ausgeführt werden muss. Weitere Informationen finden Sie in der Windows-Hilfe.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8debuggerincludeswin8mdmd-includewin81debuggerincludeswin81mdmd-includewinserver8debuggerincludeswinserver8mdmd-or-includewinblueserver2ideincludeswinblueserver2mdmd"></a>So führen Sie Visual Studio mit Administratorberechtigungen in [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] oder [!INCLUDE[winblue_server_2](../ide/includes/winblue_server_2_md.md)] aus  

1.  Geben Sie auf dem **Start**-Bildschirm **Visual Studio** ein. Sie sollten die Version oder die Versionen von Visual Studio sehen, die Sie installiert haben.  

2.  Wählen Sie die Version von Visual Studio, die Sie starten möchten, und öffnen Sie dann das Kontextmenü (es wird am unteren Bildschirmrand angezeigt). Wählen Sie **Als Administrator ausführen**.  

     Beim Starten von Visual Studio wird **(Administrator)** nach dem Produktnamen in der Titelleiste angezeigt.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7debuggerincludeswin7mdmd-or-includewinsvr08r2debuggerincludeswinsvr08r2mdmd"></a>So führen Sie Visual Studio mit Administratorberechtigungen in [!INCLUDE[win7](../debugger/includes/win7_md.md)] oder [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] aus  

1.  Wählen Sie im **Start**-Menü die Option **Alle Programme** aus.  

2.  Wählen Sie im **Microsoft Visual Studio** *Version*-Ordner **Visual Studio** *Version* aus, öffnen Sie das Kontextmenü, und wählen Sie **Als Administrator ausführen** aus.  

     Beim Starten von Visual Studio wird **(Administrator)** nach dem Produktnamen in der Titelleiste angezeigt.  

## <a name="see-also"></a>Siehe auch  
 [Portieren, Migrieren und Upgraden von Visual Studio-Projekten](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Installieren von Visual Studio](../install/install-visual-studio.md)

