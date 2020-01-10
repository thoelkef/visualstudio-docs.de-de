---
title: Portieren, Migrieren und Upgraden von Projekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 0f41abab206362ea60fafa30f2abcbf5eb474ddc
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849915"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Projektmigration und Upgradereferenz für Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [Projektmigration und Upgradereferenz für Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Wenn Sie in Erwägung ziehen, zu einer neueren Version von Visual Studio zu wechseln, können Sie anhand dieses Artikels herausfinden, welche Projektmappen, Projekte, Dateien und anderen Ressourcen, die Sie in Visual Studio 2013, Visual Studio 2012 oder Visual Studio 2010 SP1 erstellt haben, ausgeführt werden. ohne Änderung in Visual Studio 2013 und Visual Studio 2015. Möglicherweise wurde diese Seite auch aufgerufen, wenn Sie beim Öffnen eines Projekts eine Fehlermeldung erhalten haben, weil das Projekt in Ihrer Visual Studio-Version nicht unterstützt wird bzw. ein SDK oder eine Erweiterung wie z. B. das Azure SDK für .NET erfordert.

Viele häufig verwendete Assets Verhalten sich in Visual Studio 2015, Visual Studio 2013 und den beiden früheren Versionen identisch. Beispielsweise können Sie in Visual Studio 2015 ein Projekt öffnen, das in Visual Studio 2013 oder Visual Studio 2012 erstellt wurde, es ändern und anschließend in Visual Studio 2015 erneut öffnen. Ihre Änderungen bleiben erhalten, und das Projekt verhält sich wie in der früheren Version. Dies gilt auch für viele Ressourcen, die in Visual Studio 2010 SP1 erstellt wurden.

Bei Visual Basic wurden in Visual Studio 2015 keine Änderungen eingeführt, die verhindern, dass eine Visual Basic-APP, die in Visual Studio 2013 erstellt wurde, kompiliert wird. Das Laufzeitverhalten von Visual Basic-apps, die mit Visual Studio 2015 neu kompiliert werden, ändert sich nicht.

Wenn Sie Visual Studio 2015 mit Visual Studio 2013, Visual Studio 2012 oder Visual Studio 2010 SP1 verwenden, können Sie Projekte und Dateien in jeder der Versionen erstellen und ändern. Sie können Projekte und Dateien zwischen den Versionen übertragen, solange Sie keine Funktionen hinzufügen, die in einer oder mehreren Versionen nicht unterstützt werden.

## <a name="project"></a> Projekte

In der folgenden Liste wird die Unterstützung in Visual Studio 2015 und Visual Studio 2013 für Projekte beschrieben, die in Visual Studio 2012 oder Visual Studio 2010 SP1 erstellt wurden. Verwenden Sie diese Liste, um zu bestimmen, ob Sie ein Projekt "unverändert" in Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 oder Visual Studio 2010 SP1 öffnen können oder ob Sie es ändern müssen, um die Kompatibilität zu gewährleisten.

