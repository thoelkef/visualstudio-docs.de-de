---
title: Im Editor
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710325"
---
# <a name="inside-the-editor"></a>Innerhalb des Editors

Der Editor besteht aus verschiedenen Subsystemen, die das Editor-Textmodell von der Textansicht und der Benutzeroberfläche trennen sollen.

In diesen Abschnitten werden verschiedene Aspekte des Editors beschrieben:

- [Übersicht der Subsysteme](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Das Textmodell](../extensibility/inside-the-editor.md#the-text-model)

- [Die Textansicht](../extensibility/inside-the-editor.md#the-text-view)

In diesen Abschnitten werden die Funktionen des Editors beschrieben:

- [Tags und Klassifikatoren](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Verzierungen](../extensibility/inside-the-editor.md#adornments)

- [Projection](../extensibility/inside-the-editor.md#projection)

- [Gliedern](../extensibility/inside-the-editor.md#outlining)

- [Mausbindungen](../extensibility/inside-the-editor.md#mouse-bindings)

- [Editor-Operationen](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Übersicht der Subsysteme

### <a name="text-model-subsystem"></a>Textmodell-Subsystem

Das Teilsystem des Textmodells ist für die Darstellung von Text und die Aktivierung seiner Bearbeitung verantwortlich. Das Textmodell-Subsystem <xref:Microsoft.VisualStudio.Text.ITextBuffer> enthält die Schnittstelle, die die Reihenfolge der Zeichen beschreibt, die vom Editor angezeigt werden soll. Dieser Text kann auf vielfältige Weise geändert, nachverfolgt und anderweitig bearbeitet werden. Das Textmodell enthält auch Typen für die folgenden Aspekte:

- Ein Dienst, der Text mit Dateien verknüpft und das Lesen und Schreiben im Dateisystem verwaltet.

- Ein unterschiedlicher Dienst, der die minimalen Unterschiede zwischen zwei Sequenzen von Objekten ermittelt.

- Ein System zur Beschreibung des Textes in einem Puffer in Bezug auf Teilmengen des Textes in anderen Puffern.

Das Textmodell-Subsystem ist frei von Benutzeroberflächenkonzepten. Sie ist z. B. nicht für die Textformatierung oder das Textlayout verantwortlich und kennt keine visuellen Verzierungen, die dem Text zugeordnet sein können.

Die öffentlichen Typen des Textmodellsubsystems sind in *Microsoft.VisualStudio.Text.Data.dll* und *Microsoft.VisualStudio.CoreUtility.dll*enthalten, die nur von der .NET Framework-Basisklassenbibliothek und dem Managed Extensibility Framework (MEF) abhängen.

### <a name="text-view-subsystem"></a>Textansichtssubsystem

Das Teilsystem der Textansicht ist für das Formatieren und Anzeigen von Text zuständig. Die Typen in diesem Subsystem sind in zwei Ebenen unterteilt, je nachdem, ob die Typen auf Windows Presentation Foundation (WPF) basieren. Die wichtigsten Typen <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>sind und , die den Satz der anzuzeigenden Textzeilen steuern, sowie die Einstellte, die Auswahl und die Funktionen zum Adornen des Textes mithilfe von WPF-UI-Elementen. Dieses Subsystem bietet auch Ränder um den Textanzeigebereich. Diese Ränder können erweitert werden und können verschiedene Arten von Inhalten und visuellen Effekten enthalten. Beispiele für Ränder sind Liniennummernanzeigen und Bildlaufleisten.

Die öffentlichen Typen des Textansichtssubsystems sind in *Microsoft.VisualStudio.Text.UI.dll* und *Microsoft.VisualStudio.Text.UI.Wpf.dll*enthalten. Die erste Baugruppe enthält die plattformunabhängigen Elemente und die zweite die WPF-spezifischen Elemente.

### <a name="classification-subsystem"></a>Klassifikationssubsystem

Das Klassifizierungssubsystem ist für die Bestimmung der Schriftarteigenschaften für Text verantwortlich. Ein Klassifier unterbricht den Text in verschiedene Klassen, z. B. "Keyword" oder "comment". Die Klassifizierungsformatzuordnung verknüpft diese Klassen mit tatsächlichen Schriftarteneigenschaften, z. B. "Blue Consolas 10 pt". Diese Informationen werden von der Textansicht verwendet, wenn text formatiert und gerendert wird. Das Tagging, das weiter unten in diesem Thema ausführlicher beschrieben wird, ermöglicht die Zuordnung von Daten zu Textspannen.

Die öffentlichen Typen des Klassifizierungssubsystems sind in Microsoft.VisualStudio.Text.Logic.dll enthalten und interagieren mit den visuellen Aspekten der Klassifizierung, die in Microsoft.VisualStudio.Text.UI.Wpf.dll enthalten sind.

### <a name="operations-subsystem"></a>Betriebssubsystem

Das Operations-Subsystem definiert das Editorverhalten. Es stellt die Implementierung für Visual Studio-Editorbefehle und das Rückgängig-System bereit.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Ein genauerer Blick auf das Textmodell und die Textansicht

### <a name="the-text-model"></a>Das Textmodell

Das Textmodell-Subsystem besteht aus verschiedenen Gruppierungen von Texttypen. Dazu gehören der Textpuffer, Textmomentaufnahmen und Textspannen.

#### <a name="text-buffers-and-text-snapshots"></a>Textpuffer und Textmomentaufnahmen

Die <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle stellt eine Sequenz von Unicode-Zeichen dar, die mithilfe von UTF-16 codiert werden, d. h. der Codierung, die `String` vom Typ in .NET Framework verwendet wird. Ein Textpuffer kann als Dateisystemdokument beibehalten werden, dies ist jedoch nicht erforderlich.

Der <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> wird verwendet, um einen leeren Textpuffer oder einen Textpuffer <xref:System.IO.TextReader>zu erstellen, der aus einer Zeichenfolge oder aus initialisiert wird. Der Textpuffer kann im Dateisystem als <xref:Microsoft.VisualStudio.Text.ITextDocument>beibehalten werden.

Jeder Thread kann den Textpuffer bearbeiten, bis ein <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>Thread den Besitz des Textpuffers übernimmt, indem er aufruft. Danach kann nur noch dieser Thread Bearbeitungen durchführen.

Ein Textpuffer kann während seiner Lebensdauer viele Versionen durchlaufen. Jedes Mal, wenn der Puffer bearbeitet wird, wird <xref:Microsoft.VisualStudio.Text.ITextSnapshot> eine neue Version generiert, und ein Unveränderliches stellt den Inhalt dieser Version des Puffers dar. Da Textmomentaufnahmen unveränderlich sind, können Sie ohne Einschränkungen auf einen Textmomentaufnahme in jedem Thread zugreifen, auch wenn sich der dargestellte Textpuffer weiterhin ändert.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Text-Snapshots und Text-Snapshot-Zeilen

Sie können den Inhalt einer Textmomentaufnahme als eine Folge von Zeichen oder als eine Folge von Zeilen anzeigen. Zeichen und Linien werden beide ab Null indiziert. Ein leerer Textmomentaufnahme enthält null Zeichen und eine leere Zeile. Eine Zeile wird durch eine gültige Unicode-Zeilenumbruchzeichenfolge oder durch den Anfang oder das Ende des Puffers begrenzt. Zeilenumbruchzeichen werden im Textmomentaufnahme explizit dargestellt, und die Zeilenumbrüche in einem Textmomentaufnahme müssen nicht alle gleich sein.

> [!NOTE]
> Weitere Informationen zu Zeilenumbruchzeichen im Visual Studio-Editor finden Sie unter [Codierungen und Zeilenumbrüche](../ide/encodings-and-line-breaks.md).

Eine Textzeile wird durch <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> ein Objekt dargestellt, das aus einer Textmomentaufnahme für eine bestimmte Zeilennummer oder für eine bestimmte Zeichenposition abgerufen werden kann.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans und NormalizedSnapshotSpanCollections

A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> stellt eine Zeichenposition in einer Momentaufnahme dar. Die Position liegt garantiert zwischen Null und der Länge des Snapshots. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> stellt eine Textspanne in einer Momentaufnahme dar. Seine Endposition liegt garantiert zwischen Null und der Länge des Snapshots. Der <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> besteht aus <xref:Microsoft.VisualStudio.Text.SnapshotSpan> einer Gruppe von Objekten aus demselben Snapshot.

#### <a name="spans-and-normalizedspancollections"></a>Spans und NormalizedSpanCollections

A <xref:Microsoft.VisualStudio.Text.Span> stellt ein Intervall dar, das auf eine Textspanne in einer Textmomentaufnahme angewendet werden kann. Snapshot-Positionen sind nullbasiert, sodass Spannen an jeder Position beginnen können, einschließlich Null. Die `End` Eigenschaft einer Spanne entspricht der Summe `Start` ihrer `Length` Eigenschaft und ihrer Eigenschaft. A `Span` enthält nicht das Zeichen, das `End` von der Eigenschaft indiziert wird. Beispielsweise hat eine Spanne mit Start=5 und Length=3 End=8 und enthält die Zeichen an den Positionen 5, 6 und 7. Die Notation für diesen Zeitraum ist [5..8).

Zwei Spannen schneiden sich, wenn sie irgendwelche Positionen gemeinsam haben, einschließlich der Endposition. Daher ist der Schnittpunkt von [3, 5) und [2, 7) [3, 5) und der Schnittpunkt von [3, 5) und [5, 7) [5, 5). (Beachten Sie, dass [5, 5) eine leere Spanne ist.)

Zwei Spannen überlappen sich, wenn sie gemeinsame Positionen haben, mit Ausnahme der Endposition. Eine leere Spanne überlappt nie eine andere Spanne, und die Überlappung von zwei Spannen ist nie leer.

A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> ist eine Liste von Spannen in der Reihenfolge der Starteigenschaften der Spannen. In der Liste werden überlappende oder angrenzende Spannen zusammengeführt. Wenn man z. B. die Spanne [5..9), [0..1), [3..6) und [9..10) enthält, lautet die normalisierte Liste der Spannen [0..1), [3..10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit-, TextVersion- und Textänderungsbenachrichtigungen

Der Inhalt eines Textpuffers kann <xref:Microsoft.VisualStudio.Text.ITextEdit> mithilfe eines Objekts geändert werden. Durch Erstellen eines solchen Objekts `CreateEdit()` (mit einer der Methoden von <xref:Microsoft.VisualStudio.Text.ITextBuffer>) wird eine Texttransaktion gestartet, die aus Textbearbeitungen besteht. Jede Bearbeitung ist ein Ersetzen einer Textspanne im Puffer durch eine Zeichenfolge. Die Koordinaten und der Inhalt jeder Bearbeitung werden relativ zum Snapshot des Puffers ausgedrückt, als die Transaktion gestartet wurde. Das <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt passt die Koordinaten von Bearbeitungen an, die von anderen Bearbeitungen in derselben Transaktion betroffen sind.

Betrachten Sie beispielsweise einen Textpuffer, der diese Zeichenfolge enthält:

```
abcdefghij
```

Wenden Sie eine Transaktion an, die zwei Änderungen enthält, eine Bearbeitung, die `X` die Spanne bei [2..4) durch das Zeichen ersetzt, und eine zweite Bearbeitung, die die Spanne bei [6..9) durch das Zeichen `Y`ersetzt. Das Ergebnis ist dieser Puffer:

```
abXefYj
```

Die Koordinaten für die zweite Bearbeitung wurden in Bezug auf den Inhalt des Puffers zu Beginn der Transaktion berechnet, bevor die erste Bearbeitung angewendet wurde.

Die Änderungen am Puffer werden <xref:Microsoft.VisualStudio.Text.ITextEdit> wirksam, wenn `Apply()` das Objekt durch Aufrufen seiner Methode festgeschrieben wird. Wenn mindestens eine nicht leere Bearbeitung vorhanden <xref:Microsoft.VisualStudio.Text.ITextVersion> war, wird <xref:Microsoft.VisualStudio.Text.ITextSnapshot> eine neue `Changed` erstellt, ein neues erstellt und ein Ereignis ausgelöst. Jede Textversion hat einen anderen Text-Snapshot. Ein Textmomentaufnahme stellt den vollständigen Status des Textpuffers nach einer Bearbeitungstransaktion dar, aber eine Textversion beschreibt nur die Änderungen von einem Snapshot zum nächsten. Im Allgemeinen sollen Textmomentaufnahmen einmal verwendet und dann verworfen werden, während Textversionen für einige Zeit am Leben bleiben müssen.

Eine Textversion <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>enthält eine . Diese Auflistung beschreibt die Änderungen, die beim Anwenden auf den Snapshot den nachfolgenden Snapshot erzeugen. Jede <xref:Microsoft.VisualStudio.Text.ITextChange> in der Auflistung enthält die Zeichenposition der Änderung, die ersetzte Zeichenfolge und die Ersatzzeichenfolge. Die ersetzte Zeichenfolge ist für eine grundlegende Einfügung leer, und die Ersatzzeichenfolge ist für einen einfachen Löschvorgang leer. Die normalisierte Auflistung `null` ist immer für die neueste Version des Textpuffers.

Es <xref:Microsoft.VisualStudio.Text.ITextEdit> kann immer nur ein Objekt für einen Textpuffer instanziiert werden, und alle Textbearbeitungen müssen für den Thread durchgeführt werden, der den Textpuffer besitzt (falls der Besitz beansprucht wurde). Eine Textbearbeitung kann durch Aufrufen `Cancel` der `Dispose` Methode oder der Methode abgebrochen werden.

<xref:Microsoft.VisualStudio.Text.ITextBuffer>bietet `Insert()`auch `Delete()`, `Replace()` und Methoden, die <xref:Microsoft.VisualStudio.Text.ITextEdit> denen auf der Schnittstelle ähneln. Das Aufrufen dieser Aufrufe hat <xref:Microsoft.VisualStudio.Text.ITextEdit> den gleichen Effekt wie das Erstellen eines Objekts, das Ausführen eines ähnlichen Aufrufs und das anwenden der Bearbeitung.

#### <a name="tracking-points-and-tracking-spans"></a>Tracking-Punkte und Tracking-Spannen

Ein <xref:Microsoft.VisualStudio.Text.ITrackingPoint> stellt eine Zeichenposition in einem Textpuffer dar. Wenn der Puffer so bearbeitet wird, dass sich die Position des Zeichens verschiebt, verschiebt sich der Tracking-Punkt mit ihm. Wenn sich z. B. ein Tracking-Punkt auf Position 10 in einem Puffer bezieht und fünf Zeichen am Anfang des Puffers eingefügt werden, bezieht sich der Tracking-Punkt auf Position 15. Wenn eine Einfügung genau an der Position erfolgt, die <xref:Microsoft.VisualStudio.Text.PointTrackingMode>durch den Tracking-Punkt bezeichnet wird, wird ihr Verhalten durch die , die entweder `Positive` oder `Negative`sein kann, bestimmt. Wenn der Nachverfolgungsmodus positiv ist, bezieht sich der Tracking-Punkt auf dasselbe Zeichen, das sich jetzt am Ende der Einfügung befindet. Wenn der Nachverfolgungsmodus negativ ist, bezieht sich der Tracking-Punkt auf das zuerst eingefügte Zeichen an der ursprünglichen Position. Wenn das Zeichen an der Position, die durch einen Tracking-Punkt dargestellt wird, gelöscht wird, verschiebt sich der Tracking-Punkt in das erste Zeichen, das dem gelöschten Bereich folgt. Wenn sich z. B. ein Tracking-Punkt auf das Zeichen an Position 5 bezieht und die Zeichen an den Positionen 3 bis 6 gelöscht werden, bezieht sich der Tracking-Punkt auf das Zeichen an Position 3.

An <xref:Microsoft.VisualStudio.Text.ITrackingSpan> stellt einen Bereich von Zeichen anstelle nur einer Position dar. Sein Verhalten wird <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>durch seine bestimmt. Wenn der Span-Tracking-Modus [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive)ist, wird die Nachverfolgungsspanne vergrößert, um Text zu integrieren, der an seinen Rändern eingefügt wird. Wenn der Span-Tracking-Modus [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)ist, enthält die Nachverfolgungsspanne keinen Text, der an seinen Rändern eingefügt wird. Wenn der Span-Tracking-Modus jedoch [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive)ist, schiebt eine Einfügung die aktuelle Position in Richtung des Starts, und wenn der Span-Tracking-Modus [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)ist, schiebt eine Einfügung die aktuelle Position zum Ende.

Sie können die Position eines Tracking-Punkts oder die Spanne einer Nachverfolgungsspanne für jede Momentaufnahme des Textpuffers abrufen, zu dem sie gehören. Tracking-Punkte und Tracking-Spannen können sicher von jedem Thread referenziert werden.

#### <a name="content-types"></a>Inhaltstypen

Inhaltstypen sind ein Mechanismus zum Definieren verschiedener Inhaltstypen. Ein Inhaltstyp kann ein Dateityp wie "text", "code" oder "binary" oder ein Technologietyp wie "xml", "vb" oder "c" sein. Das Wort "using" ist z. B. ein Schlüsselwort in C- und Visual Basic, jedoch nicht in anderen Programmiersprachen. Daher wäre die Definition dieses Schlüsselworts auf die Inhaltstypen "c" und "vb" beschränkt.

Inhaltstypen werden als Filter für Verzierungen und andere Elemente des Editors verwendet. Viele Editor-Features und Erweiterungspunkte werden pro Inhaltstyp definiert. Beispielsweise unterscheidet sich die Textfärbung für Nur-Text-Dateien, XML-Dateien und Visual Basic-Quellcodedateien. Textpuffern wird beim Erstellen im Allgemeinen ein Inhaltstyp zugewiesen, und der Inhaltstyp eines Textpuffers kann geändert werden.

Inhaltstypen können von anderen Inhaltstypen mehrfach erben. Mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> der können Sie mehrere Basistypen als Elementangeben eines bestimmten Inhaltstyps angeben.

Entwickler können ihre eigenen Inhaltstypen definieren <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>und diese mithilfe der registrieren. Viele Editorfunktionen können in Bezug auf einen bestimmten <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>Inhaltstyp mithilfe der definiert werden. Beispielsweise können Editorränder, Verzierungen und Maushandler so definiert werden, dass sie nur für Editoren gelten, die bestimmte Inhaltstypen anzeigen.

### <a name="the-text-view"></a>Die Textansicht

Der Ansichtsteil des MVC-Musters (Model View Controller) definiert die Textansicht, die Formatierung der Ansicht, grafische Elemente wie die Bildlaufleiste und die Einfügeleiste. Alle Präsentationselemente des Visual Studio-Editors basieren auf WPF.

#### <a name="text-views"></a>Textansichten

Die <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Schnittstelle ist eine plattformunabhängige Darstellung einer Textansicht. Es wird in erster Linie verwendet, um Textdokumente in einem Fenster anzuzeigen, kann aber auch für andere Zwecke verwendet werden, z. B. in einer QuickInfo.

Die Textansicht verweist auf verschiedene Arten von Textpuffern. Die <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> Eigenschaft bezieht <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> sich auf ein Objekt, das auf diese drei verschiedenen Textpuffer verweist: den Datenpuffer, der der Puffer auf oberster Datenebene ist, den Bearbeitungspuffer, in dem die Bearbeitung stattfindet, und den visuellen Puffer, der der Puffer ist, der in der Textansicht angezeigt wird.

Der Text wird basierend auf den Klassifikatoren formatiert, die dem zugrunde liegenden Textpuffer zugeordnet sind, und wird mithilfe der Verzierungsanbieter geschmückt, die der Textansicht selbst zugeordnet sind.

#### <a name="the-text-view-coordinate-system"></a>Das Textansichtskoordinatensystem

Das Textansichtskoordinatensystem gibt Positionen in der Textansicht an. In diesem Koordinatensystem entspricht der x-Wert 0,0 dem linken Rand des angezeigten Textes, und der y-Wert 0,0 entspricht dem oberen Rand des angezeigten Textes. Die x-Koordinate wird von links nach rechts und die y-Koordinate von oben nach unten erhöht.

Ein Ansichtsfenster (der Teil des Textes, der im Textfenster sichtbar ist) kann nicht horizontal auf die gleiche Weise gescrollt werden, wie es vertikal gescrollt wird. Ein Ansichtsfenster wird horizontal gescrollt, indem seine linke Koordinate so geändert wird, dass es sich in Bezug auf die Zeichnungsfläche bewegt. Ein Ansichtsfenster kann jedoch nur vertikal gescrollt werden, indem <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> der gerenderte Text geändert wird, wodurch ein Ereignis ausgelöst wird.

Die Entfernungen im Koordinatensystem entsprechen logischen Pixeln. Wenn die Text-Rendering-Oberfläche ohne Skalierungstransformation angezeigt wird, entspricht eine Einheit im Textrendering-Koordinatensystem einem Pixel auf dem Display.

#### <a name="margins"></a>Ränder

Die <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> Schnittstelle stellt einen Rand dar und ermöglicht die Kontrolle der Sichtbarkeit des Rands und seiner Größe. Es gibt vier vordefinierte Ränder, die "Oben", "Links", "Rechts" und "Unten" heißen und am oberen, unteren, linken oder rechten Rand einer Ansicht befestigt sind. Bei diesen Rändern handelt es sich um Container, in denen andere Ränder platziert werden können. Die Schnittstelle definiert Methoden, die die Größe des Rands und die Sichtbarkeit eines Rands zurückgeben. Ränder sind visuelle Elemente, die zusätzliche Informationen über die Textansicht bereitstellen, der sie zugeordnet sind. Der Zeilennummernrand zeigt z. B. Zeilennummern für die Textansicht an. Der Glyphenrand zeigt UI-Elemente an.

Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Schnittstelle übernimmt die Erstellung und Platzierung von Rändern. Margen können in Bezug auf andere Margen bestellt werden. Ränder mit höherer Priorität befinden sich näher an der Textansicht. Wenn z. B. zwei linke Ränder, Rand A und Rand B, und Marge B eine niedrigere Priorität als Rand A haben, erscheint Rand B links von Rand A.

#### <a name="the-text-view-host"></a>Der Textansichtshost

Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Benutzeroberfläche enthält die Textansicht und alle angrenzenden Dekorationen, die die Ansicht begleiten, z. B. Bildlaufleisten. Der Textansichtshost enthält auch Ränder, die an einen Rahmen der Ansicht angefügt sind.

#### <a name="formatted-text"></a>Formatierter Text

Der Text, der in einer Textansicht angezeigt wird, besteht aus <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Objekten. Jede Textansichtszeile entspricht einer Textzeile in der Textansicht. Lange Linien im zugrunde liegenden Textpuffer können entweder teilweise verdeckt (wenn der Wortumbruch nicht aktiviert ist) oder in mehrere Textansichtszeilen aufgeteilt werden. Die <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Schnittstelle enthält Methoden und Eigenschaften zum Zuordnen zwischen Koordinaten und Zeichen sowie für die Verzierungen, die der Zeile zugeordnet werden können.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>Objekte werden über <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> eine Schnittstelle erstellt. Wenn Sie sich nur Umsorgen über den Text machen, der derzeit in der Ansicht angezeigt wird, können Sie die Formatierungsquelle ignorieren. Wenn Sie an dem Textformat interessiert sind, das nicht in der Ansicht angezeigt wird (z. <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> B. zur Unterstützung eines Rich-Text-Ausschneidens und Einfügens), können Sie Text in einem Textpuffer formatieren.

Die Textansicht <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> formatiert nacheinander.

## <a name="editor-features"></a>Editor-Funktionen

Die Funktionen des Editors sind so konzipiert, dass die Definition des Features von seiner Implementierung getrennt ist. Der Editor enthält folgende Funktionen:

- Tags und Klassifikatoren

- Verzierungen

- Projection

- Gliedern

- Maus- und Tastenbindungen

- Operationen und Primitive

- IntelliSense

### <a name="tags-and-classifiers"></a>Tags und Klassifikatoren

Tags sind Markierungen, die einer Textspanne zugeordnet sind. Sie können auf unterschiedliche Weise dargestellt werden, z. B. mithilfe von Textfarben, Unterstreichungen, Grafiken oder Pop-ups. Klassifikatoren sind eine Art von Tag.

Andere Arten von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> Tags sind <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> für die <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> Texthervorhebung, für die Gliederung und für Kompilierungsfehler.

#### <a name="classification-types"></a>Klassifizierungstypen

Eine <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Schnittstelle stellt eine Äquivalenzklasse dar, bei der es sich um eine abstrakte Textkategorie handelt. Klassifizierungstypen können von anderen Klassifizierungstypen mehrfach erben. Programmiersprachenklassifizierungen können z. B. "Keyword", "comment" und "identifier" enthalten, die alle von "code" erben. Natürliche Sprachklassifizierungstypen können "Noun", "Verb" und "Adjektiv" umfassen, die alle von "natürlicher Sprache" erben.

#### <a name="classifications"></a>Klassifizierungen

Eine Klassifizierung ist eine Instanz eines bestimmten Klassifizierungstyps, in der Regel über einen Textspannen. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> wird verwendet, um eine Klassifizierung darzustellen. Eine Klassifizierungsspanne kann als Beschriftung betrachtet werden, die eine bestimmte Textspanne abdeckt und dem System mitteilt, dass diese Textspanne von einem bestimmten Klassifizierungstyp ist.

#### <a name="classifiers"></a>Klassifizierungen

Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Mechanismus, der Text in eine Reihe von Klassifizierungen aufteilt. Klassifikatoren müssen für bestimmte Inhaltstypen definiert und für bestimmte Textpuffer instanziiert werden. Clients müssen <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> implementiert werden, um an der Textklassifizierung teilzunehmen.

#### <a name="classifier-aggregators"></a>Klassifigator-Aggregatoren

Ein Klassifikatoraggregator ist ein Mechanismus, der alle Klassifikatoren für einen Textpuffer in nur einem Satz von Klassifizierungen kombiniert. Beispielsweise können sowohl ein C-Klassifikum als auch ein englischsprachiger Klassifikierer Klassifizierungen über einen Kommentar in einer C-Datei erstellen. Betrachten Sie diesen Kommentar:

```
// This method produces a classifier
```

Ein C-Klassifikum kann die gesamte Spanne als Kommentar beschriften, und der englische Sprachklassifikum klassifiziert "produces" möglicherweise als "verb" und "method" als "Noun". Der Aggregator erstellt eine Reihe von nicht überlappenden Klassifizierungen, und der Typ des Satzes basiert auf allen Beiträgen.

Ein Klassifieraggregator ist auch ein Klassifier, da er Text in eine Reihe von Klassifizierungen aufteilt. Der Klassifieraggregator stellt außerdem sicher, dass es keine überlappenden Klassifizierungen gibt und dass die Klassifizierungen sortiert werden. Für einzelne Klassifikatoren steht es frei, beliebige Klassifizierungen in beliebiger Reihenfolge zurückzugeben und sich in irgendeiner Weise zu überlappen.

#### <a name="classification-formatting-and-text-coloring"></a>Klassifizierungsformatierung und Textfärbung

Die Textformatierung ist ein Beispiel für ein Feature, das auf der Textklassifizierung basiert. Sie wird von der Textansichtsebene verwendet, um die Anzeige von Text in einer Anwendung zu bestimmen. Der Textformatierungsbereich hängt von WPF ab, die logische Definition von Klassifizierungen jedoch nicht.

Ein Klassifizierungsformat ist ein Satz von Formatierungseigenschaften für einen bestimmten Klassifizierungstyp. Diese Formate erben vom Format des übergeordneten Typs des Klassifizierungstyps.

Eine <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> ist eine Zuordnung von einem Klassifizierungstyp zu einem Satz von Textformatierungseigenschaften. Die Implementierung der Formatzuordnung im Editor behandelt alle Exporte von Klassifizierungsformaten.

### <a name="adornments"></a>Verzierungen

Verzierungen sind Grafikeffekte, die nicht direkt mit der Schriftart und Farbe der Zeichen in der Textansicht zusammenhängen. Beispielsweise ist die rote Squiggle-Unterstreichung, die zum Markieren von nicht kompilierendem Code in vielen Programmiersprachen verwendet wird, eine eingebettete Verzierung, und QuickInfos sind Popup-Verzierungen. Verzierungen werden <xref:System.Windows.UIElement> von <xref:Microsoft.VisualStudio.Text.Tagging.ITag>abgeleitet und implementiert . Zwei spezielle Arten von Verzierungs-Tags sind die <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>für Verzierungen, die <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>den gleichen Platz wie der Text in einer Ansicht einnehmen, und die für die Squiggle-Unterstreichung.

Eingebettete Verzierungen sind Grafiken, die Teil der formatierten Textansicht sind. Sie sind in verschiedenen Z-Order-Schichten organisiert. Es gibt drei integrierte Ebenen, wie folgt: Text, die Einsiedewart und die Auswahl. Entwickler können jedoch mehr Layer definieren und in Ordnung bringen. Die drei Arten eingebetteter Verzierungen sind textrelative Verzierungen (die sich verschieben, wenn der Text verschoben wird, und werden gelöscht, wenn der Text gelöscht wird), ansichtsrelative Verzierungen (die mit Nicht-Text-Teilen der Ansicht zu tun haben) und besitzergesteuerte Verzierungen (der Entwickler muss seine Platzierung verwalten).

Popup-Verzierungen sind Grafiken, die in einem kleinen Fenster über der Textansicht angezeigt werden, z. B. QuickInfos.

### <a name="projection"></a><a name="projection"></a>Projektion

Projektion ist eine Technik zum Erstellen einer anderen Art von Textpuffer, die eigentlich keinen Text speichert, sondern Text aus anderen Textpuffern kombiniert. Beispielsweise kann ein Projektionspuffer verwendet werden, um den Text aus zwei anderen Puffern zu verketten und das Ergebnis so darzustellen, als ob es sich in nur einem Puffer befindet, oder um Teile des Textes in einem Puffer auszublenden. Ein Projektionspuffer kann als Quellpuffer für einen anderen Projektionspuffer fungieren. Eine Gruppe von Puffern, die durch Projektion miteinander verknüpft sind, kann erstellt werden, um Text auf viele verschiedene Arten neu anzuordnen. (Ein solcher Satz wird auch als *Pufferdiagramm*bezeichnet.) Das Visual Studio-Textumriss-Feature wird mithilfe eines Projektionspuffers implementiert, um den reduzierten Text auszublenden, und der Visual Studio-Editor für ASP.NET Seiten verwendet Projektion, um eingebettete Sprachen wie Visual Basic und C zu unterstützen.

Eine <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> wird mithilfe <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>von erstellt. Ein Projektionspuffer wird durch <xref:Microsoft.VisualStudio.Text.ITrackingSpan> eine geordnete Sequenz von Objekten dargestellt, die als *Quellspannen*bezeichnet werden. Der Inhalt dieser Spannen wird als eine Folge von Zeichen dargestellt. Die Textpuffer, aus denen die Quellspannen gezogen werden, werden als *Quellpuffer*bezeichnet. Clients eines Projektionspuffers müssen sich nicht bewusst sein, dass er sich von einem normalen Textpuffer unterscheidet.

Der Projektionspuffer überwacht Textänderungsereignisse in den Quellpuffern. Wenn sich der Text in einer Quellspanne ändert, ordnet der Projektionspuffer die geänderten Textkoordinaten ihren eigenen Koordinaten zu und löst entsprechende Textänderungsereignisse aus. Betrachten Sie beispielsweise die Quellpuffer A und B mit folgenden Inhalten:

```
A: ABCDE
B: vwxyz
```

Wenn Projektionspuffer P aus zwei Textspannen gebildet wird, einer mit Puffer A und der andere mit puffer B, dann hat P den folgenden Inhalt:

```
P: ABCDEvwxyz
```

Wenn die `xy` Teilzeichenfolge aus Puffer B gelöscht wird, löst Puffer P ein Ereignis aus, das angibt, dass die Zeichen an den Positionen 7 und 8 gelöscht wurden.

Der Projektionspuffer kann auch direkt bearbeitet werden. Es gibt Änderungen an die entsprechenden Quellpuffer weiter. Wenn z. B. eine Zeichenfolge an Position 6 (die ursprüngliche Position des Zeichens "v") in Puffer P eingefügt wird, wird die Einfügung an Puffer B an Position 1 weitergegeben.

Es gibt Einschränkungen für die Quellspannen, die zu einem Projektionspuffer beitragen. Quellspannen dürfen sich nicht überlappen; Eine Position in einem Projektionspuffer kann nicht einer Position in einem Quellpuffer zugeordnet werden, und eine Position in einem Quellpuffer kann nicht mehr als einer Position in einem Projektionspuffer zugeordnet werden. In der Quellpufferbeziehung sind keine Zirkeinheiten zulässig.

Ereignisse werden ausgelöst, wenn sich der Satz von Quellpuffern für einen Projektionspuffer ändert und sich der Satz von Quellspannen ändert.
Ein Elisionspuffer ist eine spezielle Art von Projektionspuffer. Es wird hauptsächlich für die Gliederung und für Operationen verwendet, die Textblöcke erweitern und reduzieren. Ein Elisionspuffer basiert auf nur einem Quellpuffer, und die Spannen im Elisionspuffer müssen so angeordnet werden, wie sie im Quellpuffer angeordnet sind.

#### <a name="the-buffer-graph"></a>Das Pufferdiagramm

Die <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Schnittstelle ermöglicht die Zuordnung über ein Diagramm von Projektionspuffern. Alle Textpuffer und Projektionspuffer werden in einem gerichteten azyklischen Diagramm gesammelt, ähnlich wie der abstrakte Syntaxbaum, der von einem Sprachcompiler erstellt wird. Das Diagramm wird durch den oberen Puffer definiert, der ein beliebiger Textpuffer sein kann. Das Pufferdiagramm kann von einem Punkt im oberen Puffer zu einem Punkt in einem Quellpuffer oder von einer Spanne im oberen Puffer zu einer Reihe von Spannen in einem Quellpuffer zugeordnet werden. Auf ähnliche Weise kann ein Punkt oder eine Spanne von einem Quellpuffer zu einem Punkt im oberen Puffer zugeordnet werden. Pufferdiagramme werden mithilfe <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>der erstellt.

#### <a name="events-and-projection-buffers"></a>Ereignisse und Projektionspuffer

Wenn ein Projektionspuffer geändert wird, werden die Änderungen vom Projektionspuffer an die Puffer gesendet, die davon abhängen. Nachdem alle Puffer geändert wurden, werden Pufferänderungsereignisse ausgelöst, beginnend mit dem tiefsten Puffer.

### <a name="outlining"></a>Gliedern

Die Gliederung ist die Möglichkeit, verschiedene Textblöcke in einer Textansicht zu erweitern oder zu reduzieren. Die Gliederung wird <xref:Microsoft.VisualStudio.Text.Tagging.ITag>als eine Art von definiert, in der gleichen Weise wie Verzierungen definiert werden. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ist ein Tag, der einen Textbereich definiert, der erweitert oder reduziert werden kann. Um die Gliederung zu <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> verwenden, <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>müssen Sie die importieren, um eine zu erhalten. Der Umriss-Manager zählt die verschiedenen Blöcke auf, reduziert und erweitert <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> sie, die als Objekte dargestellt werden, und löst Ereignisse entsprechend aus.

### <a name="mouse-bindings"></a>Mausbindungen

Mausbindungen verknüpfen Mausbewegungen mit verschiedenen Befehlen. Mausbindungen werden mithilfe einer <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>definiert, und Schlüsselbindungen werden <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>mithilfe einer definiert. Der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> instanziiert automatisch alle Bindungen und verbindet sie mit Mausereignissen in der Ansicht.

Die <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> Schnittstelle enthält Vor- und Nachprozessereignishandler für verschiedene Mausereignisse. Um eines der Ereignisse zu behandeln, können Sie <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>einige der Methoden in überschreiben.

### <a name="editor-operations"></a>Editor-Operationen

Editor-Operationen können verwendet werden, um die Interaktion mit dem Editor zu automatisieren, für Skripting oder andere Zwecke. Sie können <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> die zu zugriffsvorgänge für eine bestimmte <xref:Microsoft.VisualStudio.Text.Editor.ITextView>importieren. Sie können diese Objekte dann verwenden, um die Auswahl zu ändern, die Ansicht zu scrollen oder die Einserbin in verschiedene Teile der Ansicht zu verschieben.

### <a name="intellisense"></a>IntelliSense

IntelliSense unterstützt die Anweisungsvervollständigung, Signaturhilfe (auch als Parameterinfo bezeichnet), Quick Info und Glühbirnen.

Die Anweisungsvervollständigung stellt Popuplisten mit potenziellen Vervollständigungen für Methodennamen, XML-Elemente und andere Codierungs- oder Markupelemente bereit. Im Allgemeinen ruft eine Benutzergeste eine Abschlusssitzung auf. In der Sitzung wird die Liste der möglichen Abschlüsse angezeigt, und der Benutzer kann eine Liste auswählen oder die Liste schließen. Der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> ist für das <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>Erstellen und Auslösen der verantwortlich. Der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> berechnet <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> die Abschlusselemente für die Sitzung.

## <a name="see-also"></a>Weitere Informationen

- [Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
- [Editor-Importe](../extensibility/editor-imports.md)
