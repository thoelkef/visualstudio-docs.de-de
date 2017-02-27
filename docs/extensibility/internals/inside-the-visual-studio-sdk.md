---
title: "In der Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Roadmap, Integration in Visual Studio SDK"
  - "Visual Studio SDK Integrationsstrategie"
  - "Integrationsstrategie, Visual Studio SDK"
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# In der Visual Studio SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieser Abschnitt enthält detaillierte Informationen über Visual Studio\-Erweiterungen, einschließlich Visual Studio\-Architektur, Komponenten, Dienste, Schemas, Dienstprogramme und ähnliches.  
  
## Erweiterbarkeitsarchitektur  
 Die folgende Abbildung zeigt die Architektur der Visual Studio\-Erweiterbarkeit. VSPackages bieten die Funktionalität der Anwendung, die in der IDE als Dienste gemeinsam verwendet wird. Die standard\-IDE bietet außerdem eine Vielzahl von Diensten, wie z. B. <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, die Zugriff auf die IDE Windowing\-Funktionen bereitstellen.  
  
 ![Grafik zur Umgebungsarchitektur](../../extensibility/internals/media/environment.png "environment")  
Allgemeine Ansicht der Visual Studio\-Architektur  
  
## VSPackages  
 VSPackages sind Software\-Module, die bilden und Erweitern von Visual Studio mit UI\-Elemente, Dienste, Projekte, Editoren und Designer. VSPackages sind die zentralen Architektur von Visual Studio. Weitere Informationen finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md).  
  