|Projekttyp|Kompatibilität|
|---------------------|-------------------|
|Universelle Windows-Plattform-Apps|Wählen Sie zum Installieren der Tools für die universelle Windows-Apps **Benutzerdefiniert** oder **Ändern**und dann die Option für die **Entwicklungstools für die universelle Windows-App**aus.<br /><br /> Die universelle Windows-Plattform (UWP)-app-Entwicklung für Windows 10 wird nur in Visual Studio 2015 unter Windows 10 oder [!INCLUDE[win81](../includes/win81-md.md)]unterstützt.|
|Windows Store-Apps|Windows Store-App-Entwicklung, einschließlich Universelle Apps für Windows 8.1 und Windows Phone 8.1 wird unter [!INCLUDE[win81](../includes/win81-md.md)] und Windows 10 unterstützt. Vorhandene [!INCLUDE[win8](../includes/win8-md.md)] -Projekte können weiterhin gewartet werden. Es können jedoch keine neuen [!INCLUDE[win8](../includes/win8-md.md)] -Projekte erstellt werden. [!INCLUDE[win81](../includes/win81-md.md)]-Projekte können nur von bestimmten Verweistypen abhängen. Weitere Informationen finden Sie unter [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md). **Hinweis:** [!INCLUDE[win81](../includes/win81-md.md)] Projekte, die Sie mit Visual Studio 2015 oder Visual Studio 2013 erstellen, können nicht in Visual Studio 2012 geöffnet werden. Dies liegt daran, dass [!INCLUDE[win81](../includes/win81-md.md)] Projekte, die mit Visual Studio 2015 und Visual Studio 2013 erstellt werden, diese Versionen als Ziel haben und Visual Studio 2012 nur [!INCLUDE[win8](../includes/win8-md.md)] Projekte unterstützt, die auf [!INCLUDE[win8](../includes/win8-md.md)]abzielen.|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|Sie können diese Projekte in Visual Studio Visual Studio 2013 2015 erstellen und verwenden, nachdem Sie das entsprechende Paket für die mehrstufige Ziel Installation installiert haben. Diese Projekttypen werden in Visual Studio 2010 SP1 nicht unterstützt.|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|Sie können diese Projekte in Visual Studio 2015, Visual Studio 2013 und Visual Studio 2012, aber nicht in Visual Studio 2010 SP1 erstellen und öffnen.|
|BizTalk|BizTalk Server-Projekte sind nicht mit Visual Studio 2015 oder Visual Studio 2013 kompatibel.|
|C#-/Visual Basic-Silverlight 4-Anwendung oder -Klassenbibliothek|Wenn Sie zulassen, dass Visual Studio das Projekt automatisch aktualisiert, können Sie es entweder in Visual Studio 2013 oder in Visual Studio 2012 öffnen.|
|C#/Visual Basic Webform oder Windows Form|Sie können das Projekt in Visual Studio 2013 und Visual Studio 2012 öffnen.|
|Visual Basic 6 und Visual C++ 6|Visual Studio 2012 und Visual Studio 2013 unterstützen keine Debugging-Anwendungen, die mit Visual Basic 6 C++ oder Visual 6 erstellt wurden. Verwenden Sie frühere Versionen von Visual Studio, um diese Anwendungen zu debuggen.|
|Test der codierten UI|Wenn Sie zulassen, dass Visual Studio das Projekt automatisch aktualisiert, können Sie es in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen.|
|F#|Wenn Sie zulassen, dass Visual Studio ein Projekt aktualisiert, das in Visual Studio 2010 SP1 erstellt wurde, können Sie es in Visual Studio 2013 und Visual Studio 2012 öffnen. Ein Silverlight-Projekt, das in einer älteren Version von Visual Studio erstellt wurde, kann jedoch nicht auf Visual Studio 2013 aktualisiert werden. Sie müssen stattdessen ein Silverlight-Projekt in Visual Studio 2013 erstellen und dann den Code in das Projekt kopieren. Silverlight-Projekte, die Sie in Visual Studio 2013 Ziel Silverlight 5 erstellen.|
|LightSwitch|Wenn Sie zulassen, dass Visual Studio das Projekt automatisch aktualisiert, können Sie es nur in Visual Studio 2013 öffnen.|
|Cache für lokale Datenbanken|Die Cache Vorlage für lokale Datenbanken und das Dialogfeld **Datensynchronisierung konfigurieren** sind nicht in Visual Studio 2013 enthalten. Sie können Visual Studio 2013 verwenden, um Projekte zu öffnen und auszuführen, die in [!INCLUDE[vs2010](../includes/vs2010-md.md)] erstellt wurden, wenn Microsoft-Synchronisierungs Dienste v 1.0 installiert sind. Wenn Sie diese jedoch in Visual Studio 2013 aktualisieren möchten, müssen Sie alle Änderungen manuell im Code vornehmen. Alternativ können Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)] weiterhin verwenden, um diese Projekte zu verwalten und zu aktualisieren.  Für Neuentwicklungen geben Sie das neue Synchronisierungsmodell an, das von Microsoft Synchronization Framework bereitgestellt wird. Weitere Informationen finden Sie unter [Microsoft Synchronization Framework-Developer Center](https://msdn.microsoft.com/sync/default).|
|Model View Controller-Framework|Visual Studio 2010 SP1 unterstützt nur MVC 2 und MVC 3, Visual Studio 2012 unterstützt nur MVC 3 und MVC 4, und Visual Studio 2013 unterstützt nur MVC 4. Informationen über das automatische Upgrade von MVC 2 auf MCV 3 finden Sie unter [ASP.NET MVC 3-Anwendung Upgrader](https://aspnet.codeplex.com/releases/view/59008). Informationen über das manuelle Upgrade von MVC 2 auf MVC 3 finden Sie unter [Aktualisieren eines ASP.NET MVC 2-Projekts zum ASP.NET MVC 3-Tool-Update](https://aspnet.codeplex.com/releases/view/59008). Informationen über das manuelle Upgrade von MVC3 auf MVC 4 finden Sie unter [Aktualisieren eines ASP.NET MVC 3-Projekts zu ASP.NET MVC 4](https://docs.microsoft.com/aspnet/whitepapers/mvc4-release-notes). Wenn das Projekt .NET Framework 3.5 SP1 verwendet, müssen Sie es auf .NET Framework 4. umleiten.|
|Modellierung|Wenn Sie zulassen, dass Visual Studio das Projekt automatisch aktualisiert, können Sie es in Visual Studio 2013, Visual Studio 2012 oder Visual Studio 2010 SP1 öffnen.<br /><br /> Wenn Team Foundation ein Modellierungsprojekt erstellt, versucht es, die Ebenen im Projekt zu überprüfen. In Visual Studio 2013 kann Team Foundation Build die Ebenen für ein Modellierungsprojekt, das in Visual Studio 2010 SP1 erstellt wurde, nicht validieren. In Visual Studio 2010 SP1 kann Team Foundation Build jedoch die Ebenen in einem Modellierungsprojekt überprüfen, das in Visual Studio 2013 erstellt wurde.|
|MPI-/Clusterdebugging|Wenn die gleiche Version der Laufzeit oder der Tools auf den Computern installiert ist, auf denen Visual Studio 2013, Visual Studio 2012 oder Visual Studio 2010 SP1 ausgeführt wird, können Sie dieses Projekt in allen drei Versionen öffnen.|
|MSI-Setup (.vdproj)|Dieses Projekt kann nicht in Visual Studio 2013 geöffnet werden, da es diesen Projekttyp nicht unterstützt. Es wird empfohlen, die kostenlose Bereitstellungslösung InstallShield Limited- Edition für Visual Studio (ISLE) zu verwenden, die die meisten Windows-Plattformen und Anwendungslaufzeiten direkt unterstützt. Sie können ISLE auch verwenden, um Daten und Einstellungen von Visual Studio-Installationsprogrammprojekten zu importieren. ausgeführt werden können.|
|Office 2007 VSTO|Wenn Sie das Projekt auf Office 2013 und .NET Framework 4 aktualisieren, können Sie dieses Projekt in Visual Studio 2013, Visual Studio 2012 oder Visual Studio 2010 SP1 öffnen.|
|Office 2010 VSTO|Wenn das Projekt auf die .NET Framework 4 abzielt, können Sie es in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen. Alle anderen Projekte erfordern ein unidirektionales Upgrade.|
|Umfassende Internetanwendungen (Rich Internet Applications)|Wenn Sie das Projekt aktualisieren, können Sie es in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen.|
|SharePoint 2007|Dieses Projekt kann nicht in Visual Studio 2013 geöffnet werden. Wenn Sie das Projekt jedoch manuell auf SharePoint 2010 aktualisieren, können Sie es in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen. Weitere Informationen zum Upgraden von SharePoint 2007 finden Sie unter [Migrieren von SharePoint 2007 nach SharePoint 2010 für IT-Experten](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro), [Migrationstool für SharePoint-Unternehmenssuche für SharePoint Server 2010](https://docs.microsoft.com/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|Sie können das Projekt in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen.|
|SketchFlow|Wenn Sie zulassen, dass Visual Studio das Projekt auf WPF 4.5/Silverlight 5 aktualisiert, können Sie es in Visual Studio 2012 öffnen und Visual Studio 2013.|
|[!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]-Datenbank|Sie können das Projekt in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen. Wenn Sie über eine Datenbankdatei (.mdf) verfügen, die in einer früheren Version von SQL Server erstellt wurde, müssen Sie sie auf [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] aktualisieren, bevor Sie sie mit SQL Server Express LocalDB verwenden können, die Datenbank ist jedoch nicht mehr mit früheren Versionen von SQL Server kompatibel. Wenn Sie kein Upgrade durchführen, können Sie in Visual Studio 2013 weiterhin mit der Datenbank arbeiten, indem Sie [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] auf demselben Computer installieren und verwenden. Weitere Informationen finden Sie unter [Aktualisieren von MDF-Dateien](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|Wenn [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express auf den Computern installiert ist, auf denen Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 ausgeführt wird, können Sie das Projekt in allen drei Versionen öffnen.|
|SQL Server-Berichtsprojekt|Sie können das Projekt in Visual Studio 2013 und Visual Studio 2012 öffnen. Nur im lokalen Modus (das heißt, wenn keine Verbindung zum SQL Server hergestellt wurde) rufen Sie nicht die Entwurfszeitumgebung für Steuerelemente ab, die dem Viewer in [!INCLUDE[vs2010](../includes/vs2010-md.md)]zugeordnet werden, aber das Projekt funktioniert zur Laufzeit ordnungsgemäß. **Vorsicht:**  Wenn Sie ein Feature hinzufügen, das für Visual Studio 2013 spezifisch ist, wird das Berichts Schema automatisch aktualisiert, und Sie können das Projekt in Visual Studio 2012 nicht mehr öffnen.|
|Komponententests|Sie können [!INCLUDE[TCMext](../includes/tcmext-md.md)] in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 verwenden, um Tests zu öffnen, die in einer dieser Versionen erstellt wurden.|
|Visual C++|Sie können Visual Studio 2013 verwenden, um ein C++ Projekt zu öffnen, das in Visual Studio 2012 oder Visual Studio 2010 SP1 erstellt wurde. Wenn Sie die Visual Studio 2013-Buildumgebung verwenden möchten, um ein Projekt zu erstellen, das in Visual Studio 2012 erstellt wurde, müssen beide Versionen von Visual Studio auf demselben Computer installiert sein. Weitere Informationen finden Sie unter [Vorgehensweise: Upgrade von Visual C++-Projekten auf Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) und [Visual C++-Handbuch: Portieren und Aktualisieren](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Visual Studio 2010 Web|Wenn Sie zulassen, dass Visual Studio das Projekt automatisch aktualisiert, können Sie es in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen.|
|Visual Studio 2010-Datenbank (.dbproj)|Wenn Sie das Projekt in ein SQL Server Data Tools Datenbankprojekt konvertieren, können Sie es in Visual Studio 2013 öffnen. Diese Artefakte werden von Visual Studio 2013 jedoch nicht unterstützt:<br /><br /> -   Komponententests<br />-   Datengenerierungspläne<br />-   Datenvergleichsdateien<br />-   Erweiterungen der benutzerdefinierten Regel für statische Codeanalyse<br />-   server.sqlsettings<br />-   SQLCMD-Dateien<br />-   Benutzerdefinierte Bereitstellungserweiterungen<br />-   Unvollständige Projekte (FILES-Dateien)<br /><br /> Wenn Sie SQL Server Data Tools installieren, können Sie nach der Konvertierung das Projekt in Visual Studio 2010 SP1 öffnen. Weitere Informationen finden Sie unter [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx).|
|Visual Studio 2010 Visual Database Tools|Sie können dieses Projekt in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen.|
|Visual Studio Lab Management|Sie können [!INCLUDE[TCMext](../includes/tcmext-md.md)], Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 verwenden, um Umgebungen zu öffnen, die in einer dieser Versionen erstellt wurden. Allerdings muss die Version von Microsoft Test Manager mit der Version von Team Foundation Server übereinstimmen, bevor Sie Umgebungen erstellen können.|
|Visual Studio-Makro|Dieses Projekt kann nicht in Visual Studio 2013 geöffnet werden, da es den Projekttyp nicht unterstützt.|
|Visual Studio SDK/VSIX|Nachdem Sie ein Visual Studio SDK-Projekt auf Visual Studio 2013 aktualisiert haben, kann es nicht in Visual Studio 2012 geöffnet werden. Weitere Informationen finden Sie unter [Vorgehensweise: Migrate Extensibility Projects to Visual Studio 2015 (Vorgehensweise: Migrieren von Erweiterbarkeitsprojekten nach Visual Studio 2015)](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Microsoft Azure-Tools für Visual Studio|Wenn Sie Microsoft Azure-Tools für Visual Studio, Version 2,1, verwenden, können Sie das Projekt in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen. Wenn Sie für Projekte, die auf frühere Versionen abzielen, Visual Studio das Upgrade des Projekts auf Version 2,1 zulassen, können Sie es in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen.|
|Windows Communication Foundation, Windows Presentation Foundation|Sie können dieses Projekt in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen.|
|Windows Mobile|Dieses Projekt kann nicht in Visual Studio 2013 geöffnet werden, da es den Projekttyp nicht unterstützt.|
|Windows Phone 7.1|Wenn Sie zulassen, dass Visual Studio das Projekt auf Windows Phone 8,0 aktualisiert, können Sie es in Visual Studio 2012 öffnen und Visual Studio 2013.|
|Andere|Sie können die meisten anderen Projekttypen in Visual Studio 2012, Visual Studio 2013 und Visual Studio 2010 SP1 öffnen.|
|FrontPage-Websites|Dieses Projekt kann nicht in Visual Studio 2013 geöffnet werden, da es den Projekttyp nicht unterstützt.|
|Portable Klassenbibliothek|Wenn Sie zulassen, dass Visual Studio das Projekt automatisch aktualisiert, können Sie es in Visual Studio 2013, Visual Studio 2012 oder Visual Studio 2010 SP1 öffnen.<br /><br /> -   Projekte, die auf Silverlight 4 ausgerichtet waren, verwenden nun Silverlight 5.<br />-   Projekte, die auf Windows Phone 7.0 oder Windows Phone 7.5 ausgerichtet waren, verwenden Windows Phone 8.<br />-   Projekte, die auf Xbox 360 ausgerichtet waren, verwenden Xbox 360 nicht mehr.|
|Azure-Projekte wie z. B. Clouddienst-Projekte (ccproj-Erweiterung) und Azure Resource Manager-Projekte (Cloud-Bereitstellungsprojekte) mit der deployproj-Erweiterung.|Um diese Projekttypen zu öffnen, müssen Sie zunächst das [Azure SDK für .NET](https://azure.microsoft.com/downloads/)installieren. Danach können Sie das Projekt öffnen.|

## <a name="troubleshooting-project-compatibility-issues"></a>Problembehandlung bei Projektkompatibilitätsproblemen
 Im folgenden finden Sie einige Dinge, die Sie tun können, wenn ein Projekt nicht in Visual Studio 2015 oder Visual Studio 2013 geöffnet wird:

- Wenn Sie versuchen, ein Projekt zu öffnen, das in Visual Studio 2015 oder Visual Studio 2013 nicht unterstützt wird und für das die zugehörige Version von Visual Studio nicht installiert ist, wird möglicherweise eine Meldung angezeigt, dass der Projekttyp nicht unterstützt wird. der Projekttyp wird möglicherweise im Dialogfeld **Änderungen an Projekt und Projekt Mappe prüfen** unter **nicht unterstützte** Um dieses Problem zu beheben, öffnen Sie in der Windows- **Systemsteuerung**die Seite "Programme und Funktionen", wählen Sie **Visual Studio**und dann **Ändern**, **Reparieren**aus. Anschließend können Sie die fehlende Version installieren.

- Wenn Sie versuchen, ein Projekt für eine Desktop-App in [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]zu öffnen, tritt ein Fehler auf, und eine der folgenden Meldungen wird angezeigt: „Diese Edition von Visual Studio unterstützt nur [!INCLUDE[win81](../includes/win81-md.md)]-Apps“ oder „Dieses Projekt ist mit der aktuellen Edition von Visual Studio nicht kompatibel“. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] ist auf die Entwicklung, das Testen und die Bereitstellung von Windows Store-Apps beschränkt, die für Windows 8.1 entwickelt wurden. Um ein Desktop-App-Projekt zu öffnen, müssen Sie eine Edition von Visual Studio verwenden, die diesen Projekttyp unterstützt.

   Weitere Informationen zu den Visual Studio-Editionen finden Sie unter [Microsoft Visual Studio-Produkte](https://visualstudio.microsoft.com/products/).

- Wenn Sie versuchen, ein Windows Store-App-Projekt in [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop zu öffnen, tritt ein Fehler auf. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop kann nicht zur Erstellung von Windows Store-Apps verwendet werden. Wenn Sie Windows Store-Apps erstellen möchten, können Sie auch [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]installieren. Sie können ebenfalls Visual Studio Professional 2013 verwenden, um Apps für alle Microsoft-Plattformen und das Web zu entwickeln.

- Wenn ein Projektfunktionen erfordert, die für Visual Studio 2013 spezifisch sind, kann es nicht in einer früheren Version geöffnet werden.

- Wenn Sie Visual Studio 2012 verwenden und ein Projekt öffnen möchten, das in Visual Studio 2013 erstellt wurde, können Sie das Projekt System möglicherweise so anpassen, dass Features Visual Studio 2013 integriert werden. Informationen hierzu finden Sie unter [Bewirken, dass benutzerdefinierte Projekte versionsfähig werden](../misc/making-custom-projects-version-aware.md).

  Zusätzliche Informationen zur Problembehandlung finden Sie im KB-Artikel [Visual Studio 2013-Kompatibilität](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) .

## <a name="file"></a> Dateien

Die folgende Liste gibt Aufschluss darüber, ob Visual Studio 2013 jeden Dateityp unterstützt, ob Sie die Datei in Visual Studio 2012 und Visual Studio 2010 SP1 öffnen können und ob Sie Sie ändern müssen, um die Kompatibilität zu gewährleisten.

|Dateityp|Kompatibilität|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings (XML-Dateien)|Sie können diese Dateien in Visual Studio 2012, Visual Studio 2013 und Visual Studio 2010 SP1 öffnen.|
|BizTalk-Flatfileschemen|Sie können diese Schemas zu einem BizTalk 2013-Projekt in Visual Studio 2013 hinzufügen. Wenn Sie Visual Studio 2013 mit BizTalk 2010-Projekten mit Flatfile-Schemas verwenden möchten, installieren Sie BizTalk 2013 auf dem Computer mit Visual Studio 2013. Wenn Sie das BizTalk 2010-Projekt zum ersten Mal öffnen, wird es automatisch auf das BizTalk 2013-oder Visual Studio 2013-Projekt System aktualisiert.|
|Clientberichtsdefinitionsdateien (RDLC)|Sie können diese Dateien in Visual Studio 2013 öffnen, und das Schema wird automatisch aktualisiert, wenn Sie Visual Studio 2013 Features und Steuerelemente hinzufügen.|
|Regelsätze für die Codeanalyse|Sie können diese Dateien in Visual Studio 2012, Visual Studio 2013 und Visual Studio 2010 SP1 öffnen.|
|Paketdateien für Datenebenenanwendungen|Sie können diese Dateien in Visual Studio 2013 öffnen, wenn Sie Version 2,0 oder Version 2,5 sind.|
|Debuggerdumpdateien|Sie können diese Dateien in Visual Studio 2012, Visual Studio 2013 und Visual Studio 2010 SP1 öffnen.|
|Diagrammdateien für Directed Graph Markup Language (DGML-Datei)|Sie können diese Dateien in Visual Studio 2012, Visual Studio 2013 und Visual Studio 2010 SP1 öffnen, ohne die Datei zu ändern.|
|Entity Data Model-Dateien (EDMX)|In Visual Studio 2013 können Sie eine EDMX-Datei öffnen, die auf die .NET Framework 4,5 oder .NET Framework 4 abzielt, ohne die Datei zu ändern.|
|Profiler-Berichtsdateien|Sie können die Profiler-Berichtsdateien (. vsp. vsps,. psess und. vspf) in Visual Studio 2012 öffnen und Visual Studio 2013. Eine VSPX-Datei kann nicht in Visual Studio 2010 SP1 geöffnet werden.|
|Projektmappendatei (SUO)|Sie können Visual Studio 2013 verwenden, um eine Projektmappendatei zu öffnen, die in Visual Studio 2012 oder Visual Studio 2010 SP1 erstellt wurde.|
|SQL Server Compact Edition|Visual Studio 2013 unterstützt SQL Server Compact Edition nicht.|
|SQLX-Dateien|Um diese Dateien in Visual Studio 2013 zu öffnen, müssen Sie ein unidirektionales Upgrade ausführen, die SQLX-Datei auf der Zielversion von Visual Studio bereitstellen und dann die Datei im dacpac-Format neu erstellen.|
|IntelliTrace-Protokolldateien von [!INCLUDE[vs2010](../includes/vs2010-md.md)]|Sie können diese Dateien in Visual Studio 2012, Visual Studio 2013 und Visual Studio 2010 SP1 öffnen.|
|Dateien der JavaScript-Speicheranalyse (.diagsession)|Dateien, die von älteren Versionen von Visual Studio erstellt wurden, können in Visual Studio 2013 angezeigt werden. Die in Visual Studio 2013 erstellten Dateien werden jedoch möglicherweise in Visual Studio 2012 oder Visual Studio 2010 SP1 nicht geöffnet, je nachdem, welche Informationen gesammelt wurden.|

## <a name="integration"></a> Integrationsressourcen

Möglicherweise treten Kompatibilitätsprobleme auf, wenn Sie Clients und Server aus unterschiedlichen Versionen von Visual Studio Team Foundation Server verwenden.

|Art der Integration|Kompatibilität|
|-------------------------|-------------------|
|Codeüberprüfung und Meine Arbeit|Die Funktionen "Codeüberprüfung" und "Meine Arbeit" können nicht verwendet werden, wenn Sie eine Verbindung eines [!INCLUDE[esprfound](../includes/esprfound-md.md)] -Clients mit [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)]herstellen.|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|Eine 64-Bit-Umgebung wie MSBuild oder [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] kann nicht zum Erstellen von [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] -Apps verwendet werden, die in [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]erstellt wurden.|

## <a name="see-also"></a>Siehe auch

- [Bewirken, dass benutzerdefinierte Projekte versionsfähig werden](../misc/making-custom-projects-version-aware.md)
