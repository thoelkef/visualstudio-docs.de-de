---
title: Anwendungsmuster für Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55044df3898b452e87ec877f9ae10dd12a2b1110
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301590"
---
# <a name="application-patterns-for-visual-studio"></a>Anwendungsmuster für Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Fensterinteraktionen

### <a name="overview"></a>Übersicht
Die beiden Hauptfenstertypen, die in Visual Studio verwendet werden, sind Dokumenteditoren und Toolfenster. Selten, aber möglich, sind große moduslose Dialoge. Obwohl diese alle in der Schale moduslos sind, unterscheiden sich ihre Muster grundlegend. In diesem Abschnitt wird der Unterschied zwischen Dokumentfenstern, Toolfenstern und moduslosen Dialogfeldern behandelt. Modale Dialogmuster werden in [Dialogfeldern](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)behandelt.

### <a name="comparing-window-usage-patterns"></a>Vergleichen von Fensternutzungsmustern
**Dokumentfenster** werden fast immer gut im Dokument angezeigt. Dies gibt dem Dokumenteditor eine "zentrale Bühne", um zusätzliche Werkzeugfenster zu arrangieren.

Ein **Werkzeugfenster** wird am häufigsten als separates, kleineres Fenster angezeigt, das an der Kante der IDE reduziert wird. Dies kann sichtbar, ausgeblendet oder automatisch ausgeblendet sein. Manchmal werden jedoch Toolfenster innerhalb des Dokuments gut angezeigt, indem die **Window/Docking-Eigenschaft** im Fenster deaktivieren wird. Dies führt zu mehr Immobilien, aber auch zu einer gemeinsamen Entwurfsentscheidung: Wenn Sie versuchen, sich in Visual Studio zu integrieren, müssen Sie entscheiden, ob Ihr Feature ein Toolfenster oder ein Dokumentfenster anzeigen soll.

In Visual Studio wird von **moduslosen Dialogfeldern** abgeraten. Die meisten moduslosen Dialoge sind definitionsgemäß unverankerte Toolfenster und sollten auf diese Weise implementiert werden. Moduslose Dialoge sind in Fällen zulässig, in denen die Größe eines normalen Werkzeugfensters, das an die Seite der Shell angedockt ist, zu begrenzt wäre. Sie sind auch in Fällen zulässig, in denen der Benutzer das Dialogfeld wahrscheinlich auf einen sekundären Monitor verschiebt.

Überlegen Sie sich genau, welchen Containertyp Sie benötigen. Allgemeine Überlegungen zum Verwendungsmuster für den UI-Entwurf finden Sie in der folgenden Tabelle.

||Dokumentfenster|Werkzeugfenster|Modusloser Dialog|
|-|---------------------|-----------------|---------------------|
| **Position** | Immer gut innerhalb des Dokuments positioniert und dockt nicht an den Rändern der IDE an. Es kann "abgezogen" werden, so dass es getrennt von der Hauptschale schwebt. | Im Allgemeinen an den Rändern der IDE angedockt, kann jedoch so angepasst werden, dass sie unverankert, automatisch ausgeblendet (nicht fixiert) oder im Dokument gut angedockt werden.|Großes schwebendes Fenster getrennt von der IDE. |
| **Commit-Modell** | *Verzögerter Commit*<br /><br /> Um die Daten in einem Dokument zu speichern, muss der Benutzer den Befehl **Datei &gt; speichern**, **Speichern unter**oder Alle **speichern ausgeben.** In einem Dokumentfenster wird das Konzept der darin enthaltenen Daten "verdreckt" und dann an einen der Speicherbefehle gebunden. Beim Schließen eines Dokumentfensters werden alle Inhalte entweder auf dem Datenträger gespeichert oder verloren. | *SofortigeVerpflichtung*<br /><br /> Es gibt kein Speichermodell. Für Inspektor-Toolfenster, die beim Bearbeiten einer Datei helfen, muss die Datei im aktiven Editor oder Designer geöffnet sein, und der Editor oder Designer besitzt das Speichern. | *Verzögerter oder sofortiger Commit*<br /><br /> In den meisten Fall erfordert ein großes modusloses Dialogfeld eine Aktion zum Commit von Änderungen und ermöglicht einen "Abbrechen"-Vorgang, bei dem alle innerhalb der Dialogsitzung vorgenommenen Änderungen rückgängig gemacht werden.  Dadurch unterscheidet sich ein modusloses Dialogfeld von einem Toolfenster in diesem Toolfenster, das immer über ein sofortiges Commitmodell verfügt. |
| **Sichtbarkeit** | *Öffnen/Erstellen (Datei) und Schließen*<br /><br /> Das Öffnen eines Dokumentfensters erfolgt entweder durch Öffnen eines vorhandenen Dokuments oder durch Verwenden einer Vorlage zum Erstellen eines neuen Dokuments. Es gibt keinen \<Befehl "Öffnen sie einen bestimmten Editor>". | *Ausblenden und Zeigen*<br /><br /> Einzelinstanz-Toolfenster können ausgeblendet oder angezeigt werden. Inhalte und Zustände im Werkzeugfenster bleiben erhalten, unabhängig davon, ob sie angezeigt oder ausgeblendet sind. Toolfenster mit mehreren Instanzen können geschlossen und ausgeblendet werden. Wenn ein Toolfenster mit mehreren Instanzen geschlossen wird, werden Inhalt und Status im Toolfenster verworfen. | *Gestartet von einem Befehl*<br /><br /> Dialoge werden über einen aufgabenbasierten Befehl gestartet. |
| **Instanzen** | *Multi-Instanz*<br /><br /> Mehrere Editoren können gleichzeitig geöffnet sein und verschiedene Dateien bearbeiten, während einige Editoren auch zulassen, dass dieselbe Datei in mehr als einem Editor geöffnet wird (mit dem Befehl **Fenster &gt; neues Fenster).**<br /><br /> Ein einzelner Editor kann eine oder mehrere Dateien gleichzeitig bearbeiten (Projekt-Designer). | *Ein- oder mehrinstanzen*<br /><br /> Inhalte ändern sich, um kontextabhängig zu sein (wie im Eigenschaftenbrowser) oder den Fokus/Kontext in andere Fenster zu verschieben (Aufgabenliste, Projektmappen-Explorer).<br /><br /> Sowohl Einzelinstanz- als auch Multiinstanz-Toolfenster sollten dem aktiven Dokumentfenster zugeordnet werden, es sei denn, es gibt einen zwingenden Grund, dies nicht zu tun. | *Single-Instanz* |
| **Beispiele** | **Texteditoren**, wie der Code-Editor<br /><br /> **Entwerfen von Flächen,** z. B. eines Formulardesigners oder einer Modellierungsfläche<br /><br /> **Steuern von Layouts, die Dialogfeldern ähneln, wie z. B.** dem Manifest-Designer | Der **Projektmappen-Explorer** bietet eine Projektmappe und Projekte, die in der Projektmappe enthalten sind.<br /><br /> Der **Server-Explorer** bietet eine hierarchische Ansicht von Servern und Datenverbindungen, die der Benutzer im Fenster öffnen möchte. Durch Öffnen eines Objekts aus der Datenbankhierarchie, z. B. einer Abfrage, wird ein Dokumentfenster geöffnet und der Benutzer kann die Abfrage bearbeiten.<br /><br /> Der **Eigenschaftenbrowser** zeigt Eigenschaften für das Objekt an, das entweder in einem Dokumentfenster oder in einem anderen Werkzeugfenster ausgewählt wurde. Die Eigenschaften werden entweder in einer hierarchischen Rasteransicht oder in komplexen dialogähnlichen Steuerelementen dargestellt und ermöglichen es dem Benutzer, die Werte für diese Eigenschaften festzulegen. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Werkzeugfenster

### <a name="overview"></a>Übersicht
Toolfenster unterstützen die Arbeit des Benutzers, die in Dokumentfenstern stattfindet. Sie können verwendet werden, um eine Hierarchie anzuzeigen, die ein grundlegendes Stammobjekt darstellt, das Visual Studio bereitstellt und bearbeiten kann.

Wenn Sie ein neues Toolfenster in der IDE in Betracht ziehen, sollten Autoren:

- Verwenden Sie aufgabengerechte vorhandene Toolfenster, und erstellen Sie keine neuen Mitbenutzer mit ähnlicher Funktionalität. Neue Toolfenster sollten nur erstellt werden, wenn sie ein deutlich anderes "Werkzeug" oder eine deutlich andere Funktionalität bieten, die nicht in ein ähnliches Fenster integriert werden kann, oder indem ein vorhandenes Fenster in einen Schwenkhub verwandelt wird.

- Verwenden Sie bei Bedarf eine Standardbefehlsleiste oben im Werkzeugfenster.

- Konsistent mit Mustern, die bereits in anderen Toolfenstern zur Steuerungspräsentation und Tastaturnavigation vorhanden sind.

