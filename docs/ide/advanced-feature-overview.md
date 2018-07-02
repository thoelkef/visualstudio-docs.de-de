---
title: Erweiterte Features von Visual Studio 2017
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e50bd5231387261e56a62234858d10c3806de3dc
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34694068"
---
# <a name="features-of-visual-studio-2017"></a>Features von Visual Studio 2017

Der Artikel [Übersicht über die Visual Studio-IDE](../ide/visual-studio-ide.md) bietet eine grundlegende Einführung in Visual Studio. In diesem Artikel werden Features beschrieben, die möglicherweise besser für erfahrene Entwickler oder Benutzer geeignet sind, die bereits mit Visual Studio vertraut sind.

## <a name="modular-installation"></a>Modulare Installation

Mit dem modularen Installer von Visual Studio können Sie *Workloads* auswählen und installieren, die Gruppen von Funktionen sind, die für die bevorzugte Programmiersprache oder Plattform erforderlich sind. Diese Strategie hält den Platzbedarf der Visual Studio-Installation kleiner, d.h. Updates werden auch schneller installiert und aktualisiert.

Wenn Sie Visual Studio 2017 noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

Weitere Informationen zum Einrichten von Visual Studio auf Ihrem System finden Sie unter [Installieren von Visual Studio 2017 RC](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Erstellen von cloudfähigen Apps für Azure

Visual Studio bietet eine integrierte Sammlung von Tools, die Ihnen das einfache Entwickeln von cloudaktivierten Anwendungen in Microsoft Azure ermöglichen. Sie können Anwendungen und Dienste in Microsoft Azure direkt von der IDE aus konfigurieren, erstellen, debuggen, packen und bereitstellen. Wählen Sie beim Installieren von Visual Studio die Workload **Azure-Entwicklung** aus, um Azure-Tools und -Projektvorlagen zu erhalten.

![Workload „Azure-Entwicklung“](../data-tools/media/azure-development-workload.png)

Nachdem Sie die Workload **Azure-Entwicklung** installiert haben, sind die folgenden C#-Vorlagen für die **Cloud** im Dialogfeld **Neues Projekt** verfügbar:

![Cloud-Projektvorlagen für Visual Studio](media/cloud-project-templates.png)

Mit dem [Cloud-Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) von Visual Studio können Sie Azure-basierte Cloudressourcen in Visual Studio anzeigen und verwalten. Diese Ressourcen können virtuelle Computer, Tabellen, SQL-Datenbanken und mehr umfassen. **Cloud-Explorer** zeigt die Azure-Ressourcen aller Konten an, die unter dem Azure-Abonnement, bei dem Sie angemeldet sind, verwaltet werden. Wenn für einen bestimmten Vorgang das Azure-Portal erforderlich ist, stellt **Cloud-Explorer** Verknüpfungen bereit, mit denen Sie an den richtigen Ort im Portal gelangen.

![Cloud-Explorer in Visual Studio](media/cloud-explorer.png)

Sie können Azure-Dienste wie die folgenden für Ihre Apps mit **verbundenen Diensten** nutzen:

- [Verbundener Dienst für Active Directory:](/azure/active-directory/develop/vs-active-directory-add-connected-service) Damit Benutzer ihre [Azure Active Directory](/azure/active-directory/active-directory-whatis)-Konten zum Herstellen einer Verbindung mit Web-Apps verwenden können.
- [Verbundener Dienst für Azure Storage:](/azure/vs-azure-tools-connected-services-storage) Für Blob-Speicher, Warteschlangen und Tabellen
- [Verbundener Dienst für Key Vault:](/azure/key-vault/vs-key-vault-add-connected-service) Zum Verwalten von Geheimnissen für Web-Apps

Der verfügbare **verbundene Dienst** hängt vom Projekttyp ab. Fügen Sie einen Dienst hinzu, indem Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** klicken und **Hinzufügen** > **Verbundener Dienst** auswählen.

![Verbundene Dienste in Visual Studio](media/connected-services.png)

Weitere Informationen finden Sie unter [Einstieg in die Cloud mit Visual Studio und Azure](https://www.visualstudio.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Erstellen von Apps für das Web

Das Web bestimmt unsere moderne Welt, und Visual Studio kann Ihnen helfen, Apps dafür zu schreiben. Sie können Web-Apps mit ASP.NET, Node.js, Python, JavaScript und TypeScript erstellen. Visual Studio erkennt Webframeworks wie Angular, jQuery, Express und mehr. ASP.NET Core und .NET Core sind unter Windows, Mac und Linux ausführbar. [ASP.NET Core](http://www.asp.net/core/overview) ist ein wichtiges Update für MVC, WebAPI und SignalR und kann unter Windows, Mac und Linux ausgeführt werden.  ASP.NET Core wurde von Grund auf als effizienter, zusammensetzbarer .NET-Stapel zum Erstellen moderner, cloudbasierter Web-Apps und Dienste entwickelt.

Weitere Informationen finden Sie unter [Moderne Tools für die Entwicklung von Webanwendungen](https://www.visualstudio.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Erstellen plattformübergreifender Apps und Spiele

Sie können mithilfe von Visual Studio Apps und Spiele für macOS, Linux, Windows, Android, iOS und andere [mobile Geräte](https://www.visualstudio.com/vs/mobile-app-development/) erstellen.

- Entwickeln Sie [.NET Core](/dotnet/core/)-Apps, die unter Windows, macOS und Linux ausgeführt werden können.

- Erstellen Sie unter Verwendung von [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/) mobile Apps für iOS, Android und Windows in C# und F#.

- Nutzen Sie Standardwebtechnologien wie &mdash;HTML, CSS und JavaScript&mdash;, um unter Verwendung von [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/) mobile Apps für iOS, Android und Windows zu entwickeln.

- Entwickeln Sie mit den [Visual Studio-Tools für Unity](../cross-platform/visual-studio-tools-for-unity.md) 2D- und 3D-Spiele in C#.

- Mithilfe von [C++ für die plattformübergreifende Entwicklung](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md) können Sie native C++-Apps für iOS-, Android- und Windows-Geräte erstellen sowie für iOS, Android und Windows erstellten allgemeinen Code in Bibliotheken freigeben.

- Nutzen Sie den [Android-Emulator](../cross-platform/visual-studio-emulator-for-android.md), um Android-Apps bereitzustellen, zu testen und zu debuggen.

## <a name="connect-to-databases"></a>Herstellen einer Verbindung mit Datenbanken

**Server-Explorer** unterstützt Sie dabei, SQL Server-Instanzen und -Ressourcen lokal, remote, in Azure, Salesforce.com, Office 365 und auf Websites zu suchen und zu verwalten. Wählen Sie zum Öffnen des **Server-Explorers** im Hauptmenü **Ansicht** > **Server-Explorer** aus. Unter [Neue Verbindung hinzufügen](../data-tools/add-new-connections.md) finden Sie weitere Informationen zur Verwendung von Server-Explorer.

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) ist eine leistungsstarke Entwicklungsumgebung für SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse. Damit können Sie Datenbanken erstellen, debuggen, verwalten und umgestalten. Sie können mit einem Datenbankprojekt oder direkt mit einer Instanz einer verbundenen Datenbank lokal oder extern arbeiten.

**SQL Server-Objekt-Explorer** in Visual Studio bietet eine Anzeige der Datenbankobjekte ähnlich der von SQL Server Management Studio. Mit dem SQL Server-Objekt-Explorer können Sie leichte Verwaltungs- und Designarbeiten für Datenbanken durchführen, darunter Bearbeiten von Tabellendaten, Vergleichen von Schemas und Ausführen von Abfragen mithilfe von Kontextmenüs direkt aus dem SQL Server-Objekt-Explorer.

![SQL Server-Objekt-Explorer](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Debuggen, Testen und Verbessern Ihres Codes

Wenn Sie Code schreiben, müssen Sie ihn auszuführen und auf Fehler und Leistung prüfen. Das dem neuesten Entwicklungsstand entsprechende Debugsystem von Visual Studio ermöglicht Ihnen, Code in Ihrem lokalen Projekt, auf einem Remotegerät oder auf einem [Geräteemulator](../cross-platform/visual-studio-emulator-for-android.md) zu debuggen. Sie können Ihren Code Anweisung für Anweisung durchlaufen und die Variablen untersuchen. Sie können Haltepunkte setzen, die nur erreicht werden, wenn eine bestimmte Bedingung erfüllt ist. All dies kann im Code-Editor selbst verwaltet werden, sodass Sie den Code nicht verlassen müssen. Weitere Informationen über den Debugprozess in Visual Studio finden Sie unter [Tour zu den Debuggerfeatures](../debugger/debugger-feature-tour.md).

Sehen Sie sich für weitere Informationen zum Verbessern der Leistung Ihrer Apps das [Profilerstellungsfeature](../profiling/profiling-feature-tour.md) von Visual Studio an.

Zum [Testen](../test/improve-code-quality.md) stehen in Visual Studio Komponententests, Live Unit Testing, IntelliTest, Auslastungs- sowie Leistungstests und mehr zur Verfügung. Visual Studio verfügt auch über erweiterte [Codeanalyse](../code-quality/code-analysis-for-managed-code-overview.md)-Funktionen, um Entwurfsfehler, Sicherheitsfehler und andere Arten von Fehlern abzufangen.

## <a name="deploy-your-finished-application"></a>Bereitstellen der fertigen Anwendung

Wenn Ihre Anwendung für die Bereitstellung für Benutzer oder Kunden bereit ist, bietet Visual Studio die dazu benötigten Tools, unabhängig davon, ob Sie sie im Microsoft Store, auf einer SharePoint-Website oder mit InstallShield- oder Windows Installer-Technologien bereitstellen möchten. Sie können über die IDE auf alle Tools zugreifen. Weitere Informationen finden Sie unter [Bereitstellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Verarbeiten Ihres Quellcodes und Zusammenarbeiten mit anderen

Sie können Ihren Quellcode in Git-Repositorys verwalten, die von beliebigen Anbietern gehostet werden, einschließlich GitHub. Oder verwenden Sie [Visual Studio Team Services (VSTS)](/vsts/index), um Code zusammen mit Programmfehlern und Arbeitsaufgaben für Ihr gesamtes Projekt zu verwalten. Weitere Informationen zur Verwaltung von Git-Repositorys in Visual Studio mithilfe von Team Explorer finden Sie unter [Get Started with Git and Team Services (VSTS) (Erste Schritte mit Git und Team Services (VSTS))](/vsts/git/gitquickstart?tabs=visual-studio). Visual Studio verfügt auch über andere integrierte Quellcodeverwaltungsfunktionen. Weitere Informationen dazu finden Sie unter [New Git Features in Visual Studio 2017 (blog) (Neue Git-Features in Visual Studio 2017 (Blog))](https://blogs.msdn.microsoft.com/visualstudioalm/2017/03/06/new-git-features-in-visual-studio-2017/).

Visual Studio Online Team Services ist ein cloudbasierter Dienst zum Hosten von Softwareprojekten und für die Zusammenarbeit in Teams. VSTS unterstützt Git- und Team Foundation-Quellcodeverwaltungssysteme sowie die Scrum-, CMMI- und Agile-Entwicklungsmethoden. Team Foundation-Versionskontrolle (TFVC) verwendet ein einzelnes, zentralisiertes Serverrepository zum Nachverfolgen von Versionsdateien. Lokale Änderungen werden immer beim zentralen Server eingecheckt, damit andere Entwickler die neuesten Änderungen abrufen können.

Team Foundation Server (TFS) ist der Anwendungslebenszyklus-Verwaltungshub für Visual Studio. Auf diese Weise können alle am Entwicklungsprozess beteiligten Personen mithilfe einer einzigen Projektmappe am Prozess teilnehmen. TFS ist auch nützlich für die Verwaltung heterogener Teams und Projekte.

Wenn Sie in Ihrem Netzwerk über ein Visual Studio Team Services-Konto oder einen Team Foundation Server verfügen, können Sie über das Fenster **Team Explorer** eine Verbindung mit dem Konto bzw. Server in Visual Studio herstellen. Über dieses Fenster können Sie Code in die Quellcodeverwaltung einchecken oder daraus auschecken, Arbeitsaufgaben verwalten, Builds starten und auf Teamräume und Arbeitsbereiche zugreifen. Öffnen Sie **Team Explorer** über das Feld **Schnellstart** oder über das Hauptmenü unter **Ansicht** > **Team Explorer** oder **Team** > **Verbindungen verwalten**.

Die folgende Abbildung zeigt das **Team Explorer**-Fenster für eine Projektmappe, die in VSTS gehostet wird:

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer.png)

Der Buildprozess lässt sich automatisieren, um den Code zu erstellen, den die Entwickler in Ihrem Team in die Versionskontrolle eingecheckt haben. Beispielsweise können Sie ein Projekt oder mehrere Projekte jede Nacht oder bei jedem Einchecken dieses Code ausführen. Weitere Informationen finden Sie unter [Build und Release (VSTS und TFS)](/vsts/build-release/index).

## <a name="extend-visual-studio"></a>Erweitern von Visual Studio

Wenn Visual Studio nicht genau die Funktionalität besitzt, die Sie benötigen, können Sie sie hinzufügen! Sie können die IDE basierend auf Ihrem Workflow und Stil personalisieren, Unterstützung für externe Tools hinzufügen, die noch nicht in Visual Studio integriert sind, und vorhandene Funktionalität ändern, um Ihre Produktivität zu steigern. Unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md)finden Sie die neueste Version der Visual Studio-Erweiterbarkeitstools (VS SDK).

Sie können die .NET Compiler Platform („Roslyn“) zum Schreiben eigener Code-Analyzer und Code-Generators verwenden. Unter [Roslyn](https://github.com/dotnet/Roslyn)finden Sie alles Nötige.

Suchen Sie nach [vorhandenen Erweiterungen](https://marketplace.visualstudio.com/vs) für Visual Studio, die von Microsoft-Entwicklern sowie unserer Entwickler-Community erstellt wurden.

Weitere Informationen zum Erweitern von Visual Studio finden Sie unter [Erweitern der Visual Studio-IDE](https://www.visualstudio.com/vs/extend/).

## <a name="see-also"></a>Siehe auch

- [Übersicht über die Visual Studio-IDE](../ide/visual-studio-ide.md)
- [Neuerungen in Visual Studio 2017](../ide/whats-new-in-visual-studio.md)