---
title: Im Editor | Microsoft-Dokumentation
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
ms.openlocfilehash: 8f85e7c6e4ba62842986db8e6090415d2e33f1c1
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498953"
---
# <a name="inside-the-editor"></a>Im editor
Der Editor besteht aus einer Reihe von verschiedenen Subsysteme enthalten, die der Editor Text Modell Separate aus der Textansicht und die Benutzeroberfläche beibehalten werden soll.  
  
 Diese Abschnitte beschreiben die verschiedenen Aspekte der Editor:  
  
-   [Übersicht über die Subsysteme](../extensibility/inside-the-editor.md#overview-of-the-subsystems)  
  
-   [Das Textmodell](../extensibility/inside-the-editor.md#the-text-model)  
  
-   [Die Textansicht](../extensibility/inside-the-editor.md#the-text-view)  
  
 Diese Abschnitte beschreiben die Funktionen des Editors:  
  
-   [Tags und Klassifizierungen](../extensibility/inside-the-editor.md#tags-and-classifiers)  
  
-   [Zusatzelemente](../extensibility/inside-the-editor.md#adornments)  
  
-   [Projektion](../extensibility/inside-the-editor.md#projection)  
  
-   [Gliedern](../extensibility/inside-the-editor.md#outlining)  
  
-   [Mausbindungen](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [Editor-Vorgänge](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
## <a name="overview-of-the-subsystems"></a>Übersicht über die Subsysteme  
  
### <a name="text-model-subsystem"></a>Text-Modell-subsystem  
 Das Subsystem des Text-Modell dient, die Text darstellt, und aktivieren die Bearbeitung. Das Subsystem des Text-Modell enthält die <xref:Microsoft.VisualStudio.Text.ITextBuffer> -Schnittstelle, die die Sequenz von Zeichen beschreibt, die vom Editor angezeigt werden soll. Dieser Text kann geändert, nachverfolgt und auf viele Arten bearbeitet werden. Der Textmodell bietet auch Typen, für die folgenden Aspekte:  
  
-   Ein Dienst, der Text mit Dateien zugeordnet, und verwaltet werden, lesen und Schreiben sie im Dateisystem.  
  
-   Eine differenzierende Dienst, der die minimale Unterschiede zwischen zwei Sequenzen von Objekten gefunden werden.  
  
-   Ein System zum Beschreiben des Texts in einem Puffer im Hinblick auf eine Teilmenge des Texts in andere Puffer.  
  
 Das Subsystem des Text-Modell ist der Benutzer-Benutzeroberfläche (UI)-Konzepte. Beispielsweise ist nicht verantwortlich für das Formatieren von Text oder das Textlayout, und sie hat keine Kenntnisse visual Zusatzelemente, die den Text zugeordnet sein können.  
  
 Die öffentlichen Typen des Subsystems, Text-Modell sind in enthalten *Microsoft.VisualStudio.Text.Data.dll* und *Microsoft.VisualStudio.CoreUtility.dll*, die nur auf der Basis von .NET Framework abhängig sind Class-Bibliothek und das Managed Extensibility Framework (MEF).  
  
### <a name="text-view-subsystem"></a>Text anzeigen-subsystem  
 Das Text-Ansicht-Subsystem ist verantwortlich für das Formatieren und Anzeigen von Text. Die Typen dieses Subsystem Abfragesignaturen wird in zwei Ebenen, je nachdem, ob die Typen in Windows Presentation Foundation (WPF) basieren. Die wichtigsten Typen sind <xref:Microsoft.VisualStudio.Text.Editor.ITextView> und <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, die steuern, den Satz von Textzeilen ab, die angezeigt werden, und auch die Einfügemarke, die Auswahl und die Funktionen zum Verzieren von Text mithilfe von WPF-UI-Elementen. Dieses Subsystem sorgt auch, dass Ränder um den Text im angezeigt werden kann. Dieser Ränder können erweitert werden, und Sie können verschiedene Arten von Inhalten und visuelle Effekte enthalten. Beispiele für Ränder sind Zeile Anzahl zeigt und Bildlaufleisten.  
  
 Die öffentlichen Typen des Subsystems Text anzeigen, sind in enthalten *Microsoft.VisualStudio.Text.UI.dll* und *Microsoft.VisualStudio.Text.UI.Wpf.dll*. Die erste Assembly die plattformunabhängige-Elemente enthält und die zweite enthält die WPF-spezifische Elemente.  
  
### <a name="classification-subsystem"></a>Klassifizierung-subsystem  
 Das Subsystem für die Klassifizierung ist zuständig für das Ermitteln von Eigenschaften für die Schriftart für Text. Eine Klassifizierung teilt den Text in verschiedene Klassen, z. B. "Schlüsselwort" oder "Kommentar". Die formatierungszuordnung bezieht sich diese Klassen auf tatsächliche Schriftarteigenschaften, z. B. "Blue Consolas 10 pt". Diese Informationen werden von der Textansicht verwendet, wenn es formatiert und Text gerendert. Tags, die weiter unten in diesem Thema ausführlicher beschrieben wird, können Daten Textbereiche zugeordnet werden soll.  
  
 Die öffentlichen Typen des Subsystems, Klassifizierung in Microsoft.VisualStudio.Text.Logic.dll enthalten sind, und sie interagieren mit der visuellen Aspekte der Klassifizierung, die in Microsoft.VisualStudio.Text.UI.Wpf.dll enthalten sind.  
  
### <a name="operations-subsystem"></a>Operations-subsystem  
 Das Subsystem für die Vorgänge definiert die Editor-Verhalten. Stellt die Implementierung für Visual Studio-Editor-Befehle und das System rückgängig.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Genauere Betrachtung des Text-Modells und der Textansicht  
  
### <a name="the-text-model"></a>Das Textmodell  
 Das Text-Modell-Subsystem besteht aus unterschiedliche Gruppierungen der Texttypen. Dazu gehören, die den Textpuffer, Textmomentaufnahmen und Textspannen.  
  
#### <a name="text-buffers-and-text-snapshots"></a>Textpuffer und Textmomentaufnahmen  
 Die <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle stellt eine Sequenz von Unicode-Zeichen, die codiert werden, mithilfe von UTF-16, die die Codierung ein, die ist die `String` Typ in .NET Framework. Ein Textpuffer als System-Dateidokument beibehalten werden kann, aber dies ist nicht erforderlich.  
  
 Die <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> dient zum Erstellen von ein leerer Text-Puffer oder einen Textpuffer, der aus einer Zeichenfolge oder von initialisiert wird <xref:System.IO.TextReader>. Das Textpuffer beibehalten werden kann, in das Dateisystem als eine <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 Das Textpuffer kann von jedem Thread bearbeitet werden, bis ein Thread den Besitz des Textpuffers durch den Aufruf nimmt <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Danach kann nur von diesem Thread Bearbeitungen ausführen.  
  
 Ein Textpuffer kann viele Versionen während seiner Lebensdauer durchlaufen. Eine neue Version wird generiert, jedes Mal, wenn der Puffer bearbeitet wird, und ein unveränderliches <xref:Microsoft.VisualStudio.Text.ITextSnapshot> den Inhalt dieser Version des Puffers darstellt. Da Textmomentaufnahmen unveränderlich sind, können Sie eine Textmomentaufnahme, auf einem beliebigen Thread ohne Einschränkungen zugreifen, selbst wenn ändern weiterhin der Textpuffer, den es darstellt.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Textmomentaufnahmen und Momentaufnahmen von Textzeilen  
 Sie können den Inhalt einer Textmomentaufnahme als eine Folge von Zeichen oder als eine Sequenz von Zeilen anzeigen. Zeichen und Zeilen sind, dass beide indiziert, beginnend mit 0 (null). Eine leerer Text-Momentaufnahme enthält keine Zeichen und eine leere Zeile. Eine Linie als Trennzeichen dient eine beliebige gültige Unicode-Line-Break-Zeichen-Sequenz oder vom Anfang oder Ende des Puffers. Zeilenumbruchzeichen werden explizit in der Textmomentaufnahme dargestellt, und die Zeilenumbrüche in einer Textmomentaufnahme müssen nicht alle identisch sein.  
  
> [!NOTE]
>  Weitere Informationen zu den Zeilenumbruchzeichen in Visual Studio-Editor, finden Sie unter [Codierungen und Zeilenumbrüche](../ide/encodings-and-line-breaks.md).  
  
 Eine Textzeile wird dargestellt, indem ein <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> -Objekt, das von einer Textmomentaufnahme, die für eine bestimmte Zeilennummer oder einer bestimmten Zeichenposition abgerufen werden kann.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints SnapshotSpans und NormalizedSnapshotSpanCollections  
 Ein <xref:Microsoft.VisualStudio.Text.SnapshotPoint> eine Zeichenposition in eine Momentaufnahme darstellt. Die Position ist garantiert liegen zwischen 0 (null) und die Länge der Momentaufnahme. Ein <xref:Microsoft.VisualStudio.Text.SnapshotSpan> stellt eine Textpassage in einer Momentaufnahme dar. Die Endposition ist garantiert liegen zwischen 0 (null) und die Länge der Momentaufnahme. Die <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> besteht aus einem Satz von <xref:Microsoft.VisualStudio.Text.SnapshotSpan> Objekte aus der gleichen Momentaufnahme.  
  
#### <a name="spans-and-normalizedspancollections"></a>Span-Elemente und NormalizedSpanCollections  
 Ein <xref:Microsoft.VisualStudio.Text.Span> stellt einen Zeitraum an, die auf einen Textabschnitt in einer Textmomentaufnahme angewendet werden kann. Momentaufnahme Positionen sind nullbasiert, sodass Spannen an einer beliebigen Position, einschließlich 0 (null) beginnen können. Die `End` -Eigenschaft eines Textabschnitts ist gleich der Summe aus der `Start` Eigenschaft und die zugehörige `Length` Eigenschaft. Ein `Span` schließt nicht das Zeichen, das von indiziert wird die `End` Eigenschaft. Z. B. eine Spanne, die Start = 5 und Länge = 3 verfügt über End = 8, und die Zeichen an den Positionen 5, 6 und 7 enthält. Die Notation für diese Spanne ist 5..8).  
  
 Zwei Spannen überschneiden, wenn sie alle Positionen gemeinsam haben, einschließlich die Endposition. Aus diesem Grund die Schnittmenge der [3, 5) und [2, 7) ist [3, 5) sowie die Auswirkungen von [3, 5) und [5, 7) wird [5, 5). (Beachten Sie, dass [5, 5) ist eine leere Span.)  
  
 Zwei Spannen überschneiden sich, wenn sie Positionen mit Ausnahme von der Endposition gemeinsam haben. Eine leere Span nie überschneidet sich mit jeder anderen Spanne aus, und die Überlappung von zwei Spannen ist niemals leer.  
  
 Ein <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> ist eine Liste von Spannen in der Reihenfolge der Start-Eigenschaften der Spannen. In der Liste werden überlappende oder benachbarte Spannen zusammengeführt. Angenommen, den Satz von Spannen [5..9), [0..1), [3..6), und [9..10), wird die normalisierte Liste von Spannen [0..1), [3..10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>Änderungsbenachrichtigungen für ITextEdit, TextVersion und text  
 Der Inhalt eines Textpuffers kann geändert werden, mithilfe einer <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt. Erstellen eines solchen Objekts (mithilfe eines der `CreateEdit()` Methoden der <xref:Microsoft.VisualStudio.Text.ITextBuffer>) startet eine Transaktion von Text, der Textbearbeitungen besteht. Jede Bearbeitung ist ein Ersatz für einige Textabschnitt im Puffer durch eine Zeichenfolge. Die Koordinaten und den Inhalt jeder Änderung werden relativ zu den Snapshot des Puffers ausgedrückt, wenn die Transaktion gestartet wurde. Die <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt passt die Koordinaten der Bearbeitungen, die von anderen Änderungen in der gleichen Transaktion betroffen sind.  
  
 Betrachten Sie z. B. einen Textpuffer, der diese Zeichenfolge enthält:  
  
```  
abcdefghij  
```  
  
 Wenden Sie eine Transaktion, enthält zwei Änderungen, die eine Bearbeitung, das die Spanne an ersetzt [2..4) mit dem Zeichen `X` und eine zweite bearbeiten, das die Spanne an ersetzt [6..9) mit dem Zeichen `Y`. Das Ergebnis ist dieser Puffer:  
  
```  
abXefYj  
```  
  
 Die Koordinaten für die zweite Bearbeitung berechnet wurden in Bezug auf den Inhalt des Puffers zu Beginn der Transaktion statt, bevor die erste Änderung nicht angewendet wurde.  
  
 Die Änderungen in den Puffer wirksam bei der <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt wird ein Commit ausgeführt, durch den Aufruf der `Apply()` Methode. Wenn es mindestens eine nicht leere bearbeiten wurde, ein neues <xref:Microsoft.VisualStudio.Text.ITextVersion> erstellt wird, ein neues <xref:Microsoft.VisualStudio.Text.ITextSnapshot> erstellt wird, und ein `Changed` Ereignis wird ausgelöst. Jeder Textversion besitzt ein anderes Textmomentaufnahme. Eine Textmomentaufnahme steht der gesamten Zustands des Textpuffers, nachdem eine Transaktion zum Bearbeiten, aber eine Textversion beschreibt nur die Änderungen von einer Momentaufnahme, die sich auf die nächste. Im Allgemeinen sind Textmomentaufnahmen einmal verwendet werden sollen, und klicken Sie dann verworfen, während-Text-Versionen für einige Zeit aktiv bleiben müssen.  
  
 Eine Text-Version enthält eine <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Dieser Sammlung werden die Änderungen beschrieben, wenn die Momentaufnahme angewendet wird, erzeugt die nachfolgenden Momentaufnahme. Jede <xref:Microsoft.VisualStudio.Text.ITextChange> in der Auflistung enthält die Zeichenposition, der die Änderung der ersetzten Zeichenfolge und die Ersetzungszeichenfolge. Die ersetzte Zeichenfolge ist leer, um eine einfache Einfügung, und die Ersatzzeichenfolge ist leer, um eine grundlegende löschen. Die normalisierte Auflistung ist immer `null` für die neueste Version des Textpuffers.  
  
 Nur ein <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt kann für einen Textpuffer zu einem beliebigen Zeitpunkt instanziiert werden, und alle Textbearbeitungen müssen ausgeführt werden, auf dem Thread, der den Textpuffer besitzt (sofern es sich bei den Besitz genommen hat). Eine Textbearbeitung kann abgebrochen werden, durch den Aufruf der `Cancel` Methode oder den zugehörigen `Dispose` Methode.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> bietet außerdem `Insert()`, `Delete()`, und `Replace()` finden Sie Methoden, die denen ähneln, auf die <xref:Microsoft.VisualStudio.Text.ITextEdit> Schnittstelle. Dieser Aufruf hat dieselbe Wirkung wie das Erstellen einer <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt, dem ähnlichen Aufruf und dann die Bearbeitung angewendet.  
  
#### <a name="tracking-points-and-tracking-spans"></a>Überwachungspunkte und Nachverfolgungsspannen  
 Ein <xref:Microsoft.VisualStudio.Text.ITrackingPoint> eine Zeichenposition in einem Textpuffer darstellt. Wenn der Puffer in einer Weise, die bewirkt, die Position des Zeichens bearbeitet wird dass verschoben, wechselt der der Nachverfolgungspunkt mit. Bezieht sich z. B. wenn ein Verfolgungspunkt bezieht sich auf Position 10 in einem Puffer und fünf Zeichen am Anfang des Puffers eingefügt werden, der Nachverfolgungspunkt klicken Sie dann auf die Position 15. Wenn eine Einfügung an genau der Position, gekennzeichnet durch der Nachverfolgungspunkt der Fall ist, richtet sich das Verhalten nach der <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, dem kann es sich entweder `Positive` oder `Negative`. Wenn der Modus zum Nachverfolgen von positiv ist, bezieht sich der Nachverfolgungspunkt auf dem gleichen Zeichen, das am Ende der Einfügung jetzt ist ein; Wenn der Modus zum Nachverfolgen von negativ ist, bezieht sich der Nachverfolgungspunkt auf das eingefügte erste Zeichen an der ursprünglichen Position ein. Wenn das Zeichen an der Position, die durch einen Nachverfolgungspunkt dargestellt wird, gelöscht wird, wechselt der der Nachverfolgungspunkt auf das erste Zeichen, das den gelöschten Bereich folgt. Bezieht sich z. B. wenn ein Verfolgungspunkt bezieht sich auf das Zeichen an Position 5 und die Zeichen an Position 3 bis 6 werden gelöscht, der Nachverfolgungspunkt auf das Zeichen an Position 3.  
  
 Ein <xref:Microsoft.VisualStudio.Text.ITrackingSpan> stellt einen Bereich von Zeichen, anstatt nur eine Position dar. Das Verhalten richtet sich nach der <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Ist der Modus zum Nachverfolgen von Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, die Nachverfolgungsspanne vergrößert wird, um auf die Ränder des eingefügten Texts zu integrieren, ist der Modus zum Nachverfolgen von Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, die Nachverfolgungsspanne ist nicht in Text eingefügt, an den Rändern integriert. Allerdings ist der Modus zum Nachverfolgen von Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, eine Einfügung überträgt die aktuelle Position zum Anfang, und wenn der Modus zum Nachverfolgen von Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, eine Einfügung überträgt die aktuelle Position zum Ende.  
  
 Sie können die Position eines Punkts nachverfolgung oder die Spanne des eine Nachverfolgungsspanne für jede Momentaufnahme des Textpuffers abrufen, die sie angehören. Überwachungspunkte und Nachverfolgungsspannen können sicher von jedem Thread aus verwiesen werden.  
  
#### <a name="content-types"></a>Inhaltstypen  
 Inhaltstypen werden einen Mechanismus zum Definieren verschiedene Arten von Inhalt an. Ein Inhaltstyp möglich einen Dateityp, z. B. "Text", "Code" oder "binary" oder einen Technologietyp, z. B. "Xml", "Vb" oder "c#". Beispielsweise ist das Wort "using" ein Schlüsselwort in c# und Visual Basic, aber nicht in anderen Programmiersprachen. Daher wäre die Definition dieses Schlüsselwort auf den Inhalt vom Typ "c#" oder "Vb" beschränkt.  
  
 Inhaltstypen werden als Filter für die Zusatzelemente und andere Elemente des Editors verwendet. Viele Editor-Funktionen und Erweiterungspunkte sind pro Inhaltstyp definiert. beispielsweise unterscheidet sich Text Farbgebung für nur-Text-Dateien, XML-Dateien und Visual Basic-Quellcodedateien. Textpuffer werden in der Regel einen Inhaltstyp zugewiesen, wenn sie erstellt wurden, und der Inhaltstyp eines Textpuffers geändert werden kann.  
  
 Inhaltstypen können mehrere-andere Inhaltstypen erben. Die <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> können Sie mehrere Basistypen als den übergeordneten Elementen von einem bestimmten Inhaltstyp angeben.  
  
 Entwickler können eigene Inhaltstypen zu definieren und registrieren Sie sie mithilfe der <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Viele Editor-Funktionen in Bezug auf einen bestimmten Inhaltstyp definiert werden, indem Sie mit der <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Beispielsweise können Editor Ränder und Zusatzelemente, die Maushandler definiert werden, damit sie nur für Editoren gelten, die bestimmte Inhaltstypen anzeigen.  
  
###  <a name="the-text-view"></a>Die Textansicht  
 Die Ansichtsteil der Model-View-Controller (MVC)-Muster definiert die Textansicht, die die Formatierung der Ansicht, grafische Elemente wie die Bildlaufleiste, und die Einfügemarke an. Alle Darstellungselemente von Visual Studio-Editor basieren auf WPF.  
  
#### <a name="text-views"></a>Text-Ansichten  
 Die <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Schnittstelle ist eine plattformunabhängige Darstellung einer Textansicht. Es dient in erster Linie zum Text-Dokumenten in einem Fenster angezeigt, aber es kann auch der informationsfindung für andere Zwecke, z. B. in einer QuickInfo.  
  
 Die Textansicht verweist auf verschiedene Arten von Textpuffern. Die <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> Eigenschaft bezieht sich auf eine <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> Objekt, das auf diese drei anderen Text-Puffer verweist: im Datenpuffer, der ist der oberste Puffer der Datenebene, Bearbeitungspuffer, in dem die Bearbeitung erfolgt und die visuellen Puffer, der den Puffer ist, ist in der Textansicht angezeigt.  
  
 Der Text wird formatiert basierend auf den Klassifizierungen, die auf den zugrunde liegenden Textpuffer zugeordnet sind, und gestaltet wird, durch die Verwendung der Zusatzelement-Anbieter, die die Textansicht selbst zugeordnet sind.  
  
#### <a name="the-text-view-coordinate-system"></a>Das Koordinatensystem des Text-Ansicht  
 Das Koordinatensystem des Text-Ansicht gibt die Positionen in der Textansicht an. Klicken Sie in dieses Koordinatensystem der X-Wert 0,0 entspricht dem linken Rand des Texts angezeigt wird, und der y-Wert 0,0 entspricht dem oberen Rand des Texts angezeigt wird. Die X-Koordinate, die von links nach rechts erhöht, und die y-Koordinate, die von oben nach unten erhöht.  
  
 Ein Viewport (der Teil des Texts im Textfenster angezeigt) kann nicht auf die gleiche Weise ein horizontaler Bildlauf durchgeführt werden, da es ein vertikaler Bildlauf durchgeführt wird. Ein Viewport ist ein horizontaler Bildlauf durch die linke Koordinate ändern, sodass es in Bezug auf die Zeichenoberfläche durchgeführt. Allerdings ein Viewport Bildlauf möglich vertikal nur, indem Sie ändern den gerenderten Text, der bewirkt, dass eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Ereignis ausgelöst wurde.  
  
 Entfernungen im Koordinatensystem in logische Pixel entsprechen. Wenn die Oberfläche des Text-Rendering ohne Skalierung Transformation angezeigt wird, klicken Sie dann entspricht eine Einheit in den Textrendering-Koordinatensystem ein Pixel in der Anzeige.  
  
#### <a name="margins"></a>Seitenränder  
 Die <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> Schnittstelle stellt einen Rand und aktiviert die Steuerung der Sichtbarkeit der den Rand und seine Größe. Es gibt vier vordefinierte Ränder, werden mit dem Namen "Top", "Left", "Right" und "Bottom", und der oberen, unteren, linken oder rechten Rand einer Sicht zugeordnet sind. Dieser Ränder sind Container, die in denen anderen Rändern platziert werden können. Die Schnittstelle definiert Methoden, die die Größe des Rands und die Sichtbarkeit der einen Rand zurückgeben. Ränder werden visuelle Elemente, die zusätzliche Informationen über die Textansicht bereitstellen, mit denen sie verbunden sind. Beispielsweise zeigt die Zeilennummer Rand Zeilennummern für die Textansicht. Der Symbolrand Zeigt Elemente der Benutzeroberfläche.  
  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Schnittstelle behandelt die Erstellung und die Platzierung der Ränder. Ränder können in Bezug auf die anderen Rändern sortiert werden. Ränder mit höherer Priorität befinden sich näher bei der Textansicht an. Beispielsweise wird angezeigt, wenn es zwei linken Rand, A und B-Seitenrand gibt und Rand B hat eine niedrigere Priorität als Rand ein, Rand B auf der linken Seite des Rands A.  
  
#### <a name="the-text-view-host"></a>Die Textansicht-host  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Schnittstelle enthält die Textansicht und alle angrenzenden Ergänzungen, die die Sicht, z. B. die Bildlaufleisten zu begleiten. Der textansichthost enthält auch die Ränder, die einen Rahmen der Ansicht zugeordnet sind.  
  
#### <a name="formatted-text"></a>Formatierter Text  
 Der Text, der in einer Textansicht angezeigt wird besteht <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Objekte. Jede Zeile in der Textansicht entspricht einer Zeile des Texts in der Textansicht. Lange Zeilen im zugrunde liegenden Textpuffer können werden teilweise verdeckt (wenn der Zeilenumbruch nicht aktiviert ist) oder in mehrere Text-Ansicht Zeilen unterteilt. Die <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Schnittstelle enthält Methoden und Eigenschaften für die Zuordnung zwischen Koordinaten und Zeichen, und klicken Sie für die Zusatzelemente, die der Zeile zugeordnet sein können.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Objekte werden erstellt, mit einem <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> Schnittstelle. Wenn Sie nur den Text, die derzeit in der Ansicht angezeigt wird befürchten, können Sie die Quelle die Formatierung ignorieren. Wenn Sie das Format des Texts interessiert sind, die nicht angezeigt, in der Ansicht (z. B. unterstützen eine Rich-Text Ausschneiden und Einfügen), können Sie <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> zum Formatieren von Text in einem Textpuffer.  
  
 Die Textansicht formatiert eine <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> zu einem Zeitpunkt.  
  
## <a name="editor-features"></a>Editor-Funktionen  
 Die Funktionen des Editors sind so konzipiert, dass die Definition der Funktion von ihrer Implementierung getrennt ist. Der Editor bietet folgende Funktionen:  
  
-   Tags und Klassifizierungen  
  
-   Zusatzelemente  
  
-   Projection  
  
-   Gliedern  
  
-   Maus und Tastatur-Bindungen  
  
-   Vorgänge und primitive  
  
-   IntelliSense  
  
### <a name="tags-and-classifiers"></a>Tags und Klassifizierungen  
 Tags sind Marker, die einen Textabschnitt zugeordnet sind. Sie können auf unterschiedliche Weise z. B. dargestellt werden mithilfe von Farben für Text, unterstreichungen, Grafiken oder Popups. Klassifizierer sind eine Art von Tags.  
  
 Andere Arten von Tags sind <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> für die Hervorhebung von Text, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> für Gliederungen, und <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> für Kompilierungsfehler.  
  
#### <a name="classification-types"></a>Klassifizierungstypen  
 Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Schnittstelle darstellt, eine äquivalenzklasse, die eine abstrakte Kategorie von Text ist. Klassifizierungstypen können mehrere-andere Klassifizierungstypen erben. Z. B. sind sprachklassifizierungen Programmierung zum Beispiel "Schlüsselwort", "Comment" und "Bezeichner", die alle von "Code" erben. Klassifizierungstypen natürlicher Sprache sind zum Beispiel "Nomen", "Verb" und "Adjektiv", die alle von "natürlicher Sprache" erben.  
  
#### <a name="classifications"></a>Klassifizierungen  
 Eine Klassifizierung ist eine Instanz eines bestimmten Klassifizierungstyps, in der Regel über einen Textabschnitt. Ein <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> wird verwendet, um eine Klassifizierung darstellen. Eine Spanne der Klassifizierung kann als Bezeichnung betrachtet werden, die einen bestimmten Textabschnitt behandelt und weist das System, das diese Spanne von Text für einen bestimmten Klassifizierungstyp.  
  
#### <a name="classifiers"></a>Klassifizierungen  
 Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ist ein Mechanismus, die Text in einem Satz von Klassifizierungen zu beeinträchtigen. Klassifizierungen müssen für bestimmte Inhaltstypen definiert und instanziiert wird, bestimmten Textpuffer. Clients müssen implementieren <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> textklassifizierung teilnehmen.  
  
#### <a name="classifier-aggregators"></a>Klassifizierung Aggregatoren  
 Eine Klassifizierungsaggregator ist ein Mechanismus, der alle Klassifizierer von für einen Textpuffer zu nur einem Satz von Klassifizierungen kombiniert. Beispielsweise können sowohl eine C#-Klassifizierung und einen Klassifizierer für die englische Sprache Klassifizierungen über einen Kommentar in einer C#-Datei erstellen. Betrachten Sie diesen Kommentar:  
  
```  
// This method produces a classifier  
```  
  
 Eine C#-Klassifizierung kann die ganze Spanne als Kommentar bezeichnen und die Klassifizierung der englischen Sprache möglicherweise als "Verb" und "Method" als ein "Nomen" klassifiziert "erstellt". Der Aggregator erzeugt einen Satz von Klassifizierungen nichtüberlappender, und der Typ der Menge basiert darauf, dass alle Ihre Beiträge.  
  
 Eine Klassifizierungsaggregator ist auch eine Klassifizierung aus, da sie Text in einem Satz von Klassifizierungen beschädigt. Klassifizierungsaggregator wird auch sichergestellt, es sind keine überlappenden Klassifizierungen und die Klassifizierungen sortiert werden. Einzelne Klassifizierer sind zurückgeben, einen beliebigen Satz von Klassifizierungen, in beliebiger Reihenfolge und überlappende in keiner Weise.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Formatieren von Klassifizierung und Text-Farben  
 Formatieren von Text ist ein Beispiel für eine Funktion, die für textklassifizierung erstellt wird. Es wird durch die ansichtsschicht Text verwendet, um die Anzeige von Text in einer Anwendung zu bestimmen. Die Formatierung Textbereich ist abhängig von WPF, die logische Definition von Klassifizierungen ist jedoch nicht.  
  
 Ein Klassifizierungsformat ist eine Reihe von Formatierungseigenschaften für einen bestimmten Klassifizierungstyp. Diese Formate erben das Format des übergeordneten Elements des Klassifizierungstyps ab.  
  
 Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> ist eine Zuordnung von einem Klassifizierungstyp auf einen Satz von Eigenschaften für die textformatierung. Die Implementierung der gekachelten im Editor verarbeitet alle Exporte der Klassifizierung Formate.  
  
###   <a name="adornments"></a>Zusatzelemente  
 Zusatzelemente sind grafische Effekte, die nicht direkt mit der Schriftart und Farbe der Zeichen in der Textansicht verknüpft sind. Z. B. der roten Wellenlinie unterstrichen, die zum Markieren von nicht-Kompilierung von Code in vielen Programmiersprachen verwendet wird, ist ein eingebettetes Zusatzelement und QuickInfos werden Popup Randsteuerelemente. Zusatzelemente, die davon abgeleitet sind <xref:System.Windows.UIElement> und implementieren Sie <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Sind zwei spezielle Arten von Zusatzelement Tag der <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, für die Zusatzelemente, die den gleichen Speicherplatz wie der Text in einer Sicht, belegen und die <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, für die Wellenlinie unterstrichen.  
  
 Eingebettete Zusatzelemente sind Grafiken, die Teil der formatierten Textansicht an. Sie sind in verschiedenen Schichten der Z-Reihenfolge angeordnet. Es gibt drei integrierte Ebenen, die folgenden: Text, der Einfügemarke und die Auswahl. Entwickler können jedoch weitere Ebenen definieren, und platzieren Sie sie in der Reihenfolge relativ zu anderen. Die drei Arten von eingebetteten Zusatzelemente sind Relative Text-Randsteuerelemente (die Verschiebung, wenn der Text bewegt wird, und werden gelöscht, wenn der Text gelöscht wird), relativen Ansicht Zusatzelemente (die mit nicht-Text, Teile der Sicht zu tun haben) und Besitzer gesteuerte Zusatzelemente (die Entwickler muss ihrer Platzierung verwalten).  
  
 Popup Zusatzelemente sind Grafiken, die in einem kleinen Fenster über der Textansicht, z. B. QuickInfos angezeigt werden.  
  
###  <a name="projection"></a> Projektion  
 Projektion ist ein Verfahren zum Erstellen einer anderen Art von Textpuffer, die nicht tatsächlich Text gespeichert, sondern stattdessen kombiniert Text aus anderer Textpuffer. Beispielsweise kann ein Projektionspuffer verwendet werden, um den Text aus zwei anderen Puffer zu verketten und das Ergebnis präsentieren, als ob sie nur ein Puffer wird, oder Teile des Texts in einem Puffer auszublenden. Ein Projektionspuffer kann als einen Quellpuffer in eine andere Projektionspuffer fungieren. Ein Satz von Puffern, die durch Projektion beziehen kann erstellt werden, um Text auf viele verschiedene Arten neu anzuordnen. (Es ist auch bekannt als solche einem *Pufferdiagramm*.) Die Visual Studio-Text-Gliederungsfunktion wird implementiert, mit einem Projektionspuffer So blenden Sie den reduzierten Text aus, und Visual Studio-Editor für ASP.NET-Seiten-Projektion verwendet, um eingebettete Sprachen wie Visual Basic und c# zu unterstützen.  
  
 Ein <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> wird erstellt, indem Sie mithilfe von <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Ein Projektionspuffer wird durch eine geordnete Sequenz von dargestellt <xref:Microsoft.VisualStudio.Text.ITrackingSpan> Objekte, die so genannte *Quellspannen*. Der Inhalt der diese Spannen werden als eine Folge von Zeichen dargestellt. Der Textpuffer, die Quellspannen aus dem stammen, heißen *source Puffer*. Clients von einem Projektionspuffer keine Bedenken, dass es einen gewöhnlichen Textpuffer unterscheidet.  
  
 Projektionspuffer Lauscht auf Text-entitätsstatusänderungs-Ereignissen auf die Quellpuffer. Wenn der Text in einer Datenquelle umfassen Änderungen, Projektionspuffer die Koordinaten der geänderten Text in eine eigene Koordinaten und löst Ereignisse aus entsprechenden textänderung. Betrachten Sie z. B. Quellpuffer A und B, die diese Inhalte verfügen:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Wenn Projektionspuffer P aus zwei Textspannen, eine, die alle Puffer ein und das hat formatiert ist, andere, die alle Puffer B hat P den folgenden Inhalt:  
  
```  
P: ABCDEvwxyz  
```  
  
 Wenn die Teilzeichenfolge `xy` aus Puffer B gelöscht wird, und klicken Sie dann die Puffer P löst ein Ereignis aus, der angibt, dass die Zeichen an Position 7 und 8 gelöscht wurden.  
  
 Projektionspuffer kann auch direkt bearbeitet werden. Es verteilt Bearbeitungen, um die entsprechenden Quellpuffer. Wenn eine Zeichenfolge in Puffer P an Position 6 (der ursprünglichen Position den Buchstaben "V") eingefügt wird, wird z. B. das Einfügen in Puffer B an Position 1 weitergegeben.  
  
 Es gibt Einschränkungen hinsichtlich der Quellspannen, die zu einem Projektionspuffer beitragen. Quellspannen überlappen sich möglicherweise nicht; eine Position in einem Projektionspuffer kann nicht auf mehr als einem Speicherort in einem Quellpuffer, und ein Speicherort in einem Quellpuffer kann nicht mehr als einem Speicherort in einem Projektionspuffer zugeordnet. Keine Circularities sind in der Quelle Puffer Beziehung zulässig.  
  
 Ereignisse werden ausgelöst, wenn der Satz von Puffern wird für eine Projektion Puffer ändert und wenn der Satz von Änderungen umfasst.  
  
 Ein Elisionspuffer ist eine besondere Art von Projektionspuffer. Es wird hauptsächlich für eine Gliederung und für Vorgänge, die erweitern und reduzieren die Textblöcke. Ein Elisionspuffer basiert darauf, dass nur eine Quellpuffer, und die Spannen im Elisionspuffer bestellt werden müssen, gleich, wie sie in den Quellpuffer sortiert sind.  
  
#### <a name="the-buffer-graph"></a>Die dem Pufferdiagramm  
 Die <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Schnittstelle ermöglicht die Zuordnung für ein Diagramm der Projektionspuffer. Alle Textpuffer und Projektionspuffer werden in einem gerichteten azyklischen Graph, ähnlich wie die abstrakte Syntaxstruktur gesammelt, die mit einem Sprachcompiler erstellt wird. Das Diagramm wird vom obersten Puffer, definiert, die Textpuffer werden kann. Die dem Pufferdiagramm kann von einem Punkt im obersten Puffer zu einem Zeitpunkt in einem Quellpuffer oder eine Spanne in der oberen Puffer auf einen Satz von Spannen in einem Quellpuffer zuordnen. Auf ähnliche Weise können sie ordnen einen Punkt oder aus einem Quellpuffer zu einem Zeitpunkt im obersten Puffer umfassen. Puffer-Diagramme werden erstellt, mit der <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
#### <a name="events-and-projection-buffers"></a>Ereignisse und Projektionspuffer  
 Ein Projektionspuffer geändert wurde, werden die Änderungen aus dem Projektionspuffer in den Puffer gesendet, von die sie abhängen. Nachdem alle Puffer geändert werden, werden Puffer Änderungsereignisse ausgelöst, mit dem tiefsten Puffer ab.  
  
###  <a name="outlining"></a> Gliederung  
 Gliederung ist die Möglichkeit zum Erweitern oder reduzieren unterschiedliche Textblöcke in einer Textansicht. Gliederung ist definiert als eine Art von <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, in der gleichen Weise wie Zusatzelemente definiert sind. Ein <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ist ein Tag, das einen Textbereich definiert, die erweitert oder reduziert werden können. Um Gliederung zu verwenden, müssen Sie importieren die <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> zum Abrufen einer <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Der gliederungs-Manager listet reduziert und erweitert die verschiedene Blöcke, die als dargestellt werden <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> Objekte aus, und löst Ereignisse entsprechend.  
  
###  <a name="mousebindings"></a> Mausbindungen  
 Mausbindungen verknüpfen mausbewegungen auf andere Befehle. Mausbindungen mithilfe von definiert eine <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, und tastenzuordnungen mithilfe von definiert eine <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automatisch alle Bindungen instanziiert und verbindet sie mit der Mausereignisse in der Ansicht.  
  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> Schnittstelle enthält, vorab zu verarbeiten und nach der Verarbeitung-Ereignishandlern für verschiedene Mausereignisse. Um ein Handle eines der Ereignisse, können Sie einige der Methoden in überschreiben <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Editor-Vorgänge  
 Editor-Vorgänge können verwendet werden, um Interaktion mit dem Editor für Skripterstellung oder für andere Zwecke zu automatisieren. Können Sie importieren die <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> für Zugriffsvorgänge auf einen bestimmten <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Sie können diese Objekte klicken Sie dann verwenden, um die Auswahl zu ändern, führen Sie einen Bildlauf der Ansicht oder verschiebt die Einfügemarke an verschiedenen Teilen der Ansicht.  
  
###  <a name="intellisense"></a> IntelliSense  
 Es unterstützt IntelliSense-Anweisungsvervollständigung, Signaturhilfe (auch bekannt als "ParameterInfo"), QuickInfo und Glühbirnen.  
  
 Anweisungsvervollständigung bietet Popup-Listen mit möglichen vervollständigungen für Methodennamen, XML-Elemente und andere Elemente zu codieren oder Markup. Eine Benutzeraktion ruft in der Regel eine vervollständigungssitzung. Die Sitzung wird die Liste der möglichen vervollständigungen angezeigt, und der Benutzer wählen Sie eine oder die Liste zu schließen. Die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> ist verantwortlich für das Erstellen und Auslösen der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. Die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> berechnet die <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> von Vervollständigungselemente der Sitzung.  
  
## <a name="see-also"></a>Siehe auch  
 [Language-Dienst und -Editor-Erweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)   
 [Editor-Importe](../extensibility/editor-imports.md)
