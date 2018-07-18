---
title: In den Editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ace9e405b52873d08c578c2af8e7005249e7d58c
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265774"
---
# <a name="inside-the-editor"></a>Innerhalb des-Editors
Der Editor besteht aus einer Reihe von verschiedenen Subsysteme an, denen der Editor Text Modell separaten Textansicht und die Benutzeroberfläche beibehalten werden.  
  
 Diese Abschnitte beschreiben verschiedene Aspekte des Editors:  
  
-   [Übersicht über die Subsysteme](../extensibility/inside-the-editor.md#overview)  
  
-   [Das Textmodell](../extensibility/inside-the-editor.md#textmodel)  
  
-   [Textansicht](../extensibility/inside-the-editor.md#textview)  
  
 Diese Abschnitte beschreiben die Funktionen des Editors:  
  
-   [RFID-Transponder und Klassifizierer](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [Zusatzelemente](../extensibility/inside-the-editor.md#adornments)  
  
-   [Projektion](../extensibility/inside-the-editor.md#projection)  
  
-   [Gliedern](../extensibility/inside-the-editor.md#outlining)  
  
-   [Maus Bindungen](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [Editor-Vorgänge](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> Übersicht über die Subsysteme  
  
### <a name="text-model-subsystem"></a>Text-Modell-Subsystem  
 Der Text Modell Spoolersubsystem ist zum Darstellen von Text und die Bearbeitung aktivieren. Das Text-Subsystem Modell enthält die <xref:Microsoft.VisualStudio.Text.ITextBuffer> -Schnittstelle, die die Sequenz von Zeichen beschreibt, die vom Editor angezeigt werden soll. Dieser Text kann geändert, nachverfolgt und anderweitige in vielerlei Hinsicht. Der Textmodell bietet auch Typen, für die folgenden Aspekte:  
  
-   Ein Dienst, der Text Dateien zugeordnet, und verwaltet werden, lesen und Schreiben sie im Dateisystem.  
  
-   Eine differenzierende Dienst, der die minimale Unterschiede zwischen zwei Sequenzen von Objekten gefunden werden.  
  
-   Ein System zum Beschreiben des Texts in einem Puffer in Bezug auf Teilmengen des Texts in andere Puffer.  
  
 Das Text-Modell-Subsystem ist kostenlos Benutzer Konzepte, die Benutzeroberfläche (UI). Beispielsweise ist nicht verantwortlich für die textformatierung oder Textlayout, und er hat keine Informationen über visual Zusatzelemente, die den Text zugeordnet werden kann.  
  
 Die öffentlichen Typen des Subsystems Modell Text enthalten sind, in Microsoft.VisualStudio.Text.Data.dll und Microsoft.VisualStudio.CoreUtility.dll, die nur von der .NET Framework-Basisklassenbibliothek und Managed Extensibility Framework (MEF) abhängig sind.  
  
### <a name="text-view-subsystem"></a>Text-Ansicht-Subsystem  
 Der Text anzeigen Spoolersubsystem ist für das Formatieren und Anzeigen von Text. Die Typen in dieses Subsystems werden in zwei Ebenen, je nachdem, ob die Typen in Windows Presentation Foundation (WPF) beruhen aufgeteilt. Die wichtigsten Typen sind <xref:Microsoft.VisualStudio.Text.Editor.ITextView> und <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, die steuern, den Satz von Textzeilen, die angezeigt werden sollen, und auch das Caretzeichen, die Auswahl und die Funktionen zum Erweitern von Text mithilfe von WPF-UI-Elemente. Dieses Subsystems bietet auch Ränder um den Text im Bereich anzuzeigende. Diese Ränder erweitert werden können, und können verschiedene Arten von Inhalt und visuelle Effekte enthalten. Beispiele für Ränder sind Line Number zeigt und Bildlaufleisten.  
  
 Die öffentlichen Typen des Subsystems Text anzeigen, sind in Microsoft.VisualStudio.Text.UI.dll und Microsoft.VisualStudio.Text.UI.Wpf.dll enthalten. Die erste Assembly enthält plattformunabhängige Elemente und die zweite enthält die WPF-spezifische Elemente.  
  
### <a name="classification-subsystem"></a>Klassifizierung-Subsystem  
 Die Klassifizierung Spoolersubsystem ist für die Schriftarteigenschaften für Text bestimmt. Eine Klassifizierung teilt den Text in anderen Klassen, z. B. "Schlüsselwort" oder "Kommentar". Gekachelten Klassifizierung bezieht sich diese Klassen auf tatsächliche Schriftarteigenschaften, z. B. "Blue Consolas 10pt". Diese Informationen werden von der Textansicht verwendet, wenn es formatiert und Text gerendert. Tags, das weiter unten in diesem Thema ausführlicher beschrieben wird, können Daten Textpassagen zugeordnet werden soll.  
  
 Die öffentlichen Typen des Subsystems Klassifizierung in Microsoft.VisualStudio.Text.Logic.dll enthalten sind, und sie interagieren mit der visuellen Aspekte der Klassifizierung, die in Microsoft.VisualStudio.Text.UI.Wpf.dll enthalten sind.  
  
### <a name="operations-subsystem"></a>Vorgänge-Subsystem  
 Das Operations-Subsystem definiert Verhalten-Editors. Er bietet die Implementierung für Visual Studio-Editor-Befehle und die rückgängig-System.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Genauere Betrachtung der Textmodell und Textansicht  
  
###  <a name="textmodel"></a> Das Textmodell  
 Das Subsystem des Text-Modell besteht aus unterschiedliche Gruppierungen der Texttypen. Dazu gehören die Textpuffer, Textmomentaufnahmen und unzusammenhängende.  
  
#### <a name="text-buffers-and-text-snapshots"></a>Text Buffers "und" Textmomentaufnahmen  
 Die <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle darstellt, eine Sequenz von Unicode-Zeichen, die codiert werden, mithilfe von UTF-16, also die Codierung von verwendet die `String` Typ in .NET Framework. Ein Textpuffer als Datei Systemdokument beibehalten werden kann, aber dies ist nicht erforderlich.  
  
 Die <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> dient zum Erstellen von ein leerer Text-Puffer oder einen Textpuffer, die Initialisierung aus einer Zeichenfolge oder von <xref:System.IO.TextReader>. Die Textpuffer beibehalten werden kann, die im Dateisystem als ein <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 Der Textpuffer kann über einen beliebigen Thread bearbeitet werden, bis ein Thread den Besitz des Textpuffers durch den Aufruf nimmt <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Danach kann nur von diesem Thread Bearbeitungen ausführen.  
  
 Ein Textpuffer kann viele Versionen während seiner Lebensdauer durchlaufen. Eine neue Version wird jedes Mal, wenn der Puffer bearbeitet wird, und eine unveränderliche generiert <xref:Microsoft.VisualStudio.Text.ITextSnapshot> den Inhalt dieser Version des Puffers darstellt. Da Textmomentaufnahmen unveränderlich sind, können Sie einen Text-Snapshot auf einen beliebigen Thread, ohne Einschränkungen zugreifen, selbst wenn der Textpuffer, den er darstellt weiterhin ändern.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Textmomentaufnahmen und den Snapshot Textzeilen  
 Sie können den Inhalt einer Momentaufnahme Text als eine Folge von Zeichen oder als eine Sequenz von Zeilen anzeigen. Zeichen und Linien sind, dass beide indiziert, beginnend mit 0 (null). Eine leerer Textmomentaufnahme enthält 0 (null) Zeichen und eine leere Zeile. Eine Linie wird durch eine beliebige gültige Unicode-Line-Break-Zeichen-Sequenz oder vom Anfang oder Ende des Puffers als Trennzeichen. -Zeilenumbruchzeichen werden explizit in der Textmomentaufnahme dargestellt, und die Zeilenumbrüche in einer Textmomentaufnahme müssen nicht alle identisch sein.  
  
> [!NOTE]
>  Weitere Informationen zu Zeilenumbruchzeichen in Visual Studio-Editor, finden Sie unter [Codierungen und Zeilenumbrüche](../ide/encodings-and-line-breaks.md).  
  
 Eine Textzeile wird dargestellt, indem ein <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> -Objekt, das aus einem Textmomentaufnahme für eine bestimmte Zeilennummer oder für einen bestimmten Zeichenposition abgerufen werden kann.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints SnapshotSpans und NormalizedSnapshotSpanCollections  
 Ein <xref:Microsoft.VisualStudio.Text.SnapshotPoint> eine Zeichenposition in eine Momentaufnahme darstellt. Die Position ist garantiert liegen zwischen 0 (null) und die Länge der Momentaufnahme. Ein <xref:Microsoft.VisualStudio.Text.SnapshotSpan> stellt eine Textpassage in einer Momentaufnahme. Wird sichergestellt, dass seine Endposition liegen zwischen 0 (null) und die Länge der Momentaufnahme. Die <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> besteht aus einem Satz von <xref:Microsoft.VisualStudio.Text.SnapshotSpan> Objekte aus der gleichen Momentaufnahme.  
  
#### <a name="spans-and-normalizedspancollections"></a>Bereiche und datenelementausgabe NormalizedSpanCollections  
 Ein <xref:Microsoft.VisualStudio.Text.Span> stellt ein Intervall an, die auf einen Textabschnitt in einem Textmomentaufnahme angewendet werden kann. Momentaufnahme Positionen sind nullbasiert, sodass Spannen an einer beliebigen Position 0 (null) einschließlich beginnen können. Die `End` Eigenschaft eines Textabschnitts ist gleich der Summe von seiner `Start` Eigenschaft und die zugehörige `Length` Eigenschaft. Ein `Span` schließt nicht das Zeichen, die von indiziert ist die `End` Eigenschaft. Z. B. eine Spanne, die Start = 5 und Länge = 3 bietet End = 8, sowie die Zeichen an der Position 5, 6 und 7. Die Notation für diese Spanne ist 5..8).  
  
 Zwei Spannen schneiden besäßen sie alle Positionen gemeinsam, einschließlich der Endposition. Aus diesem Grund die Schnittmenge der [3, 5) und [2, 7) ist [3, 5) sowie die Auswirkungen von [3, 5) und [5, 7) wird [5, 5). (Beachten Sie, dass [5, 5) ist eine leere Spanne.)  
  
 Zwei Spannen überlappen sich, wenn sie Positionen Gemeinsamkeit, mit Ausnahme der Endposition aufweisen. Eine leere Spanne nie überschneidet sich mit jeder anderen Spanne sowie die Überlappung von zwei Spannen ist niemals leer.  
  
 Ein <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> ist eine Liste der in der Reihenfolge der Start-Eigenschaften der Spannen Spannen. In der Liste sind überschneidende oder angrenzende Spannen zusammengeführt. Angenommen, die den Satz von Spannen [5..9), [0..1), [3..6), und [9..10), wird der normalisierte Werteliste Spannen [0..1), [3..10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion und Text-Änderungsbenachrichtigungen  
 Der Inhalt von einem Textpuffer kann geändert werden, mithilfe einer <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt. Erstellen ein solches Objekt (mithilfe eines der `CreateEdit()` Methoden der <xref:Microsoft.VisualStudio.Text.ITextBuffer>) startet eine Transaktion von Text, der Textbearbeitungen besteht. Jede bearbeiten ist ein Ersatz einige Textabschnitts im Puffer durch eine Zeichenfolge. Die Koordinaten und den Inhalt jeder Bearbeitung sind relativ zu der Momentaufnahme des Puffers ausgedrückt, wenn die Transaktion gestartet wurde. Die <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt passt die Koordinaten der Bearbeitungen, die von anderen Änderungen an derselben Transaktion betroffen sind.  
  
 Betrachten Sie beispielsweise einen Textpuffer, der diese Zeichenfolge enthält:  
  
```  
abcdefghij  
```  
  
 Wenden Sie eine Transaktion, enthält zwei Änderungen, die eine bearbeiten, die die Spanne am ersetzt [2..4) mit dem Zeichen `X` und eine zweite bearbeiten, die die Spanne am ersetzt [6..9) mit dem Zeichen `Y`. Das Ergebnis ist dieser Puffer:  
  
```  
abXefYj  
```  
  
 Die Koordinaten für die zweite Bearbeitung berechnet wurden in Bezug auf den Inhalt des Puffers am Anfang der Transaktions vor dem Anwenden der ersten Bearbeitung.  
  
 Die Änderungen in den Puffer wirksam bei der <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt ein Commit wird durch Aufrufen seiner `Apply()` Methode. Wenn es mindestens eine nicht leere bearbeiten wurde, ein neues <xref:Microsoft.VisualStudio.Text.ITextVersion> erstellt wird, ein neues <xref:Microsoft.VisualStudio.Text.ITextSnapshot> erstellt wurde, und eine `Changed` Ereignis wird ausgelöst. Jeder Textversion hat einen anderen Textmomentaufnahme. Eine Textmomentaufnahme den gesamten Status des Textpuffers darstellt, nachdem eine Transaktion zum Bearbeiten, aber eine Textversion beschreibt nur die Änderungen von einer Momentaufnahme zur nächsten. Textmomentaufnahmen werden im Allgemeinen einmal verwendet werden sollen, und dann verworfen, während Text-Versionen für einige Zeit aktiv bleiben müssen.  
  
 Eine Textversion enthält eine <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Diese Auflistung gibt Aufschluss über Änderungen, die bei Anwendung auf die Momentaufnahme die nachfolgenden Momentaufnahme erzeugt. Jede <xref:Microsoft.VisualStudio.Text.ITextChange> in der Auflistung enthält die Zeichenposition, der die Änderung der ersetzten Zeichenfolge und die Ersatzzeichenfolge. Die ersetzte Zeichenfolge für eine grundlegende Einfügung leer ist, und die Ersatzzeichenfolge für das Löschen einer grundlegenden leer ist. Die normalisierte Sammlung ist stets `null` für die neueste Version des Textpuffers.  
  
 Nur ein <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt kann für einen Textpuffer jederzeit instanziiert werden, und alle Textbearbeitungen müssen ausgeführt werden, auf dem Thread, der den Textpuffer besitzt (sofern es sich bei den Besitz in Anspruch genommen wurde). Ein Text bearbeiten kann abgebrochen werden, durch Aufrufen seiner `Cancel` Methode oder den zugehörigen `Dispose` Methode.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> bietet außerdem `Insert()`, `Delete()`, und `Replace()` Methoden, die ähneln finden Sie auf der <xref:Microsoft.VisualStudio.Text.ITextEdit> Schnittstelle. Dieser Aufruf hat dieselbe Wirkung wie das Erstellen einer <xref:Microsoft.VisualStudio.Text.ITextEdit> -Objekt, dem ähnliche Aufruf durchläuft und die Bearbeitung.  
  
#### <a name="tracking-points-and-tracking-spans"></a>Nachverfolgen von Punkten und Nachverfolgen der Spannen  
 Ein <xref:Microsoft.VisualStudio.Text.ITrackingPoint> stellt eine Zeichenposition in einem Textpuffer. Wenn der Puffer auf eine Weise, der die Position des Zeichens bearbeitet wird zu verschiebenden verursacht, wechselt der Verfolgungspunkts mit. Beispielsweise verweist, wenn ein Verfolgungspunkt bezieht sich auf die Position 10 in einem Puffer, und fünf Zeichen am Anfang des Puffers eingefügt werden, Verfolgungspunkts klicken Sie dann auf Position 15. Wenn eine Einfügung genau der Position gekennzeichnet durch Verfolgungspunkts geschieht, richtet sich das Verhalten nach seiner <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, dem kann es sich um `Positive` oder `Negative`. Wenn der Modus zum Nachverfolgen von positiv ist, bezieht sich die Verfolgungspunkts in das gleiche Zeichen, die nun am Ende einfügen ist. Wenn der Modus zum Nachverfolgen von negativ ist, bezieht sich die Verfolgungspunkts auf das erste eingefügten Zeichen an der ursprünglichen Position. Wenn das Zeichen an der Position, die durch ein Verfolgungspunkt dargestellt wird, gelöscht wird, wechselt der Verfolgungspunkts zum ersten Zeichen, das den gelöschten Bereich folgt. Bezieht sich z. B. wenn ein Verfolgungspunkt bezieht sich auf das Zeichen an Position 5 und die Zeichen an der Position 3 bis 6 werden gelöscht, Verfolgungspunkts auf das Zeichen an Position 3.  
  
 Eine <xref:Microsoft.VisualStudio.Text.ITrackingSpan> stellt einen Bereich von Zeichen anstelle von nur einem Position dar. Das Verhalten richtet sich nach seiner <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Wenn der Modus zum Nachverfolgen von Span ist <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, überschreitet die Überwachungsdatenbank Spanne an seinen Rändern; eingefügten Text zu integrieren, wenn der Modus zum Nachverfolgen von Span ist <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, die Spanne für die Überwachung wird nicht an seinen Rändern eingefügten Text eingebunden. Allerdings ist der Modus zum Nachverfolgen von Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, eine Einfügung legt die aktuelle Position bis zum Anfang und, wenn der Modus zum Nachverfolgen von Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, eine Einfügung legt die aktuelle Position am Ende.  
  
 Sie können die Position eines Punkts Überwachung oder die Spanne eines Textabschnitts Überwachung für eine Momentaufnahme des Textpuffers abrufen, die sie angehören. Nachverfolgen von Punkten und Nachverfolgen der Spannen können von jedem Thread sicher verwiesen werden.  
  
#### <a name="content-types"></a>Inhaltstypen  
 Inhaltstypen sind ein Mechanismus zum Definieren von verschiedenen Arten von Inhalten. Ein Inhaltstyp möglich einen Dateityp, z. B. "Text", "Code" oder "binary" oder eine Technologietyp, z. B. "Xml", "Vb" oder "c#". Das Wort "mit" beispielsweise ist ein Schlüsselwort in c# und Visual Basic, jedoch nicht in anderen Programmiersprachen. Daher würde die Definition dieses Schlüsselwort auf den Inhalt vom Typ "c#" oder "Vb" beschränkt.  
  
 Inhaltstypen sind für Zusatzelemente und andere Elemente des Editors als Filter verwendet. Viele Features im Editor und Erweiterungspunkte werden pro Inhaltstyp definiert. beispielsweise unterscheidet sich Text Färbung für nur-Text-Dateien, XML-Dateien und Visual Basic-Quellcodedateien. Textpuffer werden in der Regel einen Inhaltstyp zugewiesen, wenn sie erstellt wurden, und der Inhaltstyp der einen Textpuffer geändert werden kann.  
  
 Inhaltstypen können mehrere-andere Inhaltstypen erben. Die <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> können Sie mehrere Basistypen als den übergeordneten Elementen eines bestimmten Inhaltstyps angeben.  
  
 Entwickler können eigene Inhaltstypen definieren und registrieren Sie sie mithilfe der <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Viele Editorfunktionen können in Bezug auf einen bestimmten Inhaltstyp definiert werden, mithilfe der <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Beispielsweise können Editor Ränder Zusatzelemente und Maushandler definiert werden, damit sie nur für Editoren gelten, in denen bestimmte Inhaltstypen angezeigt.  
  
###  <a name="textview"></a> Textansicht  
 Die Ansichtsteil des Musters Model View Controller (MVC) definiert, der Textansicht, die die Formatierung von der Sicht, die grafische Elemente wie die Bildlaufleiste und die Einfügemarke. Alle Elemente von Visual Studio-Editor basieren auf WPF.  
  
#### <a name="text-views"></a>Text-Ansichten  
 Die <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Schnittstelle ist eine plattformunabhängige Darstellung einer Text-Sicht. Es dient in erster Linie zum Textdokumente in einem Fenster angezeigt, aber es kann auch verwendet werden für andere Zwecke verwenden, z. B. in einer QuickInfo angezeigt.  
  
 Textansicht verweist auf verschiedene Arten von Textpuffer. Die <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> Eigenschaft bezieht sich auf ein <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> -Objekt, das auf diesen drei verschiedene Textpuffer verweist: im Datenpuffer der oberste Datenebene Puffer, in welche bearbeiten auftritt und visuellen Puffer, der den Puffer ist ist, ist der Bearbeiten--Puffer in der Textansicht angezeigt.  
  
 Der Text wird basierend auf der Klassifizierer, die an der zugrunde liegenden Textpuffer angefügt werden formatiert und gestaltet ist, durch die Verwendung der Randsteuerelement-Anbieter, die die Textansicht selbst zugeordnet sind.  
  
#### <a name="the-text-view-coordinate-system"></a>Das Koordinatensystem des Text-Ansicht  
 Das Koordinatensystem des Text-Sicht gibt die Positionen in der Textansicht an. In diesem Koordinatensystem der X-Wert 0,0 entspricht dem linken Rand des angezeigten Texts und der y-Wert 0,0 am oberen Rand des angezeigten Texts entspricht. Die X-Koordinate erhöht von links nach rechts und die y-Koordinate von oben nach unten.  
  
 Ein Viewport (der Teil des Texts im Fenster mit Text sichtbar) kann nicht auf die gleiche Weise ein horizontaler Bildlauf durchgeführt werden, wie sie ein vertikaler Bildlauf durchgeführt wird. Ein Viewport ist horizontaler Bildlauf durchgeführt, ändern Sie die linke Koordinate, damit sie in Bezug auf die Zeichenoberfläche verschoben wird. Allerdings ein Viewport kann Bildlauf durchgeführt werden vertikal nur durch Ändern der gerenderten-Texts, der bewirkt, dass ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Ereignis ausgelöst wurde.  
  
 Entfernungen im Koordinatensystem entsprechen logische Pixel. Wenn die Text-Rendering-Oberfläche ohne eine Skalierungstransformation angezeigt wird, klicken Sie dann entspricht eine Einheit in den Text-Rendering-Koordinatensystem ein Pixel in der Anzeige.  
  
#### <a name="margins"></a>Seitenränder  
 Die <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> Schnittstelle stellt einen Rand und aktiviert die Steuerung der Sichtbarkeit der den Rand und seine Größe. Es gibt vier vordefinierten Ränder, die "Top", "Left", "Right" und "Bottom" heißen und oben, unten, links oder rechten Rand einer Sicht zugeordnet sind. Diese Ränder sind Container, die in denen anderen Rändern platziert werden können. Die Schnittstelle definiert Methoden, die die Größe der Seitenränder und die Sichtbarkeit der einen Rand zurückgeben. Ränder werden visuelle Elemente, die zusätzliche Informationen über die Textansicht bereitstellen, mit denen sie verbunden sind. Beispielsweise zeigt die Nummer der Zeile Rand Zeilennummern für Textansicht. Der Symbolrand Zeigt Elemente der Benutzeroberfläche.  
  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Schnittstelle ist für die Erstellung und Platzierung der Ränder. Ränder können in Bezug auf die anderen Rändern sortiert werden. Höhere Priorität Ränder befinden sich näher anzuzeigende Text. Beispielsweise wird angezeigt, wenn es zwei linken Rand, A und B-Seitenrand gibt und Rand B verfügt über eine niedrigere Priorität als Rand A, Rand B auf der linken Seite des Rands A.  
  
#### <a name="the-text-view-host"></a>Text anzeigen des Hosts  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Schnittstelle enthält die Textansicht und alle angrenzenden Ergänzungen, die die Sicht, z. B. Bildlaufleisten offen. Text anzeigen des Hosts enthält auch die Ränder, die einen Rahmen der Sicht zugeordnet sind.  
  
#### <a name="formatted-text"></a>Formatierter Text  
 In einer Textansicht angezeigte Text besteht aus <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Objekte. Eine Textzeile in der Textansicht entspricht jede Zeile Text anzeigen. Lange Zeilen in der zugrunde liegenden Textpuffer können werden teilweise verdeckt (Wenn kein Zeilenumbruch aktiviert ist) oder in mehrere Textansicht Zeilen aufgeteilt. Die <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Schnittstelle enthält Methoden und Eigenschaften für die Zuordnung zwischen Koordinaten und Zeichen, und für die Zusatzelemente, die der Zeile zugeordnet werden können.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Objekte werden erstellt, mit einer <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> Schnittstelle. Wenn Sie nur den Text besorgt, die derzeit in der Ansicht angezeigt wird sind, können Sie die Quelle die Formatierung ignorieren. Wenn Sie das Format des Texts interessiert sind, die nicht angezeigt, in der Ansicht (z. B. zur Unterstützung von Rich-Text Ausschneiden und Einfügen), können Sie <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> zum Formatieren von Text in einem Textpuffer.  
  
 Textansicht formatiert eine <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> zu einem Zeitpunkt.  
  
## <a name="editor-features"></a>Editor-Funktionen  
 Die Funktionen des Editors sind so gestaltet, dass die Definition der Funktion getrennt von der Implementierung. Der Editor enthält die folgenden Funktionen:  
  
-   RFID-Transponder und Klassifizierer  
  
-   Zusatzelemente  
  
-   Projection  
  
-   Gliedern  
  
-   Maus und Tastatur Bindungen  
  
-   Vorgänge und primitive Typen  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> RFID-Transponder und Klassifizierer  
 Tags sind Marker, die einen Textabschnitt zugeordnet sind. Sie können auf unterschiedliche Weise z. B. dargestellt werden mithilfe von Farben für Text, unterstrichen, Grafiken oder Popups. Klassifizierern handelt es sich um eine Art des Tags.  
  
 Andere Arten von Tags sind <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> für die Hervorhebung von Text <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> für Gliederungen, und <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> für Kompilierungsfehler.  
  
#### <a name="classification-types"></a>Klassifizierungstypen  
 Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Schnittstelle stellt eine äquivalenzklasse, also eine abstrakte Kategorie von Text. Klassifizierungstypen können mehrere-andere Klassifizierungstypen erben. Kann die programming Language Klassifikationen enthalten, "Schlüsselwort", "Comment" und "Bezeichner", die alle von "Code" erben. Natürlicher Sprache Klassifizierung möglicherweise die folgenden Anweisungstypen "Nomen", "Verb" und "Adjektiv", die alle von "natürlicher Sprache" erben.  
  
#### <a name="classifications"></a>Klassifizierungen  
 Eine Klassifizierung ist eine Instanz einer bestimmten Klassifizierung-Typs in der Regel über einen Zeitraum von Text. Ein <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> wird verwendet, um eine Klassifizierung darstellen. Eine Klassifizierung Spanne kann als Bezeichnung betrachtet werden, die einen bestimmten Textabschnitt behandelt und weist das System, das dieser Spanne des Texts einer bestimmten Klassifizierungstyp aufweist.  
  
#### <a name="classifiers"></a>Klassifizierer  
 Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ist ein Mechanismus, die Text in einen Satz von Klassifizierungen zu beeinträchtigen. Klassifizierer für bestimmte Inhaltstypen definiert und instanziiert wird, bestimmten Textpuffer. Clients müssen implementieren <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> an textklassifizierung teilnehmen.  
  
#### <a name="classifier-aggregators"></a>Klassifizierung Aggregatoren  
 Ein Klassifizierungsaggregator ist ein Mechanismus, der alle Klassifizierungen für einen Textpuffer in nur einem Satz von Klassifizierungen kombiniert. Eine C#-Klassifizierung und einen englischen Sprache Klassifizierer konnte Klassifikationen über einen Kommentar in einer C#-Datei erstellen. Betrachten Sie diesen Kommentar aus:  
  
```  
// This method produces a classifier  
```  
  
 Eine C#-Klassifizierung möglicherweise die gesamte Spanne als Kommentar kennzeichnen und die Klassifizierung der englischen Sprache möglicherweise als "Verb" und "Method" als ein "Nomen" klassifizieren "erstellt". Der Aggregator erzeugt einen Satz nicht überschneidender Klassifizierungen, und der Typ der Menge basiert darauf, dass alle Beiträge.  
  
 Ein Klassifizierungsaggregator ist auch eine Klassifizierung aus, da Text in einen Satz von Klassifizierungen beschädigt. Der Klassifizierungsaggregator wird sichergestellt, dass auch, dass es keine überlappenden Klassifikationen sind und Klassifikationen sortiert werden. Einzelne Klassifizierern sind frei, um einen beliebigen Satz von Klassifizierungen, in beliebiger Reihenfolge zurückgegeben und in keiner Weise überlappende.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Klassifizierung Formatierung und Farben für Text  
 Formatieren von Text ist ein Beispiel für eine Funktion, die auf textklassifizierung erstellt wird. Es wird durch die Ansichtsebene Text verwendet, um die Anzeige von Text in einer Anwendung zu bestimmen. Die Formatierung Textbereich ist abhängig von WPF, aber die Definition des logischen Klassifizierungen ist.  
  
 Ein Klassifizierungsformat ist ein Satz von Eigenschaften für einen bestimmten Klassifizierung Formatierung. Diese Formate werden aus dem Format des übergeordneten Elements den Klassifizierungstyp erben.  
  
 Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> ist eine Zuordnung von einem Klassifizierungstyp auf einen Satz von Eigenschaften für die textformatierung. Die Implementierung des gekachelten im Editor behandelt alle Exporte Klassifizierung Formate.  
  
###  <a name="adornments"></a> Zusatzelemente  
 Zusatzelemente sind Graphic Effekte, die nicht direkt auf die Schriftart und Farbe der Zeichen in der Textansicht beziehen. Z. B. die rote Wellenlinie Unterstreichung ab, das nicht Kompilieren von Code in zahlreichen Programmiersprachen markieren ist eine eingebettete Randsteuerelement und QuickInfos werden Popup Zusatzelemente. Zusatzelemente abgeleitet sind <xref:System.Windows.UIElement> und Implementieren von <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Zwei spezielle Arten von Randsteuerelement Tag sind die <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, für Zusatzelemente, die den gleichen Speicherplatz wie der Text in einer Ansicht zu belegen und die <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, für die Unterstreichung Wellenlinie.  
  
 Eingebettete Zusatzelemente sind Grafiken, die Teil der Sicht formatierten Text zu bilden. Sie sind auf unterschiedlichen Ebenen der Z-Reihenfolge angeordnet. Gibt es drei vordefinierte Ebenen, wie folgt werden: Text, der Einfügemarke und die Auswahl. Entwickler können jedoch weitere Ebenen definieren, und fügen Sie sie in der Reihenfolge in Bezug auf einen anderen. Die drei Typen von eingebetteten Zusatzelemente sind Text relativ Zusatzelemente (die verschieben, wenn der Text wird verschoben und werden gelöscht. wenn der Text gelöscht wurde), relativ zum Anzeigen von randsteuerelementen (die mit-n Nichttext Teilen der Ansicht zu tun haben) und Besitzer-gesteuerten Zusatzelemente (die Entwickler muss ihrer Platzierung verwalten).  
  
 Popup Zusatzelemente sind Grafiken, die in einem kleinen Fenster oberhalb der Textansicht, z. B. QuickInfos angezeigt werden.  
  
###  <a name="projection"></a> Projektion  
 Projektion ist ein Verfahren zum Erstellen einer anderen Art von Textpuffer, die nicht tatsächlich Text gespeichert, sondern stattdessen kombiniert Text aus anderen Textpuffer. Ein Projektionspuffer kann beispielsweise verwendet werden, zum Verketten von Text aus zwei anderen Puffer und das Ergebnis darstellen, als wäre er in nur einem Puffer wird oder Teile des Texts in einem Puffer auszublenden. Ein Projektionspuffer kann als einen Quellpuffer in einen anderen Projektionspuffer fungieren. Ein Satz von Puffern, die von der Projektion beziehen kann erstellt werden, um Text auf viele verschiedene Arten neu anordnen. (Eine solchen Menge ist auch bekannt als ein *Puffer Graph*.) Die Gliederungsfunktion des Visual Studio Text wird mithilfe eines Projektionspuffers um den reduzierten Text auszublenden implementiert, und die Visual Studio-Editor für die ASP.NET-Seiten-Projektion verwendet, um eingebettete Sprachen wie Visual Basic und c# unterstützen.  
  
 Ein <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> wird erstellt, indem Sie mithilfe von <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Ein Projektionspuffer wird durch eine geordnete Sequenz von dargestellt <xref:Microsoft.VisualStudio.Text.ITrackingSpan> Objekte, die als bekanntermaßen *Datenquelle Spannen*. Der Inhalt dieser Spannen wird als eine Folge von Zeichen angezeigt. Der Textpuffer aus der Quellspannen gezeichnet werden, werden mit dem Namen *Datenquelle Puffer*. Clients eines Puffers Projektion ist nicht erforderlich, um bewusst sein, dass es ein normales Textpuffer unterscheidet.  
  
 Die Projektionspuffer überwacht textänderung Ereignisse auf der Quellpuffer. Wenn der Text in einer Datenquelle umfassen ändert, wird der Projektionspuffer ordnet die Koordinaten geänderter Text in einem eigenen Koordinaten und löst Ereignisse aus entsprechenden textänderung. Betrachten Sie beispielsweise Quellpuffer A und B, die über diesen Inhalt verfügen:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Wenn Projektionspuffer P aus zwei unzusammenhängende, alle Puffer als auch die Kennzeichnung gebildet wird, andere, die alle Puffer B vorhanden sind, hat P den folgenden Inhalt:  
  
```  
P: ABCDEvwxyz  
```  
  
 Wenn die Teilzeichenfolge `xy` aus Puffer B, gelöscht, und klicken Sie dann Puffer P löst ein Ereignis aus, der angibt, dass die Zeichen an Position 7 und 8 gelöscht wurden.  
  
 Die Projektionspuffer kann auch direkt bearbeitet werden. Es gibt Änderungen an der entsprechenden Quellpuffer weiter. Eine Zeichenfolge in Puffer P an Position 6 (der ursprünglichen Position des Zeichens "V") eingefügt wird, wird z. B. das Einfügen in Puffer B an Position 1 weitergegeben.  
  
 Es gibt Einschränkungen für die Quellspannen, die auf einen Projektionspuffer beitragen. Quellspannen überschneiden sich möglicherweise nicht; eine Position in einer Projektionspuffer kann nicht an mehreren Stellen in jeder Quellpuffer zuordnen kann nicht, und eine Position in einen Quellpuffer zu mehr als einer Position in einem Projektionspuffer. In der Quelle Puffer Beziehung sind keine Circularities zulässig.  
  
 Ereignisse werden ausgelöst, wenn der Satz von puffert einer Projektion Puffer geändert, und wenn der Satz von Änderungen umfasst.  
  
 Ein Elisionspuffer ist eine besondere Art von Projektionspuffer. Es dient in erster Linie für eine Gliederung und für Vorgänge, die erweitert und reduziert die Textblöcke bestimmt. Ein Elisionspuffer basiert auf nur einem Quellpuffer und der Spannen im Elisionspuffer bestellt werden müssen, die gleiche wie sie in der Quellpuffer sortiert werden.  
  
##### <a name="the-buffer-graph"></a>Der Pufferdiagramm  
 Die <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Schnittstelle ermöglicht die Zuordnung für ein Diagramm der Projektionspuffer. Alle Textpuffer und Projektionspuffer werden in ein gerichtetes azyklisches Diagramm, ähnlich wie die abstrakte Syntaxstruktur gesammelt, die durch einen Sprachcompiler erzeugt wird. Das Diagramm wird durch den oberen Puffer definiert, die keinen Textpuffer werden können. Das Pufferdiagramm kann von einem Punkt in der oberen Puffer zu einem Zeitpunkt einen Quellpuffer oder aus einer Spanne im obersten Puffer auf einen Satz von Spannen in einen Quellpuffer zuordnen. Sie können auf ähnliche Weise, ordnen Sie einen Punkt oder aus einem Quellpuffer zu einem Zeitpunkt in der oberen Puffer umfassen. Puffer Diagramme werden erstellt, mit der <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
##### <a name="events-and-projection-buffers"></a>Ereignisse und Projektionspuffer  
 Wenn ein Projektionspuffer geändert wird, werden die Änderungen aus dem Projektionspuffer in den Puffer gesendet, die von ihm abhängig sind. Nachdem alle Puffer geändert werden, werden Puffer Change-Ereignissen ausgelöst, mit dem tiefsten Puffer ab.  
  
###  <a name="outlining"></a> Gliederung  
 Gliederung ist die Fähigkeit zum Erweitern oder reduzieren unterschiedliche Textblöcke in einer Textansicht. Gliederung ist definiert als eine Art von <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, auf die gleiche Weise wie Zusatzelemente definiert sind. Ein <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ist ein Tag, das einen Textbereich definiert, die erweitert oder reduziert werden können. Um Gliederung zu verwenden, müssen Sie importieren die <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> zum Abrufen einer <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Gliederungsmodus Manager zählt, reduziert und erweitert die verschiedenen Blöcke, die als dargestellt werden <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> -Objekte und entsprechend löst Ereignisse aus.  
  
###  <a name="mousebindings"></a> Maus Bindungen  
 Maus Bindungen verknüpfen mausbewegungen mit anderen Befehlen. Mithilfe von Maus Bindungen definiert ein <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, und tastenbindungen mithilfe von definiert ein <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automatisch alle Bindungen instanziiert und verbindet diese Mausereignisse in der Ansicht.  
  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> Schnittstelle enthält die vor der Verarbeitung und nachzuverarbeiten Ereignishandler für verschiedene Mausereignisse. Verarbeiten eines Ereignisses, können Sie einige der Methoden in überschreiben <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Editor-Vorgänge  
 Editor-Vorgänge können verwendet werden, um Interaktion mit dem Editor für Skripterstellung oder für andere Zwecke zu automatisieren. Sie importieren können die <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> für Access-Vorgänge in einer angegebenen <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Sie können diese Objekte klicken Sie dann die Auswahl zu ändern, führen Sie einen Bildlauf der Ansicht oder verschiebt die Einfügemarke an anderen Teilen der Ansicht.  
  
###  <a name="intellisense"></a> IntelliSense  
 Es unterstützt IntelliSense-Anweisungsvervollständigung, Signaturhilfe (auch bekannt als ParameterInfo), QuickInfo und Glühbirnen.  
  
 Anweisungsvervollständigung bietet Popup-Listen von potenziellen Abschlüssen für Methodennamen, XML-Elemente und andere Elemente zu codieren oder Markup. Im Allgemeinen wird eine Benutzeraktion eine Sitzung Abschluss aufgerufen. Die Sitzung zeigt die Liste der potenziellen Abschlüssen, und der Benutzer auswählen oder schließen Sie die Liste kann. Die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> ist verantwortlich für das Erstellen und Auslösen der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. Die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> berechnet die <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> Abschluss Elemente für die Sitzung.  
  
## <a name="see-also"></a>Siehe auch  
 [Sprachdienst und Erweiterungspunkten-Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Editor-Importe](../extensibility/editor-imports.md)
