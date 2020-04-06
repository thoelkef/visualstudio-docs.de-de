---
title: Innerhalb des Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707573"
---
# <a name="inside-the-visual-studio-sdk"></a>Im Visual Studio SDK

Dieser Abschnitt enthält ausführliche Informationen zu Visual Studio-Erweiterungen, einschließlich Visual Studio-Architektur, Komponenten, Diensten, Schemas, Dienstprogrammen und dergleichen.

## <a name="extensibility-architecture"></a>Erweiterbarkeitsarchitektur
 Die folgende Abbildung zeigt die Visual Studio-Erweiterbarkeitsarchitektur. VSPackages stellen Anwendungsfunktionen bereit, die in der IDE als Dienste gemeinsam genutzt werden. Die Standard-IDE bietet auch eine breite <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>Palette von Diensten, z. B. , die Zugriff auf die IDE-Fensterfunktionalität bieten.

 ![Grafik "Umweltarchitektur"](../../extensibility/internals/media/environment.gif "Environment") Allgemeine Ansicht der Visual Studio-Architektur

## <a name="vspackages"></a>VSPackages
 VSPackages sind Softwaremodule, die Visual Studio um Benutzeroberflächenelemente, Dienste, Projekte, Editoren und Designer erweitern. VSPackages sind die zentrale Architektureinheit von Visual Studio. Weitere Informationen finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Die Visual Studio-Shell bietet grundlegende Funktionen und unterstützt die Querkommunikation zwischen den Komponenten VSPackages und MEF-Erweiterungen. Weitere Informationen finden Sie unter [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Richtlinien zur Benutzerfreundlichkeit
 Wenn Sie neue Features für Visual Studio entwerfen möchten, sollten Sie sich die folgenden Richtlinien für Entwurfs- und Benutzerfreundlichkeitstipps ansehen: [Visual Studio-Benutzererfahrungsrichtlinien](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Befehle
 Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können.

 Wenn Sie Visual Studio erweitern, können Sie Befehle erstellen und sie bei der Visual Studio-Shell registrieren. Sie können angeben, wie diese Befehle in der IDE angezeigt werden, z. B. in einem Menü oder einer Symbolleiste. In der Regel wird ein benutzerdefinierter Befehl im Menü **Extras** angezeigt, und ein Befehl zum Anzeigen eines Toolfensters wird im Untermenü **Andere Windows** im Menü **Ansicht** angezeigt.

 Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler dafür erstellen. Der Ereignishandler bestimmt, wann der Befehl sichtbar oder aktiviert ist, ermöglicht es Ihnen, seinen Text zu ändern, und garantiert, dass der Befehl entsprechend reagiert, wenn er aktiviert wird. In den meisten Fällen verarbeitet die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> IDE Befehle mithilfe der Schnittstelle. Befehle in Visual Studio werden behandelt, beginnend mit dem innersten Befehlskontext, basierend auf der lokalen Auswahl, und dem äußersten Kontext, basierend auf der globalen Auswahl. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar.

 Weitere Informationen finden Sie unter [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menüs und Symbolleisten
 Menüs und Symbolleisten bieten Benutzern die Möglichkeit, Befehle aufzurufen. Menüs sind Zeilen oder Spalten von Befehlen, die in der Regel als einzelne Textelemente oben in einem Werkzeugfenster angezeigt werden. Untermenüs sind sekundäre Menüs, die angezeigt werden, wenn ein Benutzer auf Befehle klickt, die einen kleinen Pfeil enthalten. Kontextmenüs werden angezeigt, wenn ein Benutzer mit der rechten Maustaste auf bestimmte UI-Elemente klickt. Einige häufige Menünamen sind **Datei**, **Bearbeiten**, **Ansicht**und **Fenster**. Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Symbolleisten sind Zeilen oder Spalten von Schaltflächen und anderen Steuerelementen, z. B. Kombinationsfelder, Listenfelder und Textfelder. Symbolleistenschaltflächen verfügen in der Regel über Symbolbilder, z. B. ein Ordnersymbol für einen Befehl **"Datei öffnen"** oder einen Drucker für einen **Druckbefehl.** Alle Symbolleistenelemente sind Befehlen zugeordnet. Wenn Sie auf eine Symbolleistenschaltfläche klicken, wird der zugehörige Befehl ausgeführt. Bei einem Dropdown-Steuerelement ist jedes Element in der Dropdownliste einem anderen Befehl zugeordnet. Einige Symbolleistensteuerelemente, z. B. ein Splittersteuerelement, sind Hybriden. Eine Seite des Steuerelements ist eine Symbolleistenschaltfläche und die andere Seite ist ein Pfeil nach unten, der mehrere Befehle anzeigt, wenn darauf geklickt wird.

## <a name="tool-windows"></a>Toolfenster
 Toolfenster werden in der IDE verwendet, um Informationen anzuzeigen. **Toolbox**, **Projektmappen-Explorer**, **Eigenschaftenfenster** und **Webbrowser** sind Beispiele für Toolfenster.

 Toolfenster bieten in der Regel verschiedene Steuerelemente, mit denen der Benutzer interagieren kann. Im Fenster **Eigenschaften** kann der Benutzer z. B. Eigenschaften von Objekten festlegen, die einem bestimmten Zweck dienen. Das **Eigenschaftenfenster** ist in diesem Sinne spezialisiert, aber auch allgemein, da es in vielen verschiedenen Situationen verwendet werden kann. Ebenso ist das **Ausgabefenster** spezialisiert, da es textbasierte Ausgabe bereitstellt, aber allgemein, da viele Subsysteme in Visual Studio es verwenden können, um dem Visual Studio-Benutzer ausgabegemäß zu sein.

 Betrachten Sie das folgende Bild von Visual Studio, das mehrere Toolfenster enthält:

 ![Screenshot](../../extensibility/internals/media/t1gui.png "T1gui")

 Einige der Toolfenster sind an einem einzelnen Fenster angedockt, in dem das Werkzeugfenster des Projektmappen-Explorers angezeigt wird und die anderen Toolfenster ausgeblendet werden, sie jedoch durch Klicken auf Registerkarten verfügbar machen. Das Bild zeigt zwei weitere Toolfenster, das **Fenster Fehlerliste** und **Ausgabe,** das an einem einzigen Fenster angedockt ist.

 Ebenfalls gezeigt wird der Hauptdokumentbereich, in dem mehrere Editorfenster angezeigt werden. Obwohl Toolfenster in der Regel nur über eine Instanz verfügen (z. B. können Sie nur einen **Projektmappen-Explorer**öffnen), können Editorfenster mehrere Instanzen haben, von denen jede zum Bearbeiten eines separaten Dokuments verwendet wird, aber alle im selben Bereich angedockt sind. Das Bild zeigt einen Dokumentbereich mit zwei Editorfenstern, einem Formular-Designerfenster. Alle Fenster im Dokumentbereich sind durch Klicken auf Registerkarten verfügbar, aber das Editorfenster, das EditorPane.cs Datei enthält, ist sichtbar und aktiv.

 Wenn Sie Visual Studio erweitern, können Sie Toolfenster erstellen, mit denen Visual Studio-Benutzer mit Ihrer Erweiterung interagieren können. Sie können auch eigene Editoren erstellen, mit denen Visual Studio-Benutzer Dokumente bearbeiten können. Da Ihre Toolfenster und -editoren in Visual Studio integriert werden, müssen Sie sie nicht zum Andocken oder Korrekterscheinen auf einer Registerkarte programmieren. Wenn sie ordnungsgemäß in Visual Studio registriert sind, verfügen sie automatisch über die typischen Features von Toolfenstern und Dokumentfenstern in Visual Studio. Weitere Informationen finden Sie unter [Erweitern und Anpassen von Tool Windows](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Dokumentfenster
 Ein Dokumentfenster ist ein gerahmtes untergeordnetes Fenster eines MDI-Fensters (Multiple Document Interface). Dokumentfenster werden in der Regel zum Hosten von Texteditoren, Formulareditoren (auch als Designer bezeichnet) oder zum Bearbeiten von Steuerelementen verwendet, sie können jedoch auch andere Funktionstypen hosten. Das Dialogfeld **Neue Datei** enthält Beispiele für Dokumentfenster, die Visual Studio bereitstellt.

 Die meisten Editoren sind spezifisch für eine Programmiersprache oder einen Dateityp, z. B. HTML-Seiten, Framesets, C++-Dateien oder Headerdateien. Durch Auswählen einer Vorlage im Dialogfeld **Neue Datei** erstellt ein Benutzer dynamisch ein Dokumentfenster für den Editor für den Dateityp, der der Vorlage zugeordnet ist. Ein Dokumentfenster wird auch erstellt, wenn ein Benutzer eine vorhandene Datei öffnet.

 Dokumentfenster sind auf den MDI-Clientbereich beschränkt. Jedes Dokumentfenster verfügt über eine Registerkarte oben, und die Registerkartenreihenfolge ist mit anderen Fenstern verknüpft, die möglicherweise im MDI-Bereich geöffnet sind. Wenn Sie mit der rechten Maustaste auf die Registerkarte eines Dokumentfensters klicken, wird ein Kontextmenü angezeigt, das Optionen zum Aufteilen des MDI-Bereichs in mehrere horizontale oder vertikale Registerkartengruppen enthält. Durch das Aufteilen des MDI-Bereichs können mehrere Dateien gleichzeitig angezeigt werden. Weitere Informationen finden Sie unter [Dokument Windows](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editoren
 Mit dem Visual Studio-Editor können Sie ihn anpassen und mithilfe des Managed Extensibility Framework (MEF) für Ihren eigenen Inhaltstyp verwenden. In vielen Fällen müssen Sie kein VSPackage erstellen, um den Editor zu erweitern, obwohl Sie eine MEF-Erweiterung mit einem VSPackage kombinieren können, wenn Sie Features aus der Shell einschließen möchten (z. B. einen Menübefehl oder eine Tastenkombination).

 Sie können auch einen benutzerdefinierten Editor erstellen, z. B. wenn Sie in einer Datenbank lesen und schreiben möchten oder wenn Sie einen Designer verwenden möchten. Sie können auch einen externen Editor wie Notepad oder Microsoft WordPad verwenden. Weitere Informationen finden Sie unter [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Sprachdienste
 Wenn der Visual Studio-Editor neue Programmierschlüsselwörter oder sogar eine neue Programmiersprache unterstützen soll, erstellen Sie einen Sprachdienst. Jeder Sprachdienst kann bestimmte Editorfunktionen vollständig, teilweise oder gar nicht implementieren. Je nachdem, wie er konfiguriert ist, kann der Sprachdienst Syntaxhervorhebung, Klammerabgleich, IntelliSense-Unterstützung und andere Funktionen im Editor bereitstellen.

 Im Mittelpunkt eines Sprachdienstes stehen ein Parser und ein Scanner. Ein Scanner (oder Lexer) unterteilt eine Quelldatei in Elemente, die als Token bezeichnet werden, und ein Parser stellt die Beziehungen zwischen diesen Token her. Wenn Sie einen Sprachdienst erstellen, müssen Sie den Parser und den Scanner implementieren, damit Visual Studio die Token und Grammatik der Sprache verstehen kann. Sie können verwaltete oder nicht verwaltete Sprachdienste erstellen. Weitere Informationen finden Sie unter [Legacy Language Service Extensibility](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projekte

In Visual Studio sind Projekte die Container, die Entwickler zum Organisieren und Erstellen des Quellcodes und anderer Ressourcen verwenden. Mit Projekten können Sie Quellcode, Verweise auf Webdienste und Datenbanken und andere Ressourcen organisieren, erstellen, debuggen und bereitstellen. VSPackages kann das Visual Studio-Projektsystem erweitern, indem Projekttypen, Projektuntertypen und benutzerdefinierte Tools bereitstellen werden.

Projekte können auch in einer *Projektmappe*zusammengefasst werden, bei der es sich um eine Gruppierung eines oder mehrerer Projekte handelt, die zusammenarbeiten, um eine Anwendung zu erstellen. Projekt- und Statusinformationen, die sich auf die Projektmappe beziehen, werden in zwei Lösungsdateien gespeichert, der textbasierten [Lösungsdatei (.sln)](solution-dot-sln-file.md) und der Benutzeroption für binäre [Lösungen (.suo).](solution-user-options-dot-suo-file.md) Diese Dateien ähneln den Gruppendateien (.vbg), die in früheren Versionen von Visual Basic verwendet wurden, sowie den Arbeitsbereichsdateien (.dsw) und Benutzeroptionen (.opt), die in früheren Versionen von C++ verwendet wurden.

Weitere Informationen finden Sie unter [Projekte](../../extensibility/internals/projects.md) und [Lösungen](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Projekt- und Elementvorlagen
 Visual Studio enthält vordefinierte Projektvorlagen und Projektelementvorlagen. Sie können auch eigene Vorlagen erstellen oder Vorlagen aus der Community erwerben und diese dann in Visual Studio integrieren. Die [MSDN-Codegalerie](https://code.msdn.microsoft.com/site/search?query=visual%20studio) ist der Ort, an dem Sie Vorlagen und Erweiterungen verwenden können.

 Vorlagen enthalten die Projektstruktur und grundlegende Dateien, die zum Erstellen einer bestimmten Art von Anwendung, Steuerelement, Bibliothek oder Klasse erforderlich sind. Wenn Sie Software entwickeln möchten, die einer der Vorlagen ähnelt, erstellen Sie ein Projekt, das auf der Vorlage basiert, und ändern Sie dann die Dateien in diesem Projekt.

> [!NOTE]
> Diese Vorlagenarchitektur wird [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] für Projekte nicht unterstützt.

 Weitere Informationen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Eigenschaften und Optionen
 Das **Fenster Eigenschaften** zeigt die Eigenschaften einzelner oder mehrerer ausgewählter Elemente an: Seiten für [Eigenschaftenoptionen](../../extensibility/internals/extending-properties.md) zum Erweitern von Eigenschaften enthalten Gruppen von Optionen, die sich auf eine bestimmte Komponente beziehen, z. B. eine Programmiersprache oder ein VSPackage: Optionen und [Optionsseiten](../../extensibility/internals/options-and-options-pages.md). Einstellungen sind im Allgemeinen UI-bezogene Features, die importiert und exportiert werden können: [Unterstützung für Benutzereinstellungen](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Visual Studio-Dienste
 Ein Dienst stellt einen bestimmten Satz von Schnittstellen bereit, die Komponenten verbrauchen können. Visual Studio stellt eine Reihe von Diensten bereit, die von allen Komponenten, einschließlich Erweiterungen, verwendet werden können. Visual Studio-Dienste ermöglichen beispielsweise das dynamische Anzeigen oder Aussehen von Toolfenstern, das Aktivieren des Zugriffs auf Hilfe-, Statusleisten- oder UI-Ereignisse. Der Visual Studio-Editor stellt auch Dienste bereit, die von Editorerweiterungen importiert werden können. Weitere Informationen finden Sie unter [Verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Debugger
 Der Debugger ist die Benutzeroberfläche für die sprachspezifischen Debugkomponenten. Wenn Sie einen neuen Sprachdienst erstellt haben, müssen Sie ein bestimmtes Debugmodul erstellen, das sich an den Debugger anhängt. Weitere Informationen finden Sie unter [Visual Studio Debugger Extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Quellcodeverwaltung
 Informationen zum Implementieren eines Quellcodeverwaltungs-Plug-Ins oder VSPackage finden Sie unter [Quellcodeverwaltung](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Assistenten
 Sie können einen Assistenten in Verbindung mit einem neuen Projekttyp erstellen, damit der Assistent den Benutzern helfen kann, die richtigen Entscheidungen zu treffen, wenn sie ein neues Projekt dieses Typs erstellen. Weitere Informationen finden Sie unter [Assistenten](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Benutzerdefinierte Tools
 Mit benutzerdefinierten Tools können Sie ein Werkzeug einem Element in einem Projekt zuordnen und dieses Tool ausführen, wenn die Datei gespeichert wird. Weitere Informationen finden Sie unter [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>VSSDK-Hilfsprogramme
 Das VSSDK enthält eine Reihe von Dienstprogrammen, die Sie möglicherweise benötigen, um mit verschiedenen Aspekten von VSPackages zu arbeiten. Weitere Informationen finden Sie unter [VSSDK Utilities](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Verwenden von Windows Installer
 In einigen Fällen müssen Sie möglicherweise den Windows Installer anstelle des VSIX-Installationsprogramms verwenden: Sie müssen z. B. in die Registrierung schreiben. Informationen zur Verwendung von Windows Installer mit Ihren Erweiterungen finden Sie unter [Installieren von VSPackages With Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Help Viewer
 Sie können Ihre eigene Hilfe und F1-Seiten in den Help Viewer integrieren. Weitere Informationen finden Sie unter [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