- Konsistent mit der Steuerelementdarstellung in anderen Werkzeugfenstern.

- Machen Sie dokumentspezifische Toolfenster nach Möglichkeit automatisch sichtbar, sodass sie nur angezeigt werden, wenn das übergeordnete Dokument aktiviert ist.

- Stellen Sie sicher, dass der Inhalt des Fensters über die Tastatur navigierbar ist (Pfeiltasten unterstützen).

#### <a name="tool-window-states"></a>Werkzeugfensterzustände
Visual Studio-Toolfenster weisen unterschiedliche Zustände auf, von denen einige vom Benutzer aktiviert sind (z. B. die Funktion zum automatischen Ausblenden). Andere Zustände, z. B. automatisch sichtbar, ermöglichen es, dass Toolfenster im richtigen Kontext angezeigt und ausgeblendet werden, wenn dies nicht erforderlich ist. Es gibt insgesamt fünf Werkzeugfensterzustände.

- **Angedockte/angeheftete** Werkzeugfenster können an eine der vier Seiten des Dokumentbereichs angehängt werden. Das Pin-Symbol wird in der Titelleiste des Werkzeugfensters angezeigt. Das Werkzeugfenster kann horizontal oder vertikal am Rand der Schale und anderen Werkzeugfenstern angedockt und auch mit Registerkarten verknüpft werden.

- **Automatisch ausgeblendete** Werkzeugfenster werden nicht fixiert. Das Fenster kann aus dem Blickfeld gleiten und eine Registerkarte (mit dem Namen des Werkzeugfensters und seinem Symbol) am Rand des Dokumentbereichs zurücklassen. Das Toolfenster wird herausgeklappt, wenn ein Benutzer mit der Maus über die Registerkarte zeigt.

- **Automatisch sichtbare** Toolfenster werden automatisch angezeigt, wenn ein anderes Element der Benutzeroberfläche, z. B. ein Editor, gestartet wird oder den Fokus erhält.

- **Schwebende** Werkzeugfenster bewegen sich außerhalb der IDE. Dies ist nützlich für Konfigurationen mit mehreren Monitoren.

- **Registerkarten-Dokumentwerkzeugfenster** können im Dokument gut angedockt werden. Dies ist nützlich für große Toolfenster, wie der Objektbrowser, die mehr Immobilien benötigen, als das Andocken an den Rändern des Rahmens zulässt.