## Visual Studio Shell  
 Die Visual Studio\-Shell stellt grundlegende Funktionen bereit und unterstützen als auch die Kommunikation zwischen den Erweiterungen der VSPackages und MEF\-Komponente. Weitere Informationen finden Sie unter [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## User Experience Guidelines  
 Wenn Sie planen, Entwerfen Sie neue Features für Visual Studio, ergreifen Sie einen Blick auf diese Grundsätze für Entwurf und Nutzbarkeit: [Visual Studio\-Richtlinien für die Gestaltung der Benutzeroberfläche](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## Befehle  
 Befehle sind Funktionen, die Aufgaben, z. B. ein Dokument zu drucken, eine Sicht aktualisieren oder Erstellen einer neuen Datei.  
  
 Wenn Sie Visual Studio erweitern, können Sie Befehle erstellen und registrieren sie mit der Visual Studio\-Shell. Sie können angeben, wie diese Befehle in der IDE, z. B. in einem Menü oder Symbolleiste angezeigt werden. In der Regel ein benutzerdefinierter Befehl angezeigt wird, auf die **Tools** Menü und einem Befehl zum Anzeigen eines Toolfensters würde angezeigt, die **Weitere Fenster** Untermenü der **Ansicht** Menü.  
  
 Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für ihn erstellen. Der Ereignishandler stellt fest, wenn der Befehl sichtbar oder aktiviert ist, können Sie den Text ändern und wird sichergestellt, dass der Befehl angemessen reagiert, wenn es aktiviert ist. In den meisten Fällen verarbeitet die IDE Befehle mithilfe der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Befehle in Visual Studio werden beginnend mit der innersten Befehlskontext, basierend auf der lokalen Auswahl, bis der äußersten Kontexts angegeben, basierend auf der globalen Auswahl behandelt. Befehle, die dem Hauptmenü hinzugefügt, stehen sofort für Skripting.  
  
 Weitere Informationen finden Sie unter [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Menüs und Symbolleisten  
 Menüs und Symbolleisten können Benutzer Befehle aufrufen. Menüs werden Zeilen oder Spalten von Befehlen, die in der Regel als einzelne Textelemente oben in einem Toolfenster angezeigt werden. Untermenüs sind sekundäre Menüs, die angezeigt werden, wenn ein Benutzer Befehle klickt, die einen kleinen Pfeil enthalten. Kontextmenüs angezeigt, wenn ein Benutzer bestimmte Elemente der Benutzeroberfläche klickt. Sind einige allgemeine Menünamen **Datei**, **Bearbeiten**, **Ansicht**, und **Fenster**. Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Symbolleisten können Zeilen oder Spalten mit Schaltflächen und andere Steuerelemente, wie Kombinationsfelder, Listenfelder und Textfelder. Symbolleisten\-Schaltflächen sind in der Regel Symbolbilder, z. B. ein Ordnersymbol für eine **geöffnete Datei** Befehl oder einen Drucker für eine **Drucken** Befehl. Alle Symbolleistenelemente sind Befehle zugeordnet. Wenn Sie eine Symbolleisten\-Schaltfläche klicken, wird der Befehl ausgeführt. Ein Dropdown\-Steuerelement ist jedes Element in der Dropdown\-Liste einen anderen Befehl zugeordnet. Einige Symbolleisten\-Steuerelemente, z. B. ein Aufteilungssteuerelement sind denkbar. Eine Seite des Steuerelements eine Symbolleisten\-Schaltfläche und die andere Seite wird ein Pfeil nach unten, der mehrere Befehle anzeigt, wenn darauf geklickt wird.  
  
## Toolfenster  
 Toolfenster werden in der IDE verwendet, um Informationen anzuzeigen.**Toolbox**, **Projektmappen\-Explorer**, **Eigenschaften** Fenster und **Webbrowser** sind Beispiele für Toolfenster.  
  
 Toolfenster bieten in der Regel verschiedene Steuerelemente, mit denen der Benutzer interagieren kann. Z. B. die **Eigenschaften** Fenster ermöglicht dem Benutzer, die Eigenschaften der Objekte festlegen, die einen bestimmten Zweck dienen. Die **Eigenschaften** Fenster ist in diesem Sinne spezialisierte, aber auch Allgemein, da es in vielen unterschiedlichen Situationen verwendet werden kann. Auf ähnliche Weise die **Ausgabe** Fenster ist spezialisiert, da dadurch textbasierten Ausgabe, aber Allgemein, da viele Subsysteme in Visual Studio zum Ausgeben der Visual Studio\-Benutzer verwendet werden können.  
  
 Betrachten Sie das folgende Bild von Visual Studio, die mehrere Toolfenster enthält.  
  
 ![Bildschirmabbildung](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Einige Toolfenster sind zusammen auf einem einzelnen Bereich angedockt, die im Projektmappen\-Explorer\-Toolfenster angezeigt und die anderen Toolfenster ausgeblendet jedoch stellt sie durch Klicken auf die Registerkarten zur Verfügung. Die Abbildung zeigt zwei andere Toolfenster, die **Fehlerliste** und **Ausgabe** Fenster angedockt zusammen auf einem einzelnen Bereich.  
  
 Außerdem ist im Hauptdokument\-Bereich, der mehrere\-Editor\-Fenster angezeigt wird. Obwohl Toolfenster in der Regel nur eine Instanz haben \(Sie können z. B. Öffnen nur eine **Projektmappen\-Explorer**\),\-Editor\-Fenster können mehrere Instanzen, von denen jeder wird verwendet, um ein separates Dokument bearbeiten, aber alle im gleichen Bereich angedockt sind. Die Abbildung zeigt einen Dokument Bereich mit zwei\-Editor\-Fenster ein Formular\-Designer\-Fenster und ein Browser\-Fenster, das die Seite anzeigt. Alle Fenster im Dokumentfenster sind verfügbar, indem Sie auf die Registerkarten, aber das Editorfenster, das editorpane.cs\-Datei enthält, wird angezeigt.  
  
 Wenn Sie Visual Studio erweitern, können Sie Tools, mit die Visual Studio\-Benutzer können Windows interagieren, mit der Erweiterung erstellen. Sie können auch eigene Editoren erstellen, mit die Visual Studio\-Benutzer Dokumente bearbeiten können. Da die Toolfenster und Editoren in Visual Studio integriert werden, müssen Sie keinen programmieren, andocken oder ordnungsgemäß auf einer Registerkarte angezeigt werden. Wenn sie in Visual Studio ordnungsgemäß registriert sind, müssen sie die Standardfeatures von Toolfenstern und Dokumentfenstern in Visual Studio automatisch. Weitere Informationen finden Sie unter [Erweitern und Anpassen von Toolfenstern](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## Dokumentfenster  
 Ein Dokumentfenster ist eine begrenzte untergeordnetes Fenster eines Fensters Multiple Document Interface \(MDI\). Dokumentfenster in der Regel werden zur Text\-Editoren, Formular\-Editoren \(auch bekannt als Designer\) oder Steuerelemente zu hosten, aber sie können auch andere funktionale Typen hosten. Die **neue Datei** enthält Beispiele für Dokument\-Windows, Visual Studio bietet, das Dialogfeld.  
  
 Die meisten Editoren sind spezifisch für eine Programmiersprache oder einen Dateityp, z. B. HTML\-Seiten Framesets, C\+\+\-Dateien, Headerdateien, oder. Durch Auswählen einer Vorlage in die **neue Datei** im Dialogfeld Benutzer dynamisch erstellt ein Dokumentfenster für den Editor für den Dateityp aus, die der Vorlage zugeordnet ist. Ein Dokumentfenster wird auch erstellt, wenn ein Benutzer eine vorhandene Datei geöffnet wird.  
  
 Dokumentfenster werden auf der MDI\-Client\-Bereich beschränkt. Jedes Dokumentfenster verfügt über eine Registerkarte am oberen Rand und Aktivierreihenfolge ist verknüpft mit anderen Fenstern, die im MDI\-Bereich geöffnet werden können. Der rechten Maustaste auf die Registerkarte im Dokumentfenster zeigt ein Kontextmenü aufrufen, die Optionen den MDI\-Bereich in mehreren horizontalen oder vertikalen Registerkartengruppen aufteilen. Aufteilen des MDI\-Bereichs können mehrere Dateien gleichzeitig angezeigt werden. Weitere Informationen finden Sie unter [Dokumentfenster](../../extensibility/internals/document-windows.md).  
  
## Editoren  
 Der Visual Studio\-Editor können Sie anpassen und verwenden es für Ihre eigenen Inhaltstyp mithilfe der Managed Extensibility Framework \(MEF\). In vielen Fällen müssen Sie nicht, ein VSPackage, erweitern Sie im Editor zu erstellen, aber wenn Sie Funktionen aus der Shell \(z. B. einen Menübefehl oder eine Tastenkombination\) einschließen möchten, eine MEF\-Erweiterung mit einem VSPackage kombinieren können.  
  
 Sie können auch einen benutzerdefinierten Editor, z. B. erstellen, lesen und Schreiben in einer Datenbank werden soll, oder wenn Sie einen Designer verwenden möchten. Sie können auch einen externen Editor wie z. B. Editor oder Microsoft WordPad. Weitere Informationen finden Sie unter [\-Editor, und Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).  
  
## Language Services  
 Wenn Sie die Visual Studio\-Editor, um neue Programmiersprachen\-Schlüsselwörter oder sogar eine neue Programmiersprache unterstützen möchten, erstellen Sie einen Sprachdienst. Jeder Sprachdienst kann bestimmte Editorfeatures vollständig, teilweise oder gar nicht implementieren. Je nachdem, wie es konfiguriert ist kann der Sprachdienst syntaxhervorhebung, Klammern, IntelliSense\-Unterstützung und andere Funktionen im Editor bereitstellen.  
  
 Das Kernstück eines Sprachdiensts sind ein Parser und Scanner. Scanner \(oder Lexer\) Elemente, die als Token bezeichnet werden eine Quelldatei unterteilt und ein Parser richtet die Beziehungen zwischen diesen Token. Wenn Sie einen Sprachdienst erstellen, müssen Sie der Parser und der Scanner implementieren, damit Visual Studio den Token und Grammatik der Programmiersprache vertraut machen können. Sie können Dienste für verwalteten oder nicht verwalteten Sprachen erstellen. Weitere Informationen finden Sie unter [Ältere Sprache Service\-Erweiterbarkeit](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## Projekte  
 In Visual Studio sind Projekte die Container, mit denen Entwickler beim Organisieren und erstellen den Quellcode und andere Ressourcen. Projekte können Sie organisieren, erstellen, Debuggen und Bereitstellen von Quellcode, Verweise auf Webdienste und Datenbanken und anderen Ressourcen. VSPackages können das Visual Studio\-Projektsystem erweitern, indem Projekttypen, Projekt\-Untertypen und benutzerdefinierte Tools.  
  
 Projekte können auch in einer Lösung, d. h. eine Gruppierung von einem oder mehreren Projekten, die zusammenarbeiten, um eine Anwendung zu erstellen, erfasst werden. Projekt\- und Status Informationen über die Projektmappe wird in zwei Projektmappendateien, die textbasierte Projektmappendatei \(.sln\) und die binären Lösung Benutzeroptionsdatei \(.suo\) gespeichert. Diese Dateien sind ähnlich wie die Gruppen\-\(.vbg\)\-Dateien, die in früheren Versionen von verwendeten [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], und der Arbeitsbereich \(.dsw\) und Optionen \(.opt\)\-Dateien, die in früheren Versionen von verwendeten [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Weitere Informationen finden Sie unter [Projekte](../../extensibility/internals/projects.md) und [Projektmappen](../../extensibility/internals/solutions.md).  
  
## Projekt\- und Elementvorlagen  
 Visual Studio enthält vordefinierte Projektvorlagen und Projektelementvorlagen. Sie können auch eigene Vorlagen oder Vorlagen aus der Community zu erhalten und diese dann in Visual Studio integrieren. Die [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) ist die Anlaufstelle für Vorlagen und Erweiterungen.  
  
 Vorlagen enthalten die Projektstruktur und die grundlegenden Dateien, die erforderlich sind, um eine bestimmte Art von Anwendung, Control, Bibliothek oder Klasse zu erstellen. Wenn Sie Software entwickeln, die eine der Vorlagen ähnelt möchten, erstellen Sie ein Projekt, das auf der Vorlage basiert, und ändern Sie dann die Dateien in diesem Projekt.  
  
> [!NOTE]
>  Diese Architektur wird nicht unterstützt für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte. Informationen zum Erstellen von [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] \-Projektvorlagen, finden Sie unter [Entwerfen eines Assistenten](/visual-cpp/ide/designing-a-wizard).  
  
 Weitere Informationen finden Sie unter [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## Eigenschaften und Optionen  
 Die **Eigenschaften** Fenster zeigt die Eigenschaften für einzelne oder mehrere ausgewählte Elemente: [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md) Optionsseiten enthalten Optionen, die einer bestimmten Komponente, wie z. B. einer Programmiersprache oder ein VSPackage betreffen: [Optionen und Optionen \(Seiten\)](../../extensibility/internals/options-and-options-pages.md). Einstellungen sind im allgemeinen UI\-bezogene Funktionen, die importiert und exportiert werden können: [Unterstützung für Benutzereinstellungen](../../extensibility/internals/support-for-user-settings.md).  
  
## Visual Studio\-Dienste  
 Ein Dienst stellt einen bestimmten Satz von Schnittstellen für die Komponenten nutzen. Visual Studio bietet eine Reihe von Diensten, die von Komponenten, einschließlich Erweiterungen verwendet werden kann. Visual Studio\-Dienste ermöglichen z. B. Toolfenster angezeigt oder ausgeblendet dynamisch Aktivieren des Zugriffs auf Hilfe, Statusleiste oder UI\-Ereignisse. Der Visual Studio\-Editor stellt auch Dienste, die von Editor\-Erweiterungen importiert werden können. Weitere Informationen finden Sie unter [Verwendung und Bereitstellung von Diensten](../../extensibility/using-and-providing-services.md).  
  
## Debugger  
 Der Debugger ist die Benutzeroberfläche der sprachspezifische Komponenten zum Remotedebuggen. Wenn Sie einen neuen Sprachdienst erstellt haben, müssen Sie zum Erstellen einer bestimmten Debugmodul an den Debugger zu verknüpfen. Weitere Informationen finden Sie unter [Visual Studio\-Debugger\-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## Quellcodeverwaltung  
 Informationen zum Implementieren eines Plug\-in\-Datenquellen\-Steuerelement oder ein VSPackage, finden Sie unter [Quellcodeverwaltung](../../extensibility/internals/source-control.md).  
  
## Assistenten  
 Sie können einen Assistenten in Verbindung mit einen neuen Projekttyp erstellen, damit der Assistent hilft Ihren Benutzern fundierter, wenn sie ein neues Projekt dieses Typs erstellen. Weitere Informationen finden Sie unter [Assistenten](../../extensibility/internals/wizards.md).  
  
## Benutzerdefinierte Tools  
 Benutzerdefinierte Tools können Sie ein Tool mit einem Element in einem Projekt zuordnen, und dieses Tool ausführen, wenn die Datei gespeichert wird. Weitere Informationen finden Sie unter [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).  
  
## VSSDK\-Dienstprogramme  
 VSSDK umfasst eine Reihe von Dienstprogrammen, die Sie möglicherweise mit verschiedenen Aspekten des VSPackages arbeiten benötigen. Weitere Informationen finden Sie unter [VSSDK\-Dienstprogramme](../../extensibility/internals/vssdk-utilities.md).  
  
## Verwenden von Windows Installer  
 In einigen Fällen müssen Sie das VSIX\-Installationsprogramm, sondern die Windows Installer verwenden: Sie möchten z. B. in die Registrierung geschrieben. Informationen zum Verwenden von Windows Installer mit den Erweiterungen finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## Hilfe\-Viewer  
 Sie können eigene Hilfe und die F1\-Seiten in Help Viewer integrieren. Weitere Informationen finden Sie unter [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).