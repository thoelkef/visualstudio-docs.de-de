---
title: Benutzerberechtigungen und Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08b12e09348a28276d0c5d2f375b26e75c1ac3c5
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="user-permissions-and-visual-studio"></a>Benutzerberechtigungen und Visual Studio

Aus Sicherheitsgründen sollten Sie Visual Studio möglichst als normaler Benutzer ausführen.

> [!WARNING]
> Sie sollten auch sicherstellen, dass Sie keine Visual Studio-Projektmappe kompilieren, starten oder debuggen, die nicht von einer vertrauenswürdigen Person oder einem vertrauenswürdigen Speicherort stammt.

Sie können nahezu alles in der Visual Studio-IDE als normaler Benutzer ausführen. Für die folgenden Aufgaben benötigen Sie allerdings Administratorberechtigungen:

|Bereich|Aufgabe|Weitere Informationen|
|----------|----------|--------------------------|
|Installation|Installieren von Visual Studio.|[Installieren von Visual Studio](../install/install-visual-studio.md)|
||Installieren, Aktualisieren oder Entfernen der lokalen Hilfeinhalte.|[Installieren und Verwalten von lokalen Inhalten](../ide/install-and-manage-local-content.md)|
|Anwendungstypen|Entwickeln von Lösungen für SharePoint.|[Anforderungen für die Entwicklung von SharePoint-Projektmappen](../sharepoint/requirements-for-developing-sharepoint-solutions.md)|  
||Erwerben einer Entwicklerlizenz für [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Anfordern einer Entwicklerlizenz](http://go.microsoft.com/fwlink/?LinkID=241313)|
|Werkzeugkasten|Hinzufügen von klassischen COM-Steuerelementen zur **Toolbox**.|[Werkzeugkasten](../ide/reference/toolbox.md)|
|Add-Ins|Installieren und Verwenden von Add-Ins, die mit klassischem COM in der IDE geschrieben wurden.|[Erstellen von Add-Ins und Assistenten](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Erstellung|Verwenden von Postbuildereignissen, die eine Komponente registrieren.|[Grundlagen benutzerdefinierter Buildschritte und Buildereignisse](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||Einschließen eines Registrierungsschritts beim Erstellen von C++-Projekten.|[Grundlagen benutzerdefinierter Buildschritte und Buildereignisse](/cpp/ide/understanding-custom-build-steps-and-build-events)|
|Debuggen|Debuggen von Anwendungen, die mit höheren Berechtigungen ausgeführt werden.|[Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)|
||Debuggen von Anwendungen, die unter einem anderen Benutzerkonto, wie ASP.NET-Websites, ausgeführt werden.|[Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Debuggen in der Zone für XAML-Browseranwendungen (XBAP).|[WPF-Host (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Verwenden des Emulators zum Debuggen von Cloud-Dienstprojekten für Microsoft Azure.|[Debuggen eines Clouddiensts in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|
||Konfigurieren einer Firewall für das Remotedebuggen.|[Remotedebuggen](../debugger/remote-debugging.md)|
|Leistungstools|Profilerstellung für eine Anwendung|[Einführung in die Leistungsprofilerstellung](../profiling/beginners-guide-to-performance-profiling.md)|
|Bereitstellung|Bereitstellen einer Webanwendung auf Internetinformationsdienste (IIS) auf einem lokalen Computer.|[Deploy an ASP.NET Web Application to a Hosting Provider using Visual Studio or Visual Web Developer: Deploy to IIS as a Test Environment (Bereitstellen einer ASP.NET-Webanwendung für einen Hostinganbieter, der Visual Studio oder Visual Web Developer verwendet: Bereitstellen in IIS als Testumgebung)](http://go.microsoft.com/fwlink/?LinkId=266478)|
>>>>>>> 346075117af3d2bd1fddd9c3aca24516a39fa6a3

## <a name="run-visual-studio-as-an-administrator"></a>Ausführen von Visual Studio als Administrator

Sie können Visual Studio bei jedem Starten der IDE mit Administratorberechtigungen starten, oder Sie können die Anwendungsverknüpfung so ändern, dass sie immer mit Administratorberechtigungen ausgeführt werden muss. Weitere Informationen finden Sie in der Windows-Hilfe.

### <a name="run-visual-studio-with-administrative-permissions"></a>Ausführen von Visual Studio mit Administratorberechtigungen

Diese Anweisungen gelten für Windows 10. Für andere Windows-Versionen lauten die Anweisungen ähnlich.

1. Öffnen Sie das Menü **Start**, und scrollen Sie zu Visual Studio 2017.

1. Wählen Sie im Kontextmenü von **Visual Studio 2017** die Optionen **Mehr** > **Als Administrator ausführen** aus.

     Beim Starten von Visual Studio wird **(Administrator)** nach dem Produktnamen in der Titelleiste angezeigt.

## <a name="see-also"></a>Siehe auch

- [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Installieren von Visual Studio](../install/install-visual-studio.md)