![Status für Toolfenster in Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Status für Toolfenster in Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Single-Instanz und Multi-Instanz
Toolfenster sind entweder Einzelinstanzen oder Mehrere Instanzen. Einige Toolfenster mit einer Instanz sind möglicherweise dem aktiven Dokumentfenster zugeordnet, während Toolfenster mit mehreren Instanzen dies möglicherweise nicht der Fall ist. Toolfenster mit mehreren Instanzen reagieren auf den Befehl **Fenster &gt; neues Fenster,** indem sie eine neue Instanz des Fensters erstellen. Die folgende Abbildung zeigt ein Toolfenster, das den Befehl Neues Fenster aktiviert, wenn eine Instanz des Fensters aktiv ist:

![Toolfenster, das den Befehl "Neues Fenster" aktiviert, wenn eine Instanz des Fensters aktiv ist](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Toolfenster, das den Befehl "Neues Fenster" aktiviert, wenn eine Instanz des Fensters aktiv ist

Einzelinstanz-Toolfenster können ausgeblendet oder angezeigt werden, während Toolfenster mit mehreren Instanzen geschlossen und ausgeblendet werden können. Alle Toolfenster können angedockt, mit Registerkarten verknüpft, unverankert oder als untergeordnetes Fenster für die Multidocument Interface (MDI) festgelegt werden (ähnlich einem Dokumentfenster). Alle Toolfenster sollten auf die entsprechenden Fensterverwaltungsbefehle im Menü Fenster reagieren:

![Fensterverwaltungsbefehle im Menü "Visual Studio Window"](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Fensterverwaltungsbefehle im Menü "Visual Studio Window"

#### <a name="document-specific-tool-windows"></a>Dokumentspezifische Toolfenster
Einige Toolfenster sind so konzipiert, dass sie basierend auf einem bestimmten Dokumenttyp geändert werden. Diese Fenster werden ständig aktualisiert, um die Funktionalität des aktiven Dokumentfensters in der IDE widerzuspiegeln.

Beispiele für Toolfenster, deren Inhalt sich ändert, um den ausgewählten Editor widerzuspiegeln, sind die Toolbox und die Dokumentumrisslinie. Diese Fenster zeigen ein Wasserzeichen an, wenn ein Editor einen Fokus hat, der dem Fenster keinen Kontext bietet.

#### <a name="navigable-list-tool-windows"></a>Navigierbare Listentoolfenster
In einigen Toolfenstern wird eine Liste der schiffbaren Elemente angezeigt, mit denen der Benutzer interagieren kann. In diesem Fenstertyp sollte es immer Feedback für das aktuelle Element in der Liste geben, auch wenn das Fenster inaktiv ist. Die Liste sollte auf die Befehle **GoToNextLocation** und **GoToPrevLocation** reagieren, indem auch das aktuell ausgewählte Element im Fenster geändert wird.

Beispiele für navigierbare Listentoolfenster sind der Projektmappen-Explorer und das Fenster Ergebnisse suchen.

### <a name="tool-window-types"></a>Werkzeugfenstertypen

#### <a name="common-tool-windows-and-their-functions"></a>Gemeinsame Werkzeugfenster und deren Funktionen

**Hierarchische Werkzeugfenster**

| Werkzeugfenster | Funktion |
| --- | --- |
| Projektmappen-Explorer | Eine hierarchische Struktur, in der eine Liste der Dokumente angezeigt wird, die in Projekten, verschiedenen Dateien und Projektmappenelementen enthalten sind. Die Anzeige der Elemente in Projekten wird durch das Paket definiert, das den Projekttyp besitzt (z. B. referenzbasierte, verzeichnisbasierte oder gemischte Typen). |
| Klassenansicht | Ein hierarchischer Baum der Klassen und verschiedene Elemente im Arbeitssatz von Dokumenten, unabhängig von den Dateien selbst. |
| Server-Explorer | Eine hierarchische Struktur, die alle Server und Datenverbindungen in der Lösung anzeigt. |
| Dokumentgliederung | Die hierarchische Struktur des aktiven Dokuments. |

**Rasterwerkzeugfenster**

| Werkzeugfenster | Funktion |
| --- | --- |
| Eigenschaften | Ein Raster, das eine Liste von Eigenschaften für das ausgewählte Objekt sowie Wertauswahlen zum Bearbeiten dieser Eigenschaften anzeigt. |
| Aufgabenliste | Ein Raster, mit dem der Benutzer Aufgaben und Kommentare erstellen/bearbeiten/löschen kann. |

**Inhaltswerkzeugfenster**

| Werkzeugfenster | Funktion |
| --- | --- |
| Hilfe | Ein Fenster, das Benutzern den Zugriff auf verschiedene Methoden zum Abrufen von Hilfe ermöglicht, von "Wie kann ich?" Videos in MSDN-Foren. |
| Dynamische Hilfe | Ein Toolfenster, in dem Links angezeigt werden, um Hilfethemen anzuzeigen, die für die aktuelle Auswahl gelten. |
| Objektkatalog | Ein zweispaltiges Frameset mit einer Liste hierarchischer Objektkomponenten im linken Bereich und den Eigenschaften und Methoden des Objekts in der rechten Spalte. |

**Dialog-Toolfenster**

| Werkzeugfenster | Funktion |
| --- | --- |
| Suchen | Ein Dialogfeld, in dem der Benutzer verschiedene Dateien innerhalb der Lösung suchen oder suchen und ersetzen kann. |
| Erweiterte Suche | Ein Dialogfeld, in dem der Benutzer verschiedene Dateien innerhalb der Lösung suchen oder suchen und ersetzen kann. |

**Andere Werkzeugfenster**

::: moniker range="vs-2017"

| Werkzeugfenster | Funktion |
| --- | --- |
| Toolbox | Das Werkzeugfenster zum Speichern von Elementen, die auf Entwurfsflächen abgelegt werden, bietet eine konsistente Ziehquelle für alle Designer. |
| Startseite | Das Benutzerportal zu Visual Studio mit Zugriff auf Feeds von Entwicklernews, Visual Studio-Hilfe und aktuelle Projekte. Benutzer können auch benutzerdefinierte Startseiten erstellen, indem sie die Datei StartPage.xaml aus dem Programmdateiverzeichnis "Common7-IDE-StartPages\" Visual Studio" in den Ordner StartPages im Visual Studio-Dokumentverzeichnis kopieren und dann das XAML entweder von Hand bearbeiten oder in Visual Studio oder einem anderen Codeeditor öffnen. |

::: moniker-end

::: moniker range=">=vs-2019"

| Werkzeugfenster | Funktion |
| --- | --- |
| Toolbox | Das Werkzeugfenster zum Speichern von Elementen, die auf Entwurfsflächen abgelegt werden, bietet eine konsistente Ziehquelle für alle Designer. |

::: moniker-end

**Debugger-Toolfenster**

| Werkzeugfenster | Funktion |
| --- | --- |
| Autos ||
| Unmittelbar ||
| Output | Das Ausgabefenster kann immer dann verwendet werden, wenn Sie Textereignisse oder Status deklarieren möchten. |
| Arbeitsspeicher ||
| Breakpoints ||
| Wird ausgeführt ||
| Dokumente ||
| Aufrufliste ||
| Locals ||
| Uhren ||
| Disassemblierung ||
| Register ||
| Threads ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Dokumenteditor-Konventionen

### <a name="document-interactions"></a>Dokumentinteraktionen
Der "Dokument brunnen" ist der größte Raum innerhalb der IDE und ist, wo der Benutzer in der Regel seine Aufmerksamkeit konzentriert hat, um ihre Aufgaben zu erfüllen, unterstützt durch zusätzliche Werkzeugfenster. Dokumenteditoren stellen die grundlegenden Arbeitseinheiten dar, die der Benutzer in Visual Studio öffnet und speichert. Sie behalten ein starkes Gefühl der Auswahl, das an den Projektmappen-Explorer oder andere aktive Hierarchiefenster gebunden ist. Der Benutzer sollte in der Lage sein, auf eines dieser Hierarchiefenster zu verweisen und zu wissen, wo das Dokument enthalten ist und ob es mit der Projektmappe, dem Projekt oder einem anderen Stammobjekt, das von einem Visual Studio-Paket bereitgestellt wird, in Beziehung steht.

Die Bearbeitung von Dokumenten erfordert eine konsistente Benutzererfahrung. Damit sich der Benutzer auf die anstehende Aufgabe konzentrieren kann, anstatt auf die Fensterverwaltung und die Suche nach Befehlen, wählen Sie eine Dokumentansichtsstrategie aus, die am besten zu den Benutzeraufgaben für die Bearbeitung dieses Dokumenttyps passt.

#### <a name="common-interactions-for-the-document-well"></a>Häufige Interaktionen für das Dokument gut

- Verwalten Sie ein konsistentes Interaktionsmodell in den allgemeinen Erfahrungen mit **neuen Dateien** und **offenen Dateien.**

- Aktualisieren Sie verwandte Funktionen in verwandten Fenstern und Menüs, wenn das Dokumentfenster geöffnet wird.

- Menübefehle sind in gängige Menüs wie **Bearbeiten,** **Formatieren**und **Anzeigen** menüs entsprechend integriert. Wenn eine beträchtliche Anzahl von spezialisierten Befehlen verfügbar ist, kann ein neues Menü erstellt werden. Dieses neue Menü sollte nur sichtbar sein, wenn das Dokument den Fokus hat.

- Eine eingebettete Symbolleiste kann oben im Editor platziert werden. Dies ist besser als eine separate Symbolleiste, die außerhalb des Editors angezeigt wird.

- Verwalten Sie immer eine Auswahl im Projektmappen-Explorer oder in einem ähnlichen aktiven Hierarchiefenster.

- Wenn Sie im Projektmappen-Explorer auf ein Dokument doppelklicken, sollte dieselbe Aktion wie **Öffnen**ausgeführt werden.

- Wenn mehr als ein Editor für einen Dokumenttyp verwendet werden kann, sollte der Benutzer in der Lage sein, die Standardaktion für einen bestimmten Dokumenttyp über das Dialogfeld **Öffnen** mit zu überschreiben oder zurückzusetzen, indem er mit der rechten Maustaste auf die Datei klickt und im Kontextmenü **"Mit öffnen"** auswählt.

- Erstellen Sie keinen Assistenten in einem Dokument.

### <a name="user-expectations-for-specific-document-types"></a>Benutzererwartungen für bestimmte Dokumenttypen
Es gibt mehrere verschiedene grundlegende Typen von Dokumenteditoren, und jeder verfügt über eine Reihe von Interaktionen, die mit anderen desselben Typs konsistent sind.

- **Textbasierter Editor:** Code-Editor, Protokolldateien

- **Designoberfläche:** WPF Forms Designer, Windows Forms

- **Dialog-Editor:** Manifest-Designer, Projekteigenschaften

- **Modelldesigner:** Workflow-Designer, Codemap, Architekturdiagramm, Progression

Es gibt auch mehrere Nicht-Editor-Typen, die das Dokument gut verwenden. Obwohl sie Dokumente nicht selbst bearbeiten, müssen sie Standardinteraktionen für Dokumentfenster befolgen.

- **Berichte:** IntelliTrace-Bericht, Hyper-V-Bericht, Profilerbericht

- **Dashboard:** Diagnose-Hub

#### <a name="text-based-editors"></a>Textbasierte Editoren

- Das Dokument nimmt am Registerkartenmodell vorschau teil, sodass das Dokument in der Vorschau angezeigt werden kann, ohne es zu öffnen.

- Die Struktur des Dokuments kann in einem Begleitwerkzeugfenster dargestellt werden, z. B. in einer Dokumentumrissleiste.

- IntelliSense (falls zutreffend) verhält sich konsistent mit anderen Code-Editoren.

- Pop-ups oder hilfsfähige Benutzeroberfläche folgen ähnlichen Stilen und Mustern für vorhandene ähnliche Benutzeroberfläche, z. B. CodeLens.

- Meldungen zum Dokumentstatus werden in einem Infoleistensteuerelement oben im Dokument oder in der Statusleiste angezeigt.

- Der Benutzer muss in der Lage sein, die Darstellung von Schriftarten und Farben mithilfe einer Seite **"Tools > Options"** anzupassen, entweder auf der Seite "freigegebene Schriftarten und Farben" oder auf der Seite "Schriftarten und Farben" oder auf der Seite "Schriftarten und Farben" oder auf der Seite für den Editor.

#### <a name="design-surfaces"></a>Design-Oberflächen

- Ein leerer Designer sollte ein Wasserzeichen auf der Oberfläche haben, das anzeigt, wie sie beginnen sollen.

- View-Switching-Mechanismen folgen vorhandenen Mustern, z. B. Doppelklick, um einen Code-Editor zu öffnen, oder Registerkarten im Dokumentfenster, die eine Interaktion mit beiden Bereichen ermöglichen.

- Das Hinzufügen von Elementen zur Entwurfsoberfläche sollte über die Toolbox erfolgen, es sei denn, es ist ein sehr spezifisches Werkzeugfenster erforderlich.

- Elemente auf der Oberfläche folgen einem konsistenten Auswahlmodell.

- Eingebettete Symbolleisten enthalten nur dokumentspezifische Befehle, keine allgemeinen Befehle wie **Speichern**.

#### <a name="dialog-style-editors"></a>Dialog-Editoren

- Das Steuerelementlayout sollte den normalen Dialoglayoutkonventionen folgen.

- Registerkarten im Editor sollten nicht mit der Darstellung der Dokumentregisterkarten übereinstimmen, sondern mit einem der beiden zulässigen Innenregisterkartenformate übereinstimmen.

- Benutzer müssen nur über die Tastatur mit den Steuerelementen interagieren können. entweder durch Aktivieren des Editors und Tabing durch Steuerelemente oder durch Verwendung von Standard-Mnemonics.

- Der Designer sollte das gemeinsame Speichern-Modell verwenden. Es sollten keine allgemeinen Schaltflächen zum Speichern oder Commit auf der Oberfläche platziert werden, obwohl andere Schaltflächen möglicherweise geeignet sind.

#### <a name="model-designers"></a>Modelldesigner

- Ein leerer Designer sollte ein Wasserzeichen auf der Oberfläche haben, das anzeigt, wie sie beginnen sollen.

- Das Hinzufügen von Elementen zur Entwurfsoberfläche sollte über die Toolbox erfolgen.

- Elemente auf der Oberfläche folgen einem konsistenten Auswahlmodell.

- Eingebettete Symbolleisten enthalten nur dokumentspezifische Befehle, keine allgemeinen Befehle wie **Speichern**.

- Eine Legende kann auf der Oberfläche erscheinen, entweder indikativ oder ein Wasserzeichen.

- Der Benutzer muss in der Lage sein, die Darstellung der Schriftarten/Farben mithilfe einer Seite **"Tools > Options"** anzupassen, entweder auf der Seite "freigegebene Schriftarten und Farben" oder auf der Seite "Schriftarten und Farben" oder auf der Seite "Schriftarten" oder auf der für den Editor spezifischen.

#### <a name="reports"></a>Berichte

- Berichte sind in der Regel nur Informationen und nehmen nicht am Speichernmodell teil. Sie können jedoch Interaktionen wie Links zu anderen relevanten Informationen oder Abschnitte enthalten, die erweitert und reduziert werden.

- Die meisten Befehle auf der Oberfläche sollten Hyperlinks und keine Schaltflächen sein.

- Das Layout sollte einen Header enthalten und die Standardrichtlinien für das Berichtslayout befolgen.

#### <a name="dashboards"></a>Dashboards

- Dashboards verfügen selbst nicht über ein Interaktionsmodell, sondern dienen als Mittel, um eine Vielzahl anderer Tools anzubieten.

- Sie nehmen nicht am Save-Modell teil.

- Benutzer müssen nur über die Tastatur mit den Steuerelementen interagieren können, entweder durch Aktivieren des Editors und Tabing durch Steuerelemente oder durch Verwendung von Standard-Mnemonics.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>Dialoge

### <a name="introduction"></a>Einführung
Dialogfelder in Visual Studio sollten in der Regel eine diskrete Einheit der Arbeit des Benutzers unterstützen und dann verworfen werden.

Wenn Sie festgestellt haben, dass Sie ein Dialogfeld benötigen, haben Sie drei Möglichkeiten in der Reihenfolge ihrer Präferenz:

1. Integrieren Sie Ihre Features in einen der freigegebenen Dialogfelder in Visual Studio.

2. Erstellen Sie Ein eigenes Dialogfeld mit einem Muster, das in einem vorhandenen ähnlichen Dialogfeld gefunden wurde.

3. Erstellen Sie ein neues Dialogfeld, das den Interaktions- und Layoutrichtlinien folgt.

In diesem Abschnitt wird beschrieben, wie Sie das richtige Dialogmuster in Visual Studio-Workflows und die allgemeinen Konventionen für den Dialogentwurf auswählen.

### <a name="themes"></a>Designs
Dialoge in Visual Studio folgen einem von zwei grundlegenden Stilen:

#### <a name="standard-unthemed"></a>Standard (unthematisch)
Die meisten Dialoge sind Standard-Utility-Dialoge und sollten nicht thematisiert werden. Legen Sie keine allgemeinen Steuerelemente neu vor oder versuchen Sie nicht, stilisierte "moderne" Schaltflächen oder Steuerelemente zu erstellen. Steuerelemente und Chromdarstellung befolgen [standardmäßige Windows Desktop-Interaktionsrichtlinien für Dialogfelder](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>Themen
Spezielle "Signatur"-Dialoge können thematisiert werden. Thematische Dialoge haben ein deutliches Erscheinungsbild, das auch einige spezielle Interaktionsmuster hat, die mit dem Stil verknüpft sind. Theme Ihr Dialogfeld nur, wenn er die folgenden Anforderungen erfüllt:

- Das Dialogfeld ist eine häufige Erfahrung, die häufig oder von vielen Benutzern (z. B. im Dialogfeld **"Neues Projekt"** ( angezeigt und verwendet wird.

- Das Dialogfeld enthält prominente Produktmarkenelemente (z. B. das Dialogfeld **Kontoeinstellungen).**

- Das Dialogfeld wird als integraler Bestandteil eines größeren Flows angezeigt, der andere Themendialoge enthält (z. B. das Dialogfeld **Verbundener Dienst hinzufügen).**

- Der Dialog ist ein wichtiger Teil einer Erfahrung, die eine strategische Rolle bei der Förderung oder Differenzierung einer Produktversion spielt.

Verwenden Sie beim Erstellen eines thematischen Dialogfelds die entsprechenden Umgebungsfarben, und befolgen Sie die richtigen Layout- und Interaktionsmuster. (Siehe [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Dialog-Design
Gut gestaltete Dialoge berücksichtigen die folgenden Elemente:

- Die unterstützte Benutzeraufgabe

- Dialogtextformat, Sprache und Terminologie

- Steuerungsauswahl und UI-Konventionen

- Visuelle Layoutspezifikation und Steuerungsausrichtung

- Tastaturzugriff

#### <a name="content-organization"></a>Inhaltsorganisation
Berücksichtigen Sie die Unterschiede zwischen diesen grundlegenden Dialogtypen:

- [Einfache Dialoge](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) stellen Steuerelemente in einem einzigen Modalfenster dar. Die Präsentation kann Variationen komplexer Steuerelementmuster enthalten, einschließlich einer Feldauswahl oder einer Symbolleiste.

- [Layered-Dialoge](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) werden verwendet, um das Beste aus Bildschirmimmobilien zu machen, wenn ein einzelnes Stück Benutzeroberfläche mehrere Gruppen von Steuerelementen umfasst. Die Gruppierungen des Dialogfelds werden über Registerkartensteuerelemente, Navigationslistensteuerelemente oder Schaltflächen "überlagert", sodass der Benutzer auswählen kann, welche Gruppierung zu einem bestimmten Zeitpunkt angezeigt werden soll.

- [Assistenten](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sind nützlich, um den Benutzer durch eine logische Abfolge von Schritten zum Abschluss einer Aufgabe zu führen. Eine Reihe von Auswahlmöglichkeiten werden in sequenziellen Panels angeboten, die manchmal verschiedene Workflows ("Zweige") einführen, die von einer Auswahl im vorherigen Panel abhängen.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Einfache Dialoge
Ein einfaches Dialogfeld ist eine Darstellung von Steuerelementen in einem einzelnen Modalfenster. Diese Präsentation kann Variationen komplexer Steuerelementmuster enthalten, z. B. einer Feldauswahl. Für einfache Dialoge folgen Sie dem allgemeinen Standardlayout sowie einem beliebigen Layout, das für komplexe Steuerungsgruppierungen erforderlich ist.

![>Erstellen eines Schlüssels für einen starken Namen ist ein Beispiel für ein einfaches Dialogfeld in Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />"Strong Name Key erstellen" ist ein Beispiel für ein einfaches Dialogfeld in Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Layered-Dialoge
Layered-Dialoge umfassen Registerkarten, Dashboards und eingebettete Strukturen. Sie werden verwendet, um Immobilien zu maximieren, wenn mehrere Gruppen von Steuerelementen in einem einzigen Stück Benutzeroberfläche angeboten werden. Die Gruppierungen sind geschichtet, sodass der Benutzer auswählen kann, welche Gruppierung gleichzeitig angezeigt werden soll.

Im einfachsten Fall ist der Mechanismus zum Wechseln zwischen Gruppierungen ein Tabstopp-Steuerelement. Es gibt mehrere Alternativen zur Verfügung. Unter Priorisieren und Layernfür die Auswahl des am besten geeigneten Stils finden Sie unter Priorisieren und Layering.

Das Dialogfeld **Werkzeuge &gt; Optionen** ist ein Beispiel für ein mehrstufiges Dialogfeld, das eine eingebettete Struktur verwendet:

![Tools > Options ist ein Beispiel für ein mehrstufiges Dialogfeld in Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Tools > Options ist ein Beispiel für ein mehrstufiges Dialogfeld in Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>Assistenten
Assistenten sind nützlich, um den Benutzer durch eine logische Abfolge von Schritten beim Abschluss einer Aufgabe zu leiten. Eine Reihe von Optionen werden in sequenziellen Bedienfeldern angeboten, und der Benutzer muss jeden Schritt durchlaufen, bevor er mit dem nächsten fortfahren kann. Sobald genügend Standardwerte verfügbar sind, ist die Schaltfläche **Fertig** stellen aktiviert.

 Modal-Assistenten werden für Aufgaben verwendet, die:

- Einschließen von Verzweigungen, bei denen je nach Benutzerauswahl unterschiedliche Pfade angeboten werden

- Abhängigkeiten zwischen Schritten enthalten, wobei nachfolgende Schritte von Benutzereingaben aus dem vorherigen Schritt(n) abhängen

- Sind so komplex, dass die Benutzeroberfläche verwendet werden sollte, um die angebotenen Auswahlmöglichkeiten und die möglichen Ergebnisse in jedem Schritt zu erläutern

- Sind transaktional und erfordern eine Reihe von Schritten, die vollständig abgeschlossen werden müssen, bevor Änderungen vorgenommen werden

### <a name="common-conventions"></a>Gemeinsame Konventionen
Um mit Ihren Dialogfeldern ein optimales Design und eine optimale Funktionalität zu erzielen, befolgen Sie diese Konventionen zu Dialoggröße, Position, Standards, Steuerungskonfiguration und -ausrichtung, UI-Text, Titelleisten, Steuertasten und Zugriffstasten.

Layoutspezifische Richtlinien finden Sie unter [Layout für Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Size
Dialoge sollten innerhalb einer Bildschirmauflösung von mindestens 1024x768 passen, und die anfängliche Dialogfeldgröße sollte 900x700 Pixel nicht überschreiten. Dialoge können in der Geänderten Datei geändert werden, sind jedoch keine Voraussetzung.

Es gibt zwei Empfehlungen für änderungsbare Dialoge:

1. Dass eine Mindestgröße für das Dialogfeld definiert ist, das für den Steuerelementsatz ohne Clipping optimiert und angepasst wird, um ein angemessenes Lokalisierungswachstum zu berücksichtigen.

2. Dass die vom Benutzer skalierte Größe von Sitzung zu Sitzung beibehalten wird. Wenn der Benutzer z. B. ein Dialogfeld auf 150 % skaliert, wird ein nachfolgender Start des Dialogfelds mit 150 % angezeigt.

#### <a name="position"></a>Position
Dialoge müssen beim ersten Start zentriert in der IDE angezeigt werden. Die letzte Position nicht übertragbarer Dialogfelder muss nicht beibehalten werden, sodass sie auf nachfolgende Starts zentriert angezeigt werden.

Bei größenänderungsfähigen Dialogfeldern sollte die Größe bei nachfolgenden Starts beibehalten werden. Für geänderte Modaldialoge muss die Position nicht beibehalten werden. Die Anzeige innerhalb der IDE zentriert verhindert, dass der Dialog an einer unvorhersehbaren oder unbrauchbaren Position angezeigt wird, wenn sich die Anzeigekonfiguration des Benutzers geändert hat.

Bei moduslosen Dialogen, die neu positioniert werden können, sollte die Position des Benutzers bei nachfolgenden Starts beibehalten werden, da das Dialogfeld häufig als integraler Bestandteil eines größeren Workflows verwendet werden kann.

Wenn Dialogfelder andere Dialogfelder erstellen müssen, sollte das oberste Dialogfeld vom übergeordneten Element nach rechts und unten kaskadieren, sodass für den Benutzer offensichtlich ist, dass er zu einem neuen Ort navigiert ist.

#### <a name="modality"></a>Modalität
Modal bedeutet, dass Benutzer das Dialogfeld abschließen oder abbrechen müssen, bevor sie fortfahren. Da modale Dialogfelder den Benutzer daran hindern, mit anderen Teilen der Umgebung zu interagieren, sollte der Aufgabenfluss Ihres Features diese so sparsam wie möglich verwenden. Wenn ein modaler Vorgang erforderlich ist, verfügt Visual Studio über eine Reihe freigegebener Dialogfelder, in die Sie Ihre Features integrieren können. Wenn Sie ein neues Dialogfeld erstellen müssen, folgen Sie dem Interaktionsmuster eines vorhandenen Dialogfelds mit ähnlicher Funktionalität.

Wenn Benutzer beim Schreiben von neuem Code zwei Aktivitäten gleichzeitig ausführen müssen, z. B. **Suchen** und **Ersetzen,** sollte das Dialogfeld moduslos sein, damit der Benutzer problemlos zwischen ihnen wechseln kann. Visual Studio verwendet in der Regel Toolfenster für diese Art von editorunterstützenden verknüpften Aufgaben.

#### <a name="control-configuration"></a>Steuerungskonfiguration
Seien Sie konsistent mit vorhandenen Steuerelementkonfigurationen, die dasselbe in Visual Studio erreichen.

#### <a name="title-bars"></a>Titelleisten

- Der Text in der Titelleiste muss den Namen des Befehls widerspiegeln, der ihn gestartet hat.

- In Dialogtitelleisten sollte kein Symbol verwendet werden. Verwenden Sie in Fällen, in denen das System eines erfordert, das Visual Studio-Logo.

- Dialoge sollten keine Schaltflächen minimieren oder maximieren.

- Die Hilfeschaltflächen in der Titelleiste sind veraltet. Fügen Sie sie nicht zu neuen Dialogfeldern hinzu. Wenn sie vorhanden sind, sollten sie ein Hilfethema starten, das für die Aufgabe konzeptionell relevant ist.

  ![Richtlinienspezifikationen für Titelleisten in Visual Studio-Dialogfeldern](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Richtlinienspezifikationen für Titelleisten in Visual Studio-Dialogfeldern

#### <a name="control-buttons"></a>Steuertasten
Im Allgemeinen sollten **ok**, **Abbrechen**und **Hilfe-Schaltflächen** horizontal in der unteren rechten Ecke des Dialogs angeordnet werden. Der alternative vertikale Stapel ist zulässig, wenn ein Dialogfeld mehrere andere Schaltflächen am unteren Rand des Dialogfelds enthält, die visuelle Verwirrung mit den Steuerelementschaltflächen darstellen würden.

![Akzeptable Konfigurationen für Steuerschaltflächen in Visual Studio-Dialogfeldern](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Akzeptable Konfigurationen für Steuerschaltflächen in Visual Studio-Dialogfeldern

Das Dialogfeld muss eine Standard-Steuerelementschaltfläche enthalten. Um den besten Befehl zu bestimmen, der als Standard verwendet werden soll, wählen Sie aus den folgenden Optionen (in der Reihenfolge der Rangfolge aufgeführt):

- Wählen Sie als Standard den sichersten und sichersten Befehl aus. Dies bedeutet, dass Sie den Befehl auswählen, der am ehesten Datenverlust verhindert und unbeabsichtigten Systemzugriff verhindert.

- Wenn Datenverlust und Sicherheit keine Faktoren sind, wählen Sie den Standardbefehl basierend auf der Bequemlichkeit aus. Wenn Sie den wahrscheinlichsten Befehl als Standard verwenden, wird der Workflow des Benutzers verbessert, wenn das Dialogfeld häufige oder sich wiederholende Aufgaben unterstützt.

Vermeiden Sie die Auswahl einer dauerhaft destruktiven Aktion für den Standardbefehl. Wenn ein solcher Befehl vorhanden ist, wählen Sie stattdessen einen sichereren Befehl als Standard.

#### <a name="access-keys"></a>Zugriffsschlüssel
Verwenden Sie keine Zugriffstasten für **OK-,** **Abbruch-** oder **Hilfeschaltflächen.** Diese Tasten werden standardmäßig Tastenkombinationen zugeordnet:

| Schaltflächenname | Tastenkombinationen |
| --- | --- |
| OK | EINGABETASTE |
| Abbrechen | Esc |
| Hilfe | F1 |

#### <a name="imagery"></a>Bilder
Verwenden Sie Bilder sparsam in Dialogen. Verwenden Sie keine großen Symbole in Dialogfeldern, nur um Speicherplatz zu verbrauchen. Verwenden Sie Bilder nur, wenn sie ein wichtiger Teil der Übermittlung der Nachricht an den Benutzer sind, z. B. Warnsymbole oder Statusanimationen.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Priorisieren und Layern

#### <a name="prioritizing-your-ui"></a>Priorisieren der Benutzeroberfläche
Es kann erforderlich sein, bestimmte UI-Elemente in den Vordergrund zu stellen und erweitertes Verhalten und Optionen (einschließlich obskurer Befehle) in Dialoge zu platzieren. Bringen Sie häufig verwendete Funktionen in den Vordergrund, indem Sie Platz dafür schaffen und sie standardmäßig in der Benutzeroberfläche mit einer Textbeschriftung sichtbar machen, wenn das Dialogfeld angezeigt wird.

#### <a name="layering-your-ui"></a>Layern der Benutzeroberfläche
Wenn Sie festgestellt haben, dass ein Dialogfeld erforderlich ist, die zugehörige Funktionalität, die Sie dem Benutzer präsentieren möchten, über das hinausgeht, was in einem einfachen Dialogfeld angezeigt werden kann, müssen Sie die Benutzeroberfläche überlagern. Die gängigsten Layering-Methoden, die Visual Studio verwendet, sind Registerkarten und Flure oder Dashboards. In einigen Fällen können Regionen, die sich erweitern und zusammenbrechen können, geeignet sein. Die adaptive Benutzeroberfläche wird in Visual Studio im Allgemeinen nicht empfohlen.

Es gibt Vor- und Nachteile für verschiedene Methoden der Überlagerung der Benutzeroberfläche durch tab-ähnliche Steuerelemente. Überprüfen Sie die folgende Liste, um sicherzustellen, dass Sie eine Layering-Technik auswählen, die ihrer Situation entspricht.

##### <a name="tabbing"></a>Wechseln mit der Tabulatortaste

| Schaltmechanismus | Vorteile und sachgerechte Nutzung | Nachteile und unsachgemäße Verwendung |
| --- | --- | --- |
| Registersteuerelement | Logische Gruppierung von Dialogseiten in verwandten Sätzen<br /><br />Nützlich für weniger als fünf (oder die Anzahl der Registerkarten, die in eine Zeile über das Dialogfeld passen) Mit verknüpften Steuerelementen im Dialogfeld<br /><br />Tab-Etiketten müssen kurz sein: ein oder zwei Wörter, die den Inhalt leicht identifizieren können<br /><br />Ein gemeinsamer Systemdialogstil<br /><br />Beispiel: **Elementeigenschaften des &gt; Datei-Explorers** | Beschreibende Kurzbeschriftungen können schwierig sein<br /><br />Im Allgemeinen wird nicht über fünf Registerkarten in einem Dialog skaliert<br /><br />Ungeeignet, wenn Sie zu viele Registerkarten für eine Zeile haben (verwenden Sie eine alternative Layering-Technik)<br /><br />Nicht erweiterbar |
| Sidebar-Navigation | Einfaches Switching-Gerät, das mehr Kategorien als Tabs aufnehmen kann<br /><br />Flache Liste der Kategorien (keine Hierarchie)<br /><br />Erweiterbarkeit<br /><br />Beispiel: **Anpassen... Befehl &gt; hinzufügen** | Keine gute Nutzung des horizontalen Raums, wenn weniger als drei Gruppen vorhanden sind<br /><br />Aufgabe könnte besser für einen Dropdown geeignet sein |
| Baumsteuerelement | Erlaubt unbegrenzte Kategorien<br /><br />Ermöglicht das Gruppieren und/oder die Hierarchie von Kategorien<br /><br />Erweiterbarkeit<br /><br />Beispiel: ** &gt; Tools-Optionen** | Stark verschachtelte Hierarchien können zu übermäßiges horizontales Scrollen führen<br /><br />Visual Studio verfügt über eine Überfülle an Baumansichten |
| Assistent | Hilft bei der Aufgabenvervollständigung, indem er den Benutzer durch aufgabenbasierte, sequenzielle Schritte führt: Der Assistent stellt eine übergeordnete Aufgabe dar, und die einzelnen Bedienfelder stellen Teilaufgaben dar, die zum Ausführen der Gesamtaufgabe erforderlich sind.<br /><br />Nützlich, wenn die Aufgabe Ui-Grenzen überschreitet, z. B. wenn der Benutzer andernfalls mehrere Editoren und Toolfenster verwenden müsste, um die Aufgabe abzuschließen<br /><br />Nützlich, wenn die Aufgabe verzweigt werden muss<br /><br />Nützlich, wenn die Aufgabe Abhängigkeiten zwischen Schritten enthält<br /><br />Nützlich, wenn mehrere ähnliche Aufgaben mit einer Entscheidungsgabel in einem Dialogfeld dargestellt werden können, um die Anzahl der verschiedenen ähnlichen Dialoge zu reduzieren | Ungeeignet für jede Aufgabe, für die kein sequenzieller Workflow erforderlich ist<br /><br />Benutzer können von einem Assistenten mit zu vielen Schritten überwältigt und verwirrt werden<br /><br />Wizards haben inhärent begrenzte Bildschirmimmobilien |

##### <a name="hallways-or-dashboards"></a>Flure oder Armaturenbretter
Flure und Dashboards sind Dialoge oder Bedienfelder, die als Startpunkte für andere Dialoge und Fenster dienen. Der gut gestaltete "Flur" zeigt sofort nur die gängigsten Optionen, Befehle und Einstellungen, sodass der Benutzer problemlos gemeinsame Aufgaben ausführen kann. Wie ein realer Flur Türöffnungen für den Zugang zu den Räumen hinter ihnen bietet, wird hier die weniger häufige Benutzeroberfläche in separaten "Räumen" (oft andere Dialoge) mit verwandten Funktionen gesammelt, die vom Hauptflur aus zugänglich sind.

Alternativ ist eine Benutzeroberfläche, die alle verfügbaren Funktionen in einer einzigen Sammlung bietet, anstatt die weniger häufigen Funktionen in separate Speicherorte umzugestalten, einfach ein Dashboard.

![Flurkonzept zum Aufstellen zusätzlicher Benutzeroberfläche in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Flurkonzept zum Aufstellen zusätzlicher Benutzeroberfläche in Outlook

##### <a name="adaptive-ui"></a>Adaptive UI
Das Anzeigen oder Ausblenden der Benutzeroberfläche basierend auf der Verwendung oder der selbst gemeldeten Benutzererfahrung ist eine weitere Möglichkeit, die erforderliche Benutzeroberfläche darzustellen, während andere Teile ausgeblendet werden. Dies wird in Visual Studio nicht empfohlen, da die Algorithmen für die Entscheidung, wann die Benutzeroberfläche ein- oder ausgeblendet werden soll, schwierig sein können und die Regeln für einige Fälle immer falsch sind.

## <a name="projects"></a><a name="BKMK_Projects"></a>Projekte

### <a name="projects-in-the-solution-explorer"></a>Projekte im Projektmappen-Explorer
Die meisten Projekte werden als referenzbasiert, verzeichnisbasiert oder gemischt klassifiziert. Alle drei Projekttypen werden gleichzeitig im Projektmappen-Explorer unterstützt. Der Stamm der Benutzererfahrung bei der Arbeit mit Projekten findet in diesem Fenster statt. Obwohl verschiedene Projektknoten Referenz-, Verzeichnis- oder Mixed-Mode-Typprojekte sind, gibt es ein gemeinsames Interaktionsmuster, das als Ausgangspunkt angewendet werden sollte, bevor es in projektspezifische Benutzermuster abweicht.

Projekte sollten immer:

- Unterstützung der Möglichkeit, Projektordner zum Organisieren von Projektinhalten hinzuzufügen

- Aufrechterhaltung eines konsistenten Modells für die Projektpersistenz

Projekte sollten auch konsistente Interaktionsmodelle beibehalten für:

- Entfernen von Projektelementen

- Speichern von Dokumenten

- Bearbeitung von Projekteigenschaften

- Bearbeiten des Projekts in einer anderen Ansicht

- Drag-and-Drop-Vorgänge

### <a name="drag-and-drop-interaction-model"></a>Drag-and-Drop-Interaktionsmodell
Projekte klassifizieren sich in der Regel als referenzbasiert (in der Lage, nur Verweise auf Projektelemente im Speicher beizubehalten), verzeichnisbasiert (nur Projektelemente, die physisch in der Hierarchie eines Projekts gespeichert sind) oder gemischt (in der Lage, Verweise beizubehalten). oder physische Gegenstände). Die IDE berücksichtigt alle drei Projekttypen gleichzeitig im **Projektmappen-Explorer**.

Aus Drag-and-Drop-Perspektive sollten die folgenden Merkmale für jeden Projekttyp im **Projektmappen-Explorer**gelten:

- **Referenzbasiertes Projekt:** Der entscheidende Punkt ist, dass das Projekt um einen Verweis auf ein Element im Speicher gezogen wird. Wenn ein referenzbasiertes Projekt als Quelle für einen Verschiebungsvorgang fungiert, sollte nur der Verweis auf das Element aus dem Projekt entfernt werden. Das Element sollte eigentlich nicht von der Festplatte gelöscht werden. Wenn ein referenzbasiertes Projekt als Ziel für einen Verschiebungs- (oder Kopier-)Vorgang fungiert, sollte es einen Verweis auf das ursprüngliche Quellelement hinzufügen, ohne eine private Kopie des Elements zu erstellen.

- **Verzeichnisbasiertes Projekt:** Aus Drag-and-Drop-Sicht wird das Projekt um das physische Element und nicht um einen Verweis gezogen. Wenn ein verzeichnisbasiertes Projekt als Quelle für einen Verschiebungsvorgang fungiert, sollte es das physische Element von der Festplatte löschen und aus dem Projekt entfernen. Wenn ein verzeichnisbasiertes Projekt als Ziel für einen Verschiebungs- (oder Kopier-)Vorgang fungiert, sollte es eine Kopie des Quellelements an seinem Zielspeicherort erstellen.

- **Projekt mit gemischtem Ziel:** Aus Drag-and-Drop-Sicht basiert das Verhalten dieses Projekttyps auf der Art des gezogenen Elements (entweder ein Verweis auf ein Lagerelement oder das Element selbst). Das korrekte Verhalten für Referenzen und physische Elemente wird oben beschrieben.

Wenn im **Projektmappen-Explorer**nur ein Projekttyp vorhanden wäre, wäre das Ziehen und Ablegen von Vorgängen einfach. Da jedes Projektsystem die Möglichkeit hat, sein eigenes Drag-and-Drop-Verhalten zu definieren, sollten bestimmte Richtlinien (basierend auf dem Drag-and-Drop-Verhalten des Windows Explorer) befolgt werden, um eine vorhersagbare Benutzererfahrung zu gewährleisten:

- Ein unveränderter Ziehvorgang im **Projektmappen-Explorer** (wenn weder Strg- noch Umschalttasten gedrückt gehalten werden) sollte zu einem Verschiebungsvorgang führen.

- Der Umschalt-Drag-Vorgang sollte auch zu einem Verschiebungsvorgang führen.

- Der Strg-Drag-Vorgang sollte zu einem Kopiervorgang führen.

- Referenzbasierte und gemischte Projektsysteme unterstützen den Begriff des Hinzufügens eines Links (oder Verweises) zum Quellelement. Wenn diese Projekte das Ziel eines Drag-and-Drop-Vorgangs sind (wenn **Strg + Umschalttaste** gedrückt wird), sollte dies zu einem Verweis auf das Element führen, das dem Projekt hinzugefügt wird.

Nicht alle Drag-and-Drop-Vorgänge sind in Kombinationen von referenzbasierten, verzeichnisbasierten und gemischten Projekten sinnvoll. Insbesondere ist es problematisch, so zu tun, als ob ein Verschiebungsvorgang zwischen einem verzeichnisbasierten Quellprojekt und einem referenzbasierten Zielprojekt zugelassen werden könnte, da das Quellverzeichnis-basierte Projekt das Quellelement nach Abschluss der Verschiebung löschen muss. Das Zielreferenzprojekt würde dann mit einem Verweis auf ein gelöschtes Element enden.

Es ist auch irreführend, so zu tun, als ob ein Kopiervorgang zwischen diesen Projekttypen zugelassen wird, da das Zielreferenzprojekt keine unabhängige Kopie des Quellelements erstellen sollte. Ebenso sollte das Ziehen von Strg + Umschaltin in ein verzeichnisbasiertes Zielprojekt nicht zulässig sein, da ein verzeichnisbasiertes Projekt keine Verweise beibehalten kann. In Fällen, in denen der Drag-and-Drop-Vorgang nicht unterstützt wird, sollte die IDE das Ablegen nicht zulassen und dem Benutzer den No-Drop-Cursor anzeigen (siehe Zeigertabelle unten).

Um das Drag-and-Drop-Verhalten ordnungsgemäß zu implementieren, muss das Quellprojekt des Drags seine Art an das Zielprojekt kommunizieren. (Ist es z. B. referenz- oder verzeichnisbasiert?) Diese Informationen werden durch das Zwischenablageformat angezeigt, das von der Quelle angeboten wird. Als Quelle eines Drags (oder Zwischenablagekopievorgangs) sollte ein Projekt entweder `CF_VSREFPROJECTITEMS` oder `CF_VSSTGPROJECTITEMS` beziehungsweise anbieten, je nachdem, ob das Projekt referenzbasiert oder verzeichnisbasiert ist. Beide Formate haben den gleichen Dateninhalt, der `CF_HDROP` dem Windows-Format`NULL` ähnelt, mit der Ausnahme, dass Listen `Projref` von Zeichenfolgen `IVsSolution::GetProjrefOfItem` anstelle von Dateinamen eine doppelt beendete Liste von Zeichenfolgen sind (wie von oder `::GetProjrefOfProject` je nach Bedarf zurückgegeben).

Als Ziel eines Drop-Vorgangs (oder Zwischenablage-Einfügevorgangs) sollte ein Projekt sowohl `CF_VSREFPROJECTITEMS` und `CF_VSSTGPROJECTITEMS`, obwohl die genaue Handhabung des Drag-and-Drop-Vorgangs je nach Art des Zielprojekts und des Quellprojekts variiert. Das Quellprojekt erklärt seine Art, ob es anbietet `CF_VSREFPROJECTITEMS` oder `CF_VSSTGPROJECTITEMS`. Das Ziel des Tropfens versteht seine eigene Natur und verfügt daher über genügend Informationen, um Entscheidungen darüber zu treffen, ob ein Umzug, eine Kopie oder ein Link ausgeführt werden soll. Der Benutzer ändert auch, welche Drag-and-Drop-Operation durch Drücken der Strg-, Umschalt- oder Strg- und Umschalttaste ausgeführt werden soll. Es ist wichtig, dass das Drop-Ziel richtig angibt, welche Operation im Voraus in seinem `DragEnter` und `DragOver` ihren Methoden durchgeführt wird. Der **Projektmappen-Explorer** weiß automatisch, ob das Quellprojekt und das Zielprojekt dasselbe Projekt sind.

Das Ziehen von Projektelementen über Instanzen von Visual Studio (z. B. von einer Instanz von devenv.exe zu einer anderen) wird ausdrücklich nicht unterstützt. Der **Projektmappen-Explorer** deaktiviert dies auch direkt.

Der Benutzer sollte immer in der Lage sein, die Auswirkungen eines Drag-and-Drop-Vorgangs zu bestimmen, indem er ein Element auswählt, es an die Zielposition zieht und beobachtet, welche der folgenden Mauszeiger angezeigt werden, bevor das Element gelöscht wird:

| Mauszeiger | Get-Help | Beschreibung |
| :---: | --- | --- |
| ![Symbol „Keine Ablage“ für Maus](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Kein Tropfen | Das Element kann nicht an den angegebenen Speicherort gelöscht werden. |
| ![Symbol "Kopieren" für Maus](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Kopieren | Das Element wird an den Zielspeicherort kopiert. |
| ![Symbol "Verschieben" für Maus](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Move | Das Element wird an den Zielspeicherort verschoben. |
| ![Symbol "Verweis hinzufügen" für Maus](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Hinzuzufügender Verweis | Dem Ziellagerort wird ein Verweis auf das ausgewählte Element hinzugefügt. |

#### <a name="reference-based-projects"></a>Referenzbasierte Projekte
 Die folgende Tabelle fasst die Drag-and-Drop-Vorgänge (sowie Ausschneiden/Kopieren/Einfügen) zusammen, die basierend auf der Art des Quellelements und der Modifikatortasten ausgeführt werden sollten, die für referenzierte Zielprojekte gedrückt werden:

| Modifizierer | Category | Quellpunkt: Referenz/Link | Quellelement: Physisches Element`CF_HDROP`oder Dateisystem ( ) |
| --- | --- | --- | --- |
| Kein Modifikator | Aktion | Move | Link |
| Kein Modifikator | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Fügt Referenz zum ursprünglichen Element hinzu |
| Kein Modifikator | `Source` | Löscht den Verweis auf das ursprüngliche Element | Behält das Originalelement bei |
| Kein Modifikator | Ergebnis | `DROPEFFECT_MOVE`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | `DROPEFFECT_LINK`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager |
| Shift+Drag | Aktion | Move | Kein Tropfen |
| Shift+Drag | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Kein Tropfen |
| Shift+Drag | `Source` | Löscht den Verweis auf das ursprüngliche Element | Kein Tropfen |
| Shift+Drag | Ergebnis | `DROPEFFECT_MOVE`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | Kein Tropfen |
| Strg+Ziehen | Aktion | Kopieren | Kein Tropfen |
| Strg+Ziehen | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Kein Tropfen |
| Strg+Ziehen | `Source` | Behält den Verweis auf das Originalelement bei | Kein Tropfen |
| Strg+Ziehen | Ergebnis | `DROPEFFECT_COPY`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | Kein Tropfen |
| Strg+Umschalt+Ziehen | Aktion | Link | Link |
| Strg+Umschalt+Ziehen | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Fügt Referenz zum ursprünglichen Element hinzu |
| Strg+Umschalt+Ziehen | `Source` | Behält den Verweis auf das Originalelement bei | Behält das Originalelement bei |
| Strg+Umschalt+Ziehen | Ergebnis | `DROPEFFECT_LINK`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | `DROPEFFECT_LINK`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager |
| Strg+Umschalt+Ziehen | Hinweis | Genauso wie Drag-and-Drop-Verhalten für Verknüpfungen im Windows Explorer. ||
| Ausschneiden/Einfügen | Aktion | Move | Link |
| Ausschneiden/Einfügen | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Fügt Referenz zum ursprünglichen Element hinzu |
| Ausschneiden/Einfügen | `Source` | Behält den Verweis auf das Originalelement bei|Behält das Originalelement bei |
| Ausschneiden/Einfügen | Ergebnis | Artikel verbleibt am ursprünglichen Lagerort | Artikel verbleibt am ursprünglichen Lagerort |
| Kopieren/Einfügen | Aktion | Kopieren | Link |
| Kopieren/Einfügen | `Source` | Fügt Referenz zum ursprünglichen Element hinzu | Fügt Referenz zum ursprünglichen Element hinzu |
| Kopieren/Einfügen | Ergebnis | Behält den Verweis auf das Originalelement bei | Behält das Originalelement bei |
| Kopieren/Einfügen | Aktion | Artikel verbleibt am ursprünglichen Lagerort | Artikel verbleibt am ursprünglichen Lagerort |

#### <a name="directory-based-projects"></a>Verzeichnisbasierte Projekte
Die folgende Tabelle fasst die Drag-and-Drop-Vorgänge (sowie Ausschneiden/Kopieren/Einfügen) zusammen, die basierend auf der Art des Quellelements und der Modifikatortasten ausgeführt werden sollten, die für verzeichnisbasierte Zielprojekte gedrückt werden:

| Modifizierer | Category | Quellpunkt: Referenz/Link | Quellelement: Physisches Element`CF_HDROP`oder Dateisystem ( ) |
|-----------------|----------| - | - |
| Kein Modifikator | Aktion | Move | Move |
| Kein Modifikator | Ziel | Kopiert Element an den Zielspeicherort | Kopiert Element an den Zielspeicherort |
| Kein Modifikator | `Source` | Löscht den Verweis auf das ursprüngliche Element | Löscht den Verweis auf das ursprüngliche Element |
| Shift+Drag | Aktion | Move | Move |
| Shift+Drag | Ziel | Kopiert Element an den Zielspeicherort | Kopiert Element an den Zielspeicherort |
| Shift+Drag | `Source` | Löscht den Verweis auf das ursprüngliche Element | Löscht Das Element vom ursprünglichen Lagerort |
| Shift+Drag | Ergebnis | `DROPEFFECT_MOVE`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | `DROPEFFECT_MOVE`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager |
| Strg+Ziehen | Aktion | Kopieren | Kopieren |
| Strg+Ziehen | Ziel | Kopiert Element an den Zielspeicherort | Kopiert Element an den Zielspeicherort |
| Strg+Ziehen | `Source` | Behält den Verweis auf das Originalelement bei | Behält den Verweis auf das Originalelement bei |
| Strg+Ziehen | Ergebnis | `DROPEFFECT_COPY`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | `DROPEFFECT_COPY`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager |
| Strg+Umschalt+Ziehen | | Kein Tropfen | Kein Tropfen |
| Ausschneiden/Einfügen | Aktion | Move | Move |
| Ausschneiden/Einfügen | Ziel | Kopiert Element an den Zielspeicherort | Kopiert Element an den Zielspeicherort |
| Ausschneiden/Einfügen | `Source` | Löscht den Verweis auf das ursprüngliche Element | Löscht Das Element vom ursprünglichen Lagerort |
| Ausschneiden/Einfügen | Ergebnis | Artikel verbleibt am ursprünglichen Lagerort | Element wird vom ursprünglichen Speicherort im Speicher gelöscht |
| Kopieren/Einfügen | Aktion | Kopieren | Kopieren |
| Kopieren/Einfügen | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Kopiert Element an den Zielspeicherort |
| Kopieren/Einfügen | `Source` | Behält das Originalelement bei | Behält das Originalelement bei |
| Kopieren/Einfügen | Ergebnis | Artikel verbleibt am ursprünglichen Lagerort | Artikel verbleibt im ursprünglichen Lagerort |

#### <a name="mixed-target-projects"></a>Projekte mit gemischten Zielen
Die folgende Tabelle fasst die Drag-and-Drop-Vorgänge (sowie Ausschneiden/Kopieren/Einfügen) zusammen, die basierend auf der Art des Quellelements und der Modifikatortasten ausgeführt werden sollten, die für Projekte mit gemischten Zielen gedrückt werden:

| Modifizierer | Category | Quellpunkt: Referenz/Link | Quellelement: Physisches Element`CF_HDROP`oder Dateisystem ( ) |
| --- | --- | --- | --- |
| Kein Modifikator | Aktion | Move | Move |
| Kein Modifikator | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Kopiert Element an den Zielspeicherort |
| Kein Modifikator | `Source` | Löscht den Verweis auf das ursprüngliche Element | Löscht den Verweis auf das ursprüngliche Element |
| Kein Modifikator | Ergebnis | `DROPEFFECT_ MOVE`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | `DROPEFFECT_ MOVE`wird als Aktion `::Drop` zurückgegeben, und das Element wird vom ursprünglichen Speicherort im Speicher gelöscht |
| Shift+Drag | Aktion | Move | Move |
| Shift+Drag | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Kopiert Element an den Zielspeicherort |
| Shift+Drag | `Source` | Löscht den Verweis auf das ursprüngliche Element | Löscht Das Element vom ursprünglichen Lagerort |
| Shift+Drag | Ergebnis | `DROPEFFECT_ MOVE`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | `DROPEFFECT_ MOVE`wird als Aktion `::Drop` zurückgegeben, und das Element wird vom ursprünglichen Speicherort im Speicher gelöscht |
| Strg+Ziehen | Aktion | Kopieren | Kopieren |
| Strg+Ziehen | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Kopiert Element an den Zielspeicherort |
| Strg+Ziehen | `Source` | Behält den Verweis auf das Originalelement bei | Behält das Originalelement bei |
| Strg+Ziehen | Ergebnis | `DROPEFFECT_ COPY`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | `DROPEFFECT_ COPY`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager |
| Strg+Umschalt+Ziehen | Aktion | Link | Link |
| Strg+Umschalt+Ziehen | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Fügt Verweise auf das ursprüngliche Quellelement hinzu |
| Strg+Umschalt+Ziehen | `Source` | Behält den Verweis auf das Originalelement bei | Behält das Originalelement bei |
| Strg+Umschalt+Ziehen | Ergebnis | `DROPEFFECT_ LINK`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager | `DROPEFFECT_ LINK`wird als Aktion `::Drop` zurückgegeben, und das Element verbleibt an der ursprünglichen Position im Lager |
| Ausschneiden/Einfügen | Aktion | Move | Move |
| Ausschneiden/Einfügen | Ziel | Kopiert Element an den Zielspeicherort | Kopiert Element an den Zielspeicherort |
| Ausschneiden/Einfügen | `Source` | Löscht den Verweis auf das ursprüngliche Element | Löscht Das Element vom ursprünglichen Lagerort |
| Ausschneiden/Einfügen | Ergebnis | Artikel verbleibt am ursprünglichen Lagerort | Element wird vom ursprünglichen Speicherort im Speicher gelöscht |
| Kopieren/Einfügen | Aktion | Kopieren | Kopieren |
| Kopieren/Einfügen | Ziel | Fügt Referenz zum ursprünglichen Element hinzu | Kopiert Element an den Zielspeicherort |
| Kopieren/Einfügen | `Source` | Behält das Originalelement bei | Behält das Originalelement bei |
| Kopieren/Einfügen | Ergebnis | Artikel verbleibt am ursprünglichen Lagerort | Artikel verbleibt am ursprünglichen Lagerort |

Diese Details sollten bei der Implementierung des Ziehens im **Projektmappen-Explorer**berücksichtigt werden:

- Entwurf für mehrere Auswahlszenarien.

- Dateinamen (vollständiger Pfad) müssen im gesamten Zielprojekt eindeutig sein, oder der Drop sollte nicht zulässig sein.

- Ordnernamen müssen eindeutig sein (bei Nichtberücksichtigen von Groß-/Kleinschreibung) auf der Ebene, auf der sie gelöscht werden.

- Es gibt Verhaltensunterschiede zwischen Dateien, die zum Zeitpunkt des Ziehens geöffnet oder geschlossen sind (in den oben genannten Szenarien nicht erwähnt).

- Dateien der obersten Ebene verhalten sich etwas anders als Dateien in Ordnern.

Ein weiteres Problem, das Sie beachten sollten, ist die Handhabung von Verschiebungsvorgängen für Elemente mit offenen Designern oder Editoren. Das erwartete Verhalten ist wie folgt (dies gilt für alle Projekttypen):

1. Wenn der geöffnete Editor/Designer keine nicht gespeicherten Änderungen hat, sollte das Editor/Designer-Fenster stillschweigend geschlossen werden.

2. Wenn der geöffnete Editor/Designer nicht gespeicherte Änderungen hat, sollte die Quelle des Ziehens warten, bis der Drop auftritt, und dann den Benutzer bitten, die nicht festgeschriebenen Änderungen in den geöffneten Dokumenten zu speichern, bevor das Fenster mit einer Eingabeaufforderung ähnlich der folgenden geschlossen wird:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Dies gibt dem Benutzer die Möglichkeit, laufende Arbeit zu speichern, bevor das Ziel seine Kopien erstellt. Eine neue `IVsHierarchyDropDataSource2::OnBeforeDropNotify` Methode wurde hinzugefügt, um diese Handhabung zu ermöglichen.

Das Ziel kopiert dann den Status des Elements, wie es sich im Speicher befindet (ohne die nicht gespeicherten Änderungen im Editor, wenn der Benutzer **Nein**ausgewählt hat). Nachdem das Ziel das Kopieren `IVsHierarchyDropDataSource::Drop`abgeschlossen hat (in ), erhält die Quelle die `IVsHierarchyDropDataSource::OnDropNotify`Möglichkeit, den Löschteil des Verschiebungsvorgangs (in ) abzuschließen.

Alle Editoren mit nicht gespeicherten Änderungen sollten offen gelassen werden. Für Dokumente mit nicht gespeicherten Änderungen bedeutet dies, dass der Kopierteil des Verschiebungsvorgangs ausgeführt wird, der Löschteil jedoch abgebrochen wird. In einem Szenario mit mehrfacher Auswahl, in dem der Benutzer **Nein**auswählt, sollten dokumente mit nicht gespeicherten Änderungen nicht geschlossen oder entfernt werden, aber die Dokumente ohne nicht gespeicherte Änderungen sollten geschlossen und entfernt werden.