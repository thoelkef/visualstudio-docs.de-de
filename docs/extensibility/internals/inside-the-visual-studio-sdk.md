---
title: In der Visual Studio SDK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebba0ea11781a4b5a3d01aabb718b0ad778daab9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="inside-the-visual-studio-sdk"></a>Im Visual Studio SDK
Dieser Abschnitt enthält ausführliche Informationen zu Visual Studio-Erweiterungen, einschließlich Visual Studio-Architektur, Komponenten, Dienste, Schemas, Dienstprogramme und Like.  
  
## <a name="extensibility-architecture"></a>Erweiterbarkeitsarchitektur  
 Die folgende Abbildung zeigt die Architektur der Visual Studio-Erweiterbarkeit. VSPackages bieten die Funktionalität der Anwendung, die in der IDE als Dienste gemeinsam verwendet wird. Die standard-IDE verfügt zudem über eine Breite Palette von Diensten, z. B. <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, die Zugriff auf den Funktionsumfang der IDE Windowing bereitstellen.  
  
 ![Grafik zur Umgebungsarchitektur](../../extensibility/internals/media/environment.gif "Umgebung")  
Generalisierte Überblick über die Visual Studio-Architektur  
  
## <a name="vspackages"></a>VSPackages  
 VSPackages sind Softwaremodule, die Visual Studio um Benutzeroberflächenelemente, Dienste, Projekte, Editoren und Designer erweitern. VSPackages sind die zentrale architektonische Einheit von Visual Studio. Weitere Informationen finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 Die Visual Studio-Shell stellt grundlegende Funktionalität bereit und Cross-Kommunikation zwischen der Komponente VSPackages und MEF-Erweiterungen unterstützen. Weitere Informationen finden Sie unter [Visual Studio-Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Richtlinien zur Benutzerfreundlichkeit  
 Wenn Sie planen, Entwerfen neue Features für Visual Studio, Sie sollten sehen Sie sich diese Richtlinien für Design und Nutzbarkeit Tipps: [Visual Studio-Umgebung Leitfäden](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Befehle  
 Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können.  
  
 Wenn Sie Visual Studio erweitern, können Sie Befehle erstellen und registrieren sie mit der Visual Studio-Shell. Sie können angeben, wie diese Befehle in der IDE, z. B. in einem Menü oder die Symbolleiste angezeigt werden. Ein benutzerdefinierter Befehl erscheint in der Regel auf die **Tools** Menü und einen Befehl für die Anzeige eines Toolfensters angezeigt würde, auf die **Weitere Fenster** Untermenü die **Ansicht** im Menü.  
  
 Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für ihn erstellen. Der Ereignishandler bestimmt, wenn der Befehl angezeigt oder aktiviert, können Sie den zugehörigen Text zu ändern und stellt sicher, dass der Befehl entsprechend reagiert, wenn es aktiviert wird. In den meisten Fällen verarbeitet die IDE Befehle mithilfe der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Befehle in Visual Studio werden verarbeitet, beginnend mit dem innersten Befehlskontext, basierend auf der lokalen Auswahl, und es wird bis zum äußersten Kontext, basierend auf der globalen Auswahl. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar.  
  
 Weitere Informationen finden Sie unter [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menüs und Symbolleisten  
 Menüs und Symbolleisten bieten eine Möglichkeit für Benutzer, die Befehle aufrufen. Menüs sind Zeilen oder Spalten von Befehlen, die in der Regel als einzelne Elemente am Anfang eines Toolfensters angezeigt werden. Untermenüs sind sekundäre Menüs, die angezeigt werden, wenn ein Benutzer Befehle klickt, die einen kleinen Pfeil enthalten. Kontextmenüs angezeigt, wenn ein Benutzer auf bestimmte Elemente der Benutzeroberfläche klickt. Einige allgemeine Menünamen sind **Datei**, **bearbeiten**, **Ansicht**, und **Fenster**. Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Symbolleisten sind Zeilen oder Spalten mit Schaltflächen und andere Steuerelemente wie Kombinationsfelder, Listenfelder und Textfelder. Symbolleistenschaltflächen weisen normalerweise Symbolbilder, z. B. ein Ordnersymbol für eine **geöffnete Datei** Befehl oder einen Drucker für eine **Drucken** Befehl. Alle Symbolleistenelemente sind Befehle zugeordnet. Wenn Sie eine Symbolleisten-Schaltfläche klicken, wird der zugeordnete Befehl ausgeführt. Bei einem Dropdown-Steuerelement für jedes Element in der Dropdown-Liste einen anderen Befehl zugeordnet ist. Einige Symbolleisten-Steuerelemente, z. B. mit einem Splittersteuerelement sind Hybriden. Eine Seite des Steuerelements eine Symbolleistenschaltfläche und die andere Seite wird ein Pfeil nach unten, in dem mehrere Befehle angezeigt, wenn darauf geklickt wird.  
  
## <a name="tool-windows"></a>Toolfenster  
 Toolfenster werden in der IDE verwendet, um Informationen anzuzeigen. **Toolbox**, **Projektmappen-Explorer**, **Eigenschaften** Fenster und **Webbrowser** sind Beispiele für Toolfenster.  
  
 Toolfenster können in der Regel verschiedene Steuerelemente, mit denen der Benutzer interagieren kann. Für die Instanz, die **Eigenschaften** Fenster ermöglicht es dem Benutzer, die Eigenschaften der Objekte festlegen, die einen bestimmten Zweck dienen. Die **Eigenschaften** Fenster ist in diesem Sinn spezielle, aber auch allgemeine, da es in vielen unterschiedlichen Situationen verwendet werden kann. Auf ähnliche Weise die **Ausgabe** Fenster spezialisiert ist, da diese textbasierten Ausgabe, aber die allgemeine bietet, da viele Subsysteme in Visual Studio zum Bereitstellen von Ausgabe für den Visual Studio-Benutzer verwendet werden können.  
  
 Betrachten Sie das folgende Bild von Visual Studio, die mehrere Toolfenster enthält.  
  
 ![Screenshot](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Einige Toolfenster sind zusammen auf einem einzelnen Bereich angedockt, die zeigt der Projektmappen-Explorer-Toolfenster an und blendet die anderen Toolfenster, jedoch werden sie durch Klicken auf die Registerkarten verfügbar gemacht. Die Abbildung zeigt zwei andere Toolfenster, die **Fehlerliste** und **Ausgabe** Fenster zusammen auf einem einzelnen Bereich angedockt.  
  
 Außerdem wird dargestellt Bereich Hauptspeicherorte für Dokumente, in der mehrere-Editor-Fenster angezeigt. Obwohl Toolfenster in der Regel nur eine Instanz haben (Sie können z. B. Öffnen nur eine **Projektmappen-Explorer**),-Editor-Fenster können mehrere Instanzen, von denen jeder wird verwendet, um ein separates Dokument bearbeiten, aber alle angedockt werden der gleiche Bereich. Das Bild zeigt ein Dokumentfenster, dessen zwei Editorfenster, ein Formular-Designer-Fenster und ein Browserfenster, in der die Startseite angezeigt. Alle Fenster im Dokumentfenster sind verfügbar, indem Sie auf die Registerkarten, aber im Editor-Fenster, das EditorPane.cs-Datei enthält ist, sichtbar und aktiv.  
  
 Wenn Sie Visual Studio erweitern, können Sie Tools, die Interaktion von Windows, mit die Visual Studio-Benutzer können mit der Erweiterung erstellen. Sie können auch eigene Editoren erstellen, mit die Visual Studio-Benutzer Dokumente bearbeiten können. Da Ihr Toolfenster und Editoren in Visual Studio integriert werden, müssen Sie keinen Programmieren zu andocken oder ordnungsgemäß auf einer Registerkarte angezeigt werden. Wenn sie in Visual Studio ordnungsgemäß registriert sind, müssen sie die Tabellen enthalten typische Features von Toolfenstern und Dokumentfenstern in Visual Studio automatisch. Weitere Informationen finden Sie unter [Extending und Anpassen von Toolfenstern](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Dokumentfenster  
 Ein Dokumentfenster ist eine begrenzte untergeordnetes Fenster eines Fensters Multiple Document Interface (MDI). Dokumentfenster in der Regel werden verwendet, um Text-Editoren, Formular-Editoren (auch bekannt als "Designer") oder Edit-Steuerelemente hosten, aber sie können auch andere funktionale Typen hosten. Die **neue Datei** Dialogfeld enthält Beispiele von Dokumentfenstern, die Visual Studio bereitstellt.  
  
 Die meisten Editoren beziehen sich auf einer Programmiersprache Ihrer Wahl oder in einen Dateityp, z. B. HTML-Seiten, Framesets, C++-Dateien oder Headerdateien. Durch Auswählen einer Vorlage in der **neue Datei** (Dialogfeld), ein Benutzer erstellt dynamisch ein Dokumentfenster für den Editor für den Dateityp, der mit der Vorlage zugeordnet ist. Ein Dokumentfenster wird auch erstellt, wenn ein Benutzer eine vorhandene Datei geöffnet wird.  
  
 Dokumentfenster werden auf der MDI-Client-Bereich beschränkt. Jedes Dokumentfenster verfügt über die Registerkarte am oberen Rand und Reihenfolge der Registerkarten mit anderen Fenstern, die im Bereich MDI Öffnen möglicherweise verknüpft ist. Der rechten Maustaste auf die Registerkarte im Dokumentfenster wird ein Kontextmenü die Optionen zum Aufteilen von MDI-Bereich in mehrere horizontale oder vertikale Registerkartengruppen enthalten angezeigt. Aufteilen des MDI-Bereichs können mehrere Dateien gleichzeitig angezeigt werden. Weitere Informationen finden Sie unter [Dokumentfenster](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Editoren  
 Der Visual Studio-Editor können Sie anpassen und verwenden es für Ihre eigenen Typ von Inhalt mithilfe der Managed Extensibility Framework (MEF). In vielen Fällen müssen Sie nicht, ein VSPackage zum Erweitern im Editors zu erstellen, aber wenn Sie Funktionen in der Befehlsshell (z. B. einen Menübefehl oder eine Tastenkombination) einschließen möchten, eine MEF-Erweiterung mit einem VSPackage kombinieren können.  
  
 Sie können auch einen benutzerdefinierten Editor, z. B. erstellen, wenn Sie möchten, lesen und Schreiben in einer Datenbank oder wenn Sie einen Designer verwenden möchten. Sie können auch einen externen Editor, z. B. Editor oder Microsoft WordPad. Weitere Informationen finden Sie unter [-Editor und Dienst Spracherweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Dienste für Sprachen  
 Wenn Sie die Visual Studio-Editor zur Unterstützung von neuen Programmiersprachen-Schlüsselwörter oder sogar eine neue Programmiersprache möchten, erstellen Sie einen Sprachdienst. Jeder Sprachdienst kann bestimmte Features im Editor vollständig, teilweise oder gar nicht implementieren. Je nachdem, wie es konfiguriert ist kann der Sprachdienst syntaxhervorhebung, Klammer, IntelliSense-Unterstützung und anderen Features im Editor bereitstellen.  
  
 Das Herzstück des einen Sprachdienst sind ein Parser und einem Scanner. Scanner (oder Lexer) dividiert eine Quelldatei in Elementen, die als Token bezeichnet werden und ein Parser stellt die Beziehungen zwischen diesen Token her. Wenn Sie einen Sprachdienst erstellen, müssen Sie der Parser und der Scanner implementieren, sodass Visual Studio, der Token und die Grammatik der Sprache weiß. Sie können Dienste für verwalteten oder nicht verwalteten Sprachen erstellen. Weitere Informationen finden Sie unter [Legacy Language Service Erweiterbarkeit](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Projekte  
 In Visual Studio sind Projekte die Container, mit denen Entwickler zum Organisieren und erstellen den Quellcode und andere Ressourcen. Projekte können Sie zu organisieren, erstellen, Debuggen und Bereitstellen von Quellcode, Verweise auf Webdienste und Datenbanken und anderen Ressourcen. VSPackages können die Visual Studio-Projektsystem erweitern, indem Projekttypen, Projekt-Untertypen und benutzerdefinierte Tools.  
  
 Projekte können auch in einer Lösung erfasst werden, also eine Gruppierung von einem oder mehreren Projekten, die zum Erstellen einer Anwendung zusammenarbeiten. Projekt- und Status Informationen über die Projektmappe wird in zwei berichtsprojektmappen-Dateien, die textbasierte Projektmappendatei (sln) und die binären Projektmappendatei Benutzer Option (SUO) gespeichert. Diese Dateien sind ähnlich wie die (.vbg)-Gruppendateien, die in früheren Versionen verwendet wurden [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], und den Arbeitsbereich (dsw) und den Benutzer ' Optionen ' (.opt)-Dateien, die in früheren Versionen verwendet wurden [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Weitere Informationen finden Sie unter [Projekte](../../extensibility/internals/projects.md) und [Lösungen](../../extensibility/internals/solutions.md).  
  
## <a name="project-and-item-templates"></a>Projekt- und Elementvorlagen  
 Visual Studio enthält vordefinierter Projekt-und Elementvorlagen und Projektelementvorlagen. Sie können auch eigene Vorlagen erstellen oder Abrufen von Vorlagen aus der Community und sie dann in Visual Studio integrieren. Die [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) bietet die Möglichkeit zum Vorlagen und -Erweiterungen finden Sie unter.  
  
 Vorlagen enthalten die Projektstruktur und die grundlegenden Dateien, die erforderlich sind, um eine bestimmte Art von Anwendung, Control, Bibliothek oder Klasse zu erstellen. Wenn Sie Software entwickeln, die eine der Vorlagen ähnelt möchten, erstellen Sie ein Projekt, das auf der Vorlage basiert, und ändern Sie die Dateien in diesem Projekt.  
  
> [!NOTE]
>  Diese Architektur wird nicht unterstützt für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte. Informationen zum Erstellen von [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] -Projektvorlagen, finden Sie unter [Entwerfen eines Assistenten](/cpp/ide/designing-a-wizard).  
  
 Weitere Informationen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Eigenschaften und Optionen  
 Die **Eigenschaften** Fenster zeigt die Eigenschaften der einzelnen oder mehreren gewählten Elementen: [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md) Optionsseiten enthalten Gruppen von Optionen, die einer bestimmten Komponente, wie z. B. betreffen ein Sprache oder ein VSPackage Programmieren: [Optionen und Seiten für Optionen](../../extensibility/internals/options-and-options-pages.md). Einstellungen sind im Allgemeinen auf die Benutzeroberfläche bezogenen Funktionen, die nicht importiert und exportiert werden können: [Unterstützung für Benutzereinstellungen](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Visual Studio-Dienste  
 Einen Dienst bereitstellt, einen bestimmten Satz von Schnittstellen für die Komponenten nutzen. Visual Studio bietet eine Reihe von Diensten, die von Komponenten, einschließlich Erweiterungen verwendet werden kann. Visual Studio-Dienste aktivieren beispielsweise Toolfenster angezeigt werden, oder Aktivieren des Zugriffs auf Hilfe, Statusleiste oder Benutzeroberflächenereignisse dynamisch, ausgeblendet. Der Visual Studio-Editor stellt auch Dienste, die durch die editorerweiterungen importiert werden können. Weitere Informationen finden Sie unter [verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Debugger  
 Der Debugger ist die Benutzeroberfläche der sprachspezifischen Debuggerkomponenten. Wenn Sie einen neuen Sprachdiensts erstellt haben, müssen Sie zum Erstellen einer bestimmten Debugmodul an den Debugger zu verknüpfen. Weitere Informationen finden Sie unter [Visual Studio-Debugger-Erweiterbarkeits](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Quellcodeverwaltung  
 Informationen zur Implementierung einer Plug-in-Datenquellen-Steuerelement oder ein VSPackage finden Sie unter [Quellcodeverwaltung](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Assistenten  
 Sie können einen Assistenten in Verbindung mit einem neuen Projekttyp erstellen, damit der Assistent hilft stellen Ihre Benutzer die richtigen Entscheidungen zu, wenn sie ein neues Projekt des betreffenden Typs erstellen. Weitere Informationen finden Sie unter [Assistenten](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Benutzerdefinierte Tools  
 Benutzerdefinierte Tools können Sie ein Element in einem Projekt ein Tool zuordnen, und führen Sie dieses Tool aus, bei jedem Speichern die Datei. Weitere Informationen finden Sie unter [benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>VSSDK-Hilfsprogramme  
 VSSDK umfasst eine Reihe von Dienstprogrammen, die Sie benötigen möglicherweise, um verschiedene Aspekte von VSPackages verwenden. Weitere Informationen finden Sie unter [VSSDK Dienstprogramme](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>Mithilfe von Windows Installer  
 In einigen Fällen müssen Sie möglicherweise Windows Installer, anstatt das VSIX-Installationsprogramm verwenden: Sie möchten z. B. in der Registrierung geschrieben werden. Informationen zur Verwendung von Windows Installer mit Ihre Erweiterungen finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Help Viewer  
 Sie können eigene Hilfe und die F1-Seiten in Help Viewer integrieren. Weitere Informationen finden Sie unter [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).