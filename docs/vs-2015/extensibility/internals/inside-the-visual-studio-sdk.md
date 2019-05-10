---
title: In Visual Studio SDK | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c6c7bb6d149281048d281cb7af13fe51d75ffd5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443895"
---
# <a name="inside-the-visual-studio-sdk"></a>Im Visual Studio SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dieser Abschnitt enthält ausführliche Informationen zu Visual Studio-Erweiterungen, einschließlich Visual Studio-Architektur, Komponenten, Dienste, Schemas, Hilfsprogramme und ähnliches.  
  
## <a name="extensibility-architecture"></a>Architektur der Erweiterbarkeit  
 Die folgende Abbildung zeigt die Architektur der Visual Studio-Erweiterbarkeit. VSPackages bieten die Funktionalität der Anwendung, die in der IDE als Dienste gemeinsam verwendet wird. Die standard-IDE bietet außerdem eine Vielzahl von Diensten, wie z. B. <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, die Zugriff auf die IDE-Windowing-Funktionen bereitstellen.  
  
 ![Grafik zur Umgebungsarchitektur](../../extensibility/internals/media/environment.gif "Umgebung")  
Generalisierte Überblick über die Architektur der Visual Studio  
  
## <a name="vspackages"></a>VSPackages  
 VSPackages sind Softwaremodule, die Visual Studio um Benutzeroberflächenelemente, Dienste, Projekte, Editoren und Designer erweitern. VSPackages sind die zentrale architektonische Einheit von Visual Studio. Weitere Informationen finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 Die Visual Studio-Shell stellt grundlegende Funktionalität bereit und unterstützt als auch die Kommunikation zwischen der Erweiterungen der VSPackages und MEF-Komponente. Weitere Informationen finden Sie unter [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Richtlinien zur Benutzerfreundlichkeit  
 Wenn Sie beabsichtigen, neuen Features für Visual Studio entwickeln, sollten Sie diese Richtlinien für Design und benutzerfreundlichkeit Tipps ansehen: [Visual Studio User Experience Guidelines](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Befehle  
 Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können.  
  
 Wenn Sie Visual Studio erweitern, können Sie Befehle erstellen und registrieren sie mit der Visual Studio-Shell. Sie können angeben, wie diese Befehle in der IDE, z. B. in einem Menü oder Symbolleiste angezeigt werden. In der Regel ein benutzerdefinierter Befehl angezeigt wird, auf die **Tools** Menü und einen Befehl zum Anzeigen eines Toolfensters würde angezeigt, die **andere Windows** Untermenü die **Ansicht** Menü.  
  
 Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für ihn erstellen. Der Ereignishandler bestimmt, wenn der Befehl angezeigt oder aktiviert, können Sie die zugehörigen Text zu ändern, und stellt sicher, dass der Befehl entsprechend reagiert, wenn es aktiviert ist. In den meisten Fällen verarbeitet die IDE Befehle mit den <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Befehle in Visual Studio erfolgt, beginnend mit dem innersten Befehlskontext, basierend auf der lokalen Auswahl, und Sie den Vorgang fortsetzen, bis zum äußersten Kontext, basierend auf der globalen Auswahl. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar.  
  
 Weitere Informationen finden Sie unter [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menüs und Symbolleisten  
 Bieten eine Möglichkeit für Benutzer zum Aufrufen der Befehle, Menüs und Symbolleisten. Menüs sind Zeilen oder Spalten von Befehlen, die in der Regel als einzelne Elemente am Anfang eines Toolfensters angezeigt werden. Untermenüs werden sekundäre Menüs, die angezeigt werden, wenn ein Benutzer Befehle klickt, die einen kleinen Pfeil enthalten. Kontextmenüs angezeigt werden, wenn ein Benutzer auf bestimmte Elemente der Benutzeroberfläche klickt. Einige allgemeine Menünamen sind **Datei**, **bearbeiten**, **Ansicht**, und **Fenster**. Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Symbolleisten sind Zeilen oder Spalten mit Schaltflächen und andere Steuerelemente wie Kombinationsfelder, Listenfelder und Textfelder. Symbolleistenschaltflächen weisen normalerweise Symbolbilder, z. B. ein Ordnersymbol für eine **geöffnete Datei** Befehl oder einen Drucker für eine **Drucken** Befehl. Alle Symbolleistenelemente sind Befehle zugeordnet. Wenn Sie eine Symbolleisten-Schaltfläche klicken, wird der zugeordnete Befehl ausgeführt. Im Fall einer Dropdown-Steuerelement für jedes Element in der Dropdownliste einen anderen Befehl zugeordnet ist. Eine Symbolleisten-Steuerelemente, z. B. einem Splittersteuerelement, sind eine Mischung. Eine Seite des Steuerelements eine Symbolleistenschaltfläche und die andere Seite wird ein Pfeil nach unten, in dem mehrere Befehle angezeigt, wenn darauf geklickt wird.  
  
## <a name="tool-windows"></a>Toolfenster  
 Toolfenster werden in der IDE verwendet, um Informationen anzuzeigen. **Toolbox**, **Projektmappen-Explorer**, **Eigenschaften** Fenster und **Webbrowser** sind Beispiele für Toolfenster.  
  
 Toolfenster bieten in der Regel verschiedene Steuerelemente, mit denen der Benutzer interagieren kann. Z. B. die **Eigenschaften** Fenster ermöglicht dem Benutzer, die Eigenschaften der Objekte, die einen bestimmten Zweck dienen, festgelegt. Die **Eigenschaften** Fenster ist in diesem Sinne spezialisierte, aber auch allgemeine, da es in vielen unterschiedlichen Situationen verwendet werden kann. Auf ähnliche Weise die **Ausgabe** Fenster ist darauf spezialisiert, da sie textbasierte Ausgabe ist jedoch Allgemein bietet, da es sich bei vielen Subsystemen in Visual Studio verwenden können, um Ausgabe für Visual Studio-Benutzer bereitzustellen.  
  
 Betrachten Sie das folgende Bild von Visual Studio, die mehrere Toolfenster enthält.  
  
 ![Screenshot](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Einige Toolfenster sind zusammen auf einem einzelnen Bereich angedockt, die zeigt das Toolfenster des Projektmappen-Explorer an und blendet Sie aus der andere Toolfenster, jedoch stellt sie durch Klicken auf die Registerkarten zur Verfügung. Die Abbildung zeigt zwei andere Toolfenster, die **Fehlerliste** und **Ausgabe** auf einem zentralen Fensterbereich zusammen angedockten Fenster.  
  
 Außerdem wird dargestellt im Hauptabschnitt des Dokuments Bereich mehrere-Editor-Fenster angezeigt. Obwohl Toolfenster in der Regel nur eine Instanz haben (Sie können z. B. Öffnen nur eine **Projektmappen-Explorer**),-Editor-Fenster können mehrere Instanzen, von denen jeder wird verwendet, um ein separates Dokument zu bearbeiten, aber alle angedockt werden haben der gleiche Bereich. Die Abbildung zeigt ein Dokumentfenster, dessen zwei Editorfenster, ein Formular-Designer-Fenster und ein Browserfenster, das die Startseite zeigt. Alle Fenster in den Aufgabenbereich durch Klicken auf die Registerkarten verfügbar sind, aber im Editor-Fenster, das EditorPane.cs-Datei enthält ist sichtbar und aktiv.  
  
 Wenn Sie Visual Studio erweitern, können Sie die Tool-Fenster, mit denen Visual Studio-Benutzer interagieren mit der Erweiterung erstellen. Sie können auch Ihren eigenen Editor erstellen, mit denen Sie Visual Studio-Benutzer, die Dokumente bearbeiten können. Da Ihr Toolfenster und Editoren in Visual Studio integriert werden, müssen Sie keinen programmieren, andocken oder ordnungsgemäß auf einer Registerkarte angezeigt werden. Wenn sie in Visual Studio ordnungsgemäß registriert sind, müssen sie den üblichen Features von Toolfenstern und Dokumentfenstern in Visual Studio automatisch. Weitere Informationen finden Sie unter [erweitern und Anpassen von Tool Windows](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Dokumentfenster  
 Ein Dokumentfenster wird ein gerahmter untergeordnete Fenster eines Fensters Multiple Document Interface (MDI). Dokumentfenster in der Regel werden verwendet, um Text-Editoren, Formular-Editoren (auch bekannt als "Designer") oder Steuerelemente zu hosten, aber sie können auch andere funktionale Typen hosten. Die **neue Datei** Dialogfeld enthält Beispiele von Dokumentfenstern, die Visual Studio bereitstellt.  
  
 Die meisten Editoren beziehen sich auf einer Programmiersprache oder in einen Dateityp, z. B. HTML-Seiten, Framesets, C++-Dateien oder Headerdateien. Durch Auswahl einer Vorlage in der **neue Datei** im Dialogfeld Benutzer dynamisch erstellt ein Dokumentfenster für den Editor für den Dateityp, der mit der Vorlage zugeordnet ist. Ein Dokumentfenster wird auch erstellt, wenn ein Benutzer eine vorhandene Datei geöffnet wird.  
  
 Dokumentfenster sind auf der MDI-Client-Bereich beschränkt. Jedes Dokumentfenster verfügt über eine Registerkarte am oberen Rand und Tab-Reihenfolge zu anderen Fenstern, die im Bereich MDI Öffnen möglicherweise verknüpft ist. Mit der rechten Maustaste in der Registerkarte im Dokumentfenster zeigt ein Kontextmenü aufrufen, die den MDI-Bereich in mehrere horizontale oder vertikale Registerkartengruppen unterteilen enthält. Aufteilen des MDI-Bereichs können mehrere Dateien gleichzeitig angezeigt werden. Weitere Informationen finden Sie unter [Dokument Windows](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Editoren  
 Visual Studio-Editor können Sie anpassen und verwenden sie für Ihre eigene Art von Inhalt über das Managed Extensibility Framework (MEF). In vielen Fällen müssen Sie sich nicht um ein VSPackage zum Erweitern des Editors zu erstellen, auch wenn Sie Folgendes: Wenn Sie Features aus der Shell (z. B. einen Menübefehl oder eine Tastenkombination) zählen möchten, können Sie eine MEF-Erweiterung mit einem VSPackage kombinieren.  
  
 Sie können auch einen benutzerdefinierten Editor, z. B. erstellen, wenn Sie möchten, lesen und Schreiben in einer Datenbank oder einen Designer verwenden möchten. Sie können auch einen externen Editor wie Editor oder WordPad von Microsoft verwenden. Weitere Informationen finden Sie unter [-Editor und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Sprachdienste  
 Wenn Sie Visual Studio-Editor zur Unterstützung von neuen Programmiersprachen-Schlüsselwörter oder sogar eine neue Programmiersprache möchten, erstellen Sie einen Sprachdienst. Jeder Sprachdienst kann bestimmte-Editor-Funktionen vollständig, teilweise oder überhaupt nicht implementieren. Je nachdem, wie es konfiguriert ist kann der Sprachdienst syntaxhervorhebung, zugehörige Klammern, IntelliSense-Unterstützung und andere Funktionen im Editor bereitstellen.  
  
 Das Herzstück von einem Sprachdienst sind ein Parser und Scanner. Scanner (oder Lexer) teilt eine Quelldatei in Elemente, die als Token bezeichnet werden, und ein Parser stellt die Beziehungen zwischen diesen Token her. Wenn Sie einen Sprachdienst erstellen, müssen Sie der Parser und die Überprüfung implementieren, damit Visual Studio die Token und die Grammatik der Sprache verstehen können. Sie können die Dienste für verwalteten oder nicht verwalteten Sprachen erstellen. Weitere Informationen finden Sie unter [Erweiterbarkeit von Legacysprachdiensten Legacy](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Projekte  
 In Visual Studio sind Projekte die Container, mit denen Entwickler zum Organisieren und den Quellcode und weitere Ressourcen zu erstellen. Lassen Sie organisieren, erstellen, Debuggen und Bereitstellen von Quellcode-Projekte, Verweise auf Webdienste und Datenbanken und andere Ressourcen. VSPackages können die Visual Studio-Projektsystem erweitern, indem Projekttypen, Projektuntertypen und benutzerdefinierte Tools.  
  
 Projekte können auch in einer Lösung erfasst werden, eine Gruppierung von ein oder mehrere Projekte, die zusammenarbeiten, um eine Anwendung zu erstellen. Informationen zum Projekt und zum Status, die der Projektmappe gehört wird in zwei Projektmappendateien, die textbasierte Projektmappendatei (.sln) und die binären Lösung Benutzeroptionsdatei (SUO) gespeichert. Diese Dateien sind ähnlich wie die (vbg)-Gruppendateien, die in früheren Versionen von verwendeten [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], und der Arbeitsbereich (.dsw) und der Benutzer "Optionen" (.opt)-Dateien, die in früheren Versionen von verwendeten [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 Weitere Informationen finden Sie unter [Projekte](../../extensibility/internals/projects.md) und [Lösungen](../../extensibility/internals/solutions-overview.md).  
  
## <a name="project-and-item-templates"></a>Projekt- und Elementvorlagen  
 Visual Studio enthält die vordefinierten Projektvorlagen und Projektelementvorlagen. Sie können stellen Sie außerdem Ihre eigenen Vorlagen oder Vorlagen aus der Community erhalten und diese dann in Visual Studio integrieren. Die [MSDN Code Gallery](https://code.msdn.microsoft.com/site/search?query=visual%20studio) ist die Anlaufstelle für Vorlagen und Erweiterungen.  
  
 Vorlagen enthalten die Projektstruktur und den grundlegenden Dateien, die erforderlich sind, um eine bestimmte Art von Anwendung "," Steuerelement ","-Bibliothek "oder"-Klasse zu erstellen. Wenn Sie Software entwickeln, die eine der Vorlagen gleicht möchten, erstellen Sie ein Projekt, das in der Vorlage basiert, und ändern Sie dann die Dateien in diesem Projekt.  
  
> [!NOTE]
> Diese Architektur wird nicht unterstützt, für die [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Projekte. Informationen über das Erstellen [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] -Projektvorlagen, finden Sie unter [Entwerfen eines Assistenten](http://msdn.microsoft.com/library/a7c0be7e-9297-4fed-83e3-5645c896d56b).  
  
 Weitere Informationen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Eigenschaften und Optionen  
 Die **Eigenschaften** Fenster zeigt die Eigenschaften der einzelnen oder mehrere ausgewählte Elemente: [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md) Optionsseiten enthalten Gruppen von Optionen, die eine bestimmte Komponente, z. B. einer Programmiersprache oder ein VSPackage betreffen: [Optionen und Optionsseiten](../../extensibility/internals/options-and-options-pages.md). Einstellungen sind im allgemeinen UI-bezogene Features, die nicht importiert und exportiert werden können: [Unterstützung für Benutzereinstellungen](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Visual Studio-Diensten  
 Ein Dienst stellt einen bestimmten Satz von Schnittstellen für die Komponenten nutzen. Visual Studio bietet eine Reihe von Diensten, die von der alle Komponenten, einschließlich der Erweiterungen verwendet werden kann. Visual Studio-Diensten ermöglichen z. B. Toolfenster angezeigt oder ausgeblendet dynamisch Aktivieren des Zugriffs auf Hilfe, Statusleiste oder UI-Ereignisse. Visual Studio-Editor bietet auch Dienste, die durch Erweiterungen des Editors importiert werden können. Weitere Informationen finden Sie unter [verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Debugger  
 Der Debugger ist die Benutzeroberfläche an den sprachspezifischen Komponenten. Wenn Sie einen neuer Sprachdienst erstellt haben, müssen Sie zum Erstellen einer bestimmten Debug-Engine an den Debugger zu verknüpfen. Weitere Informationen finden Sie unter [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Quellcodeverwaltung  
 Informationen zum Implementieren einer Datenquellen-Steuerelement-Plug-in oder das VSPackage, finden Sie unter [Quellcodeverwaltung](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Assistenten  
 Sie können einen Assistenten in Verbindung mit der ein neuer Projekttyp erstellen, damit der Assistent hilft Ihnen stellen Ihre Benutzer die richtigen Entscheidungen zu, wenn sie ein neues Projekt des Typs erstellen. Weitere Informationen finden Sie unter [Assistenten](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Benutzerdefinierte Tools  
 Benutzerdefinierte Tools können Sie ein Tool mit einem Element in einem Projekt verknüpfen, und das Tool ausführen, wenn die Datei gespeichert wird. Weitere Informationen finden Sie unter [benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>VSSDK-Hilfsprogramme  
 Das VS SDK umfasst eine Reihe von Dienstprogrammen, die Sie für die Arbeit mit verschiedenen Aspekten von VSPackages müssen. Weitere Informationen finden Sie unter [VSSDK-Hilfsprogramme](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>Mithilfe von Windows Installer  
 In einigen Fällen müssen Sie möglicherweise das VSIX-Installationsprogramm, anstelle der Windows Installer verwenden: Sie möchten z. B. in der Registrierung zu schreiben. Weitere Informationen zur Verwendung von Windows Installer mit Ihren Erweiterungen finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Help Viewer  
 Sie können Ihre eigenen Hilfe und die F1-Seiten in Help Viewer integrieren. Weitere Informationen finden Sie unter [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
