---
title: "Im Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] neue - Architektur"
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 31
caps.handback.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
---
# Im Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Editor besteht aus einer Anzahl von verschiedenen Subsysteme, die entwickelt wurden, um den Editor Text Modell separaten Textansicht und die Benutzeroberfläche zu verhindern.  
  
 Diese Abschnitte beschreiben verschiedene Aspekte des Editors:  
  
-   [Übersicht über die Subsysteme](../extensibility/inside-the-editor.md#overview)  
  
-   [Das Textmodell](../extensibility/inside-the-editor.md#textmodel)  
  
-   [Die Textansicht](../extensibility/inside-the-editor.md#textview)  
  
 Diese Abschnitte beschreiben die Funktionen des Editors:  
  
-   [Tags und Klassifizierer](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [Details](../extensibility/inside-the-editor.md#adornments)  
  
-   [Projection](../extensibility/inside-the-editor.md#projection)  
  
-   [Gliedern](../extensibility/inside-the-editor.md#outlining)  
  
-   [Maus-Bindungen](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [Editor-Vorgänge](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> Übersicht über die Subsysteme  
  
### Text\-Modell\-Subsystem  
 Das Text\-Modell\-Subsystem ist verantwortlich für die Darstellung von Text und die Bearbeitung aktivieren. Das Subsystem des Text\-Modell enthält die <xref:Microsoft.VisualStudio.Text.ITextBuffer> \-Schnittstelle, die die Sequenz von Zeichen beschreibt, die vom Editor angezeigt werden soll. Dieser Text kann geändert, nachverfolgt und auf vielfältige Weise bearbeitet werden. Das Textmodell bietet auch für die folgenden Aspekte:  
  
-   Ein Dienst, der Text Dateien zugeordnet und verwaltet werden, lesen und Schreiben in das Dateisystem.  
  
-   Eine differenzierende\-Dienst, der die minimale Unterschiede zwischen zwei Sequenzen von Objekten ermittelt.  
  
-   Ein System zum Beschreiben des Texts in einem Puffer im Hinblick auf Teilmengen des Texts in andere Puffer.  
  
 Das Text\-Modell\-Subsystem ist frei von Benutzer\-Benutzeroberfläche \(UI\)\-Konzepte. Z. B. es ist nicht verantwortlich für die textformatierung oder Textlayout, und es sind keine visuellen Zusatzelemente, die mit dem Text zugeordnet werden kann.  
  
 Die öffentlichen Typen des Subsystems Modell Text sind in Microsoft.VisualStudio.Text.Data.dll und Microsoft.VisualStudio.CoreUtilitiy.dll, die nur von der .NET Framework\-Basisklassenbibliothek und das Managed Extensibility Framework \(MEF\) abhängen enthalten.  
  
### Text anzeigen\-Subsystem  
 Das Text\-Ansicht\-Subsystem ist verantwortlich für das Formatieren und Anzeigen von Text. Die Typen dieses Subsystem sind unterteilt in zwei Ebenen, je nachdem, ob die Typen in Windows Presentation Foundation \(WPF\) basieren. Die wichtigsten Typen sind <xref:Microsoft.VisualStudio.Text.Editor.ITextView> und <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, welches Steuerelement den Satz von Textzeilen, die angezeigt werden sollen, und auch die Einfügemarke, die Auswahl und die Funktionen zum Erweitern von Text mithilfe von WPF\-UI\-Elemente. Dieses Subsystem enthält zudem Ränder um den Text angezeigt. Diese Ränder erweitert werden können, und Sie können verschiedene Arten von Inhalten und visuelle Effekte enthalten. Beispiele für Ränder sind Zeile Nummer angezeigt und Bildlaufleisten.  
  
 Die öffentlichen Typen des Subsystems Ansicht Text sind in Microsoft.VisualStudio.Text.UI.dll und Microsoft.VisualStudio.Text.UI.Wpf.dll enthalten. Die erste Assembly die plattformunabhängige\-Elemente enthält und die zweite die WPF\-spezifische Elemente enthält.  
  
### Klassifizierung\-Subsystem  
 Das Subsystem für die Klassifizierung ist zuständig für das Ermitteln von Schriftarteigenschaften für Text. Eine Classifier Textumbruch in verschiedene Klassen, z. B. "Schlüsselwort" oder "Kommentar". Klassifizierung gekachelten bezieht sich diese Klassen auf tatsächliche Schriftart\-Eigenschaften, z. B. "Blue Consolas 10 pt". Diese Informationen werden durch die Textansicht verwendet, wenn formatiert und Text gerendert. Tags, die weiter unten in diesem Thema ausführlicher beschrieben wird, können Daten Textabschnitte zugeordnet werden soll.  
  
 Die öffentlichen Typen des Subsystems Klassifizierung in Microsoft.VisualStudio.Text.Logic.dll enthalten sind, und sie interagieren mit der visuellen Aspekte der Klassifizierung, die in Microsoft.VisualStudio.Text.UI.Wpf.dll enthalten sind.  
  
### Operations\-Subsystem  
 Das Subsystem Vorgänge definiert das Verhalten von Editor. Die Implementierung für Visual Studio\-Editor und dem Rückgängig\-System bereitgestellt.  
  
## Genauere Betrachtung des Text\-Modells und der Textansicht  
  
###  <a name="textmodel"></a> Das Textmodell  
 Das Text\-Modell\-Subsystem besteht aus verschiedene Gruppen von Texttypen. Dazu gehören die Textpuffer, Text\-Snapshots und Textabschnitte.  
  
#### Textpuffer und Text\-Snapshots  
 Die <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle stellt eine Folge von Unicode\-Zeichen, die codiert werden, mithilfe der UTF\-16, also die Codierung anhand der `String` Typ in .NET Framework. Ein Textpuffer als Dokument System Datei beibehalten werden kann, aber dies ist nicht erforderlich.  
  
 Die <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> Dient zum Erstellen einer leeren Textpuffer oder einen Textpuffer, der aus einer Zeichenfolge oder initialisiert wird <xref:System.IO.TextReader>. Textpuffer beibehalten werden kann, die im Dateisystem als eine <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 Textpuffer kann von jedem Thread bearbeitet werden, bis ein Thread durch Aufrufen von den Besitz Textpuffer übernimmt <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Danach kann nur von diesem Thread Bearbeitungen durchführen.  
  
 Ein Textpuffer kann viele Versionen während seiner Lebensdauer durchlaufen. Eine neue Version wird jedes Mal, wenn der Puffer bearbeitet wird, und eine unveränderliche generiert <xref:Microsoft.VisualStudio.Text.ITextSnapshot> den Inhalt dieser Version des Puffers darstellt. Da Textmomentaufnahmen unveränderlich sind, können Sie eine Textmomentaufnahme auf einem beliebigen Thread ohne Einschränkungen zugreifen, selbst wenn ändert sich fortlaufend Textpuffer, den er darstellt.  
  
#### Text\-Snapshots und Snapshot Textzeilen  
 Sie können den Inhalt einer Momentaufnahme Text als eine Folge von Zeichen oder als eine Sequenz von Linien anzeigen. Zeichen und Zeilen sind beide beginnend mit Null indiziert. Eine leerer Text\-Momentaufnahme enthält 0 \(null\) Zeichen und eine leere Zeile. Eine Linie wird durch eine beliebige gültige Unicode\-Zeilenumbruch Zeichen\-Sequenz oder vom Anfang oder Ende des Puffers begrenzt. Zeilenumbruchzeichen werden explizit in der Textmomentaufnahme dargestellt, und die Zeilenumbrüche in einem Text\-Snapshot müssen nicht alle identisch sein.  
  
> [!NOTE]
>  Weitere Informationen zu Zeilenumbruchzeichen in der Visual Studio\-Editor, finden Sie unter [Codierungen und Zeilenumbrüche](../ide/encodings-and-line-breaks.md).  
  
 Eine Textzeile wird dargestellt, indem ein <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> \-Objekt, das aus einer Textmomentaufnahme für eine bestimmte Zeilennummer oder einer bestimmten Zeichenposition abgerufen werden kann.  
  
#### SnapshotPoints, SnapshotSpans und NormalizedSnapshotSpanCollections  
 Ein <xref:Microsoft.VisualStudio.Text.SnapshotPoint> eine Zeichenposition in einem Snapshot darstellt. Die Position ist garantiert liegen zwischen 0 \(null\) und die Länge der Momentaufnahme. Ein <xref:Microsoft.VisualStudio.Text.SnapshotSpan> ein Textabschnitts in einem Snapshot darstellt. Seine Endposition garantiert liegen zwischen 0 \(null\) und die Länge der Momentaufnahme. Die <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> besteht aus einem Satz von <xref:Microsoft.VisualStudio.Text.SnapshotSpan> Objekte aus der gleichen Momentaufnahme.  
  
#### Bereiche und NormalizedSpanCollections  
 Ein <xref:Microsoft.VisualStudio.Text.Span> stellt einen Zeitraum, der auf einen Textabschnitt in einem Text\-Snapshot angewendet werden kann. Snapshot Positionen sind nullbasiert, sodass Spannen an einer beliebigen Position 0 \(null\) einschließlich beginnen können. Die `End` \-Eigenschaft eines Textabschnitts entspricht der Summe aus dessen `Start` Eigenschaft und dessen `Length` Eigenschaft. Ein `Span` umfasst nicht das Zeichen, das durch indiziert ist die `End` Eigenschaft. Angenommen, ein SPAN\-Tag, die Start \= 5 und Länge \= 3 bietet End \= 8, sowie die Zeichen an Position 5, 6 und 7. Die Notation für diese Spanne ist 5..8\).  
  
 Zwei Spannen überschneiden sich ggf. alle Positionen gemeinsam, einschließlich der Endposition. Aus diesem Grund die Schnittmenge der \[3, 5\) und \[2, 7\) ist \[3, 5\) und die Schnittmenge der \[3, 5\) und \[5, 7\) ist \[5, 5\). \(Beachten Sie, dass \[5, 5\) ist eine leere Spanne.\)  
  
 Zwei Spannen überlappen sich, wenn sie Positionen gemeinsam, mit Ausnahme der Endposition haben. Eine leere Spanne überlappt nie keine anderen Spannen, und die Überlappung von zwei Spannen ist niemals leer.  
  
 Ein <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> ist eine Liste von Spannen in der Reihenfolge der Start\-Eigenschaften der Spannen. In der Liste werden die überlappende oder angrenzende Spannen zusammengeführt. Angenommen, den Satz von Spannen \[5..9\), \[0..1\), \[3..6\), und \[9..10\), wird die normalisierte Liste von Spannen \[0..1\), \[3..10\).  
  
#### ITextEdit, TextVersion und Text Change Notifications  
 Der Inhalt eines Puffers Text kann geändert werden, mithilfe einer <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt. Ein solches Objekt erstellen \(mithilfe eines der `CreateEdit()` Methoden der <xref:Microsoft.VisualStudio.Text.ITextBuffer>\) startet eine Transaktion von Text, der von Textbearbeitungen besteht. Jede bearbeiten ist ein Ersatz einige Textabschnitts im Puffer durch eine Zeichenfolge. Die Koordinaten und den Inhalt jeder Bearbeitung werden relativ zu den Snapshot des Puffers ausgedrückt, wenn die Transaktion gestartet wurde. Das <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt passt die Koordinaten der Änderungen, die von anderen Änderungen in der gleichen Transaktion betroffen sind.  
  
 Betrachten Sie z. B. einen Textpuffer, der diese Zeichenfolge enthält:  
  
```  
abcdefghij  
```  
  
 Wenden Sie eine Transaktion, enthält zwei Änderungen, ein Eintrag, der die Spanne bei ersetzt \[2..4\) mit dem Zeichen `X` und eine zweite bearbeiten, die die Spanne bei ersetzt \[6..9\) mit dem Zeichen `Y`. Das Ergebnis ist dieser Puffer:  
  
```  
abXefYj  
```  
  
 Die Koordinaten für die zweite Bearbeitung berechnet wurden in Bezug auf den Inhalt des Puffers zu Beginn der Transaktion vor die erste Bearbeitung angewendet wurde.  
  
 Die Änderungen in den Puffer wirksam bei der <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt wird ein Commit ausgeführt, durch Aufrufen der `Apply()` Methode. Gäbe es mindestens ein nicht leeres bearbeiten, eine neue <xref:Microsoft.VisualStudio.Text.ITextVersion> erstellt wird, ein neues <xref:Microsoft.VisualStudio.Text.ITextSnapshot> erstellt wird, und eine `Changed` \-Ereignis wird ausgelöst. Jeder Textversion hat einen anderen Textmomentaufnahme. Eine Textmomentaufnahme stellt den gesamten Status der Textpuffer nach eine Transaktion zum Bearbeiten, aber eine Textversion beschreibt nur die Änderungen von einer Momentaufnahme zur nächsten. Text\-Snapshots sind im Allgemeinen einmal verwendet werden soll und dann verworfen, während Text\-Versionen für einige Zeit aktiv bleiben müssen.  
  
 Eine Text\-Version enthält eine <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Dieser Sammlung beschreibt die Änderungen, wenn die Momentaufnahme angewendet wird, erzeugt die nachfolgenden Momentaufnahme. Jede <xref:Microsoft.VisualStudio.Text.ITextChange> in der Auflistung enthält die Zeichenposition, der die Änderung der ersetzten Zeichenfolge und die Ersatzzeichenfolge. Die ersetzte Zeichenfolge für das Einfügen eines grundlegenden leer ist, und die Ersatzzeichenfolge für das Löschen einer grundlegenden leer ist. Die normalisierte Auflistung ist immer `null` für die neueste Version der Textpuffer.  
  
 Nur ein <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt für einen Textpuffer jederzeit instanziiert werden, und alle Textbearbeitungen müssen für den Thread, der Textpuffer besitzt \(sofern Besitz genommen wurden\) durchgeführt werden. Eine Textbearbeitung kann verworfen werden, durch Aufrufen der `Cancel` Methode oder den zugehörigen `Dispose` Methode.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> bietet außerdem `Insert()`, `Delete()`, und `Replace()` Methoden, mit denen ähneln finden Sie auf der <xref:Microsoft.VisualStudio.Text.ITextEdit> Schnittstelle. Dieser Aufruf hat dieselbe Wirkung wie das Erstellen einer <xref:Microsoft.VisualStudio.Text.ITextEdit> \-Objekt, ähnlich wie Anruf anzuwenden und dann bearbeiten.  
  
#### Überwachungspunkte und Nachverfolgen von Spannen  
 Eine <xref:Microsoft.VisualStudio.Text.ITrackingPoint> stellt eine Zeichenposition in einem Textpuffer. Der Puffer in einer Weise bearbeitet wird, der die Position des Zeichens verschoben wird, wechselt der Verfolgungspunkts mit. Beispielsweise verweist, wenn ein Überwachungspunkt bezieht sich auf Position 10 in einem Puffer und fünf Zeichen am Anfang des Puffers eingefügt werden, Verfolgungspunkts auf Position 15. An genau der Position, gekennzeichnet durch die Überwachungspunkt Einfügung Fall richtet sich das Verhalten nach der <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, was kann entweder `Positive` oder `Negative`. Wenn der Modus zum Nachverfolgen von positiv ist, bezieht sich die Verfolgungspunkts in das gleiche Zeichen, der es sich nun am Ende einfügen. Wenn der Modus zum Nachverfolgen von negativ ist, verweist der Überwachungspunkt bis zum ersten eingefügten Zeichen an der ursprünglichen Position. Wenn das Zeichen an der Position, die durch ein Überwachungspunkt dargestellt gelöscht wird, wechselt der Verfolgungspunkts auf das erste Zeichen, das den gelöschten Bereich folgt. Bezieht sich z. B. wenn ein Verfolgungspunkt bezieht sich auf das Zeichen an Position 5 und die Zeichen an Position 3 bis 6 werden gelöscht, Verfolgungspunkts auf das Zeichen an Position 3.  
  
 Eine <xref:Microsoft.VisualStudio.Text.ITrackingSpan> stellt einen Bereich von Zeichen anstatt nur eine Position. Das Verhalten richtet sich nach der <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Ist der Modus zum Nachverfolgen von Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, die Überwachung Spanne vergrößert wird, um Text an seinen Rändern; eingefügt zu integrieren, wenn der Modus zum Nachverfolgen von Span\-Element ist <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, die Überwachung Spanne besitzt nicht an seinen Rändern eingefügten Text. Allerdings ist der Modus zum Nachverfolgen von Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, eine Einfügung legt die aktuelle Position in Richtung Anfang und, wenn der Modus zum Nachverfolgen von Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, eine Einfügung legt die aktuelle Position am Ende.  
  
 Die Position eines Punkts nachverfolgen oder den Zeitraum für eine Überwachung Spanne erhalten für jede Momentaufnahme der Textpuffer Sie, die sie angehören. Überwachungspunkte und Nachverfolgen von Spannen können sicher von jedem Thread aus verwiesen werden.  
  
#### Inhaltstypen  
 Inhaltstypen sind ein Mechanismus zum Definieren von verschiedenen Arten von Inhalten. Ein Inhaltstyp möglich einen Dateityp, z. B. "Text", "Code" oder "binary" oder eine Technologietyp, z. B. "Xml", "Vb" oder "c\#". Beispielsweise ist das Wort "using" ein Schlüsselwort in c\# und Visual Basic, jedoch nicht in anderen Programmiersprachen. Daher wäre die Definition dieses Schlüsselwort auf die Inhaltstypen "c\#" und "Vb" beschränkt.  
  
 Inhaltstypen werden als Filter für Zusatzelemente und andere Elemente des Editors verwendet. Viele Editor\-Funktionen und Erweiterungspunkte werden pro Inhaltstyp definiert. beispielsweise unterscheidet sich Text Färbung für reine Textdateien, XML\-Dateien und Visual Basic\-Quellcodedateien. Textpuffer sind im Allgemeinen ein Inhaltstyp zugewiesen, wenn sie erstellt werden, und der Inhaltstyp eines Puffers Text geändert werden kann.  
  
 Inhaltstypen können mehrere\-andere Inhaltstypen erben. Die <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> können Sie mehrere Basistypen als den übergeordneten Elementen von einem bestimmten Inhaltstyp angeben.  
  
 Entwickler können eigene Inhaltstypen definieren und registrieren Sie sie mithilfe der <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Viele Editorfunktionen in Bezug auf einen bestimmten Inhaltstyp definiert werden, indem Sie mit der <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Beispielsweise können Editor Ränder, Details und Maushandler definiert werden, damit sie nur für Editoren gelten, die bestimmte Inhaltstypen anzeigen.  
  
###  <a name="textview"></a> Die Textansicht  
 Die Sicht Teil der Model\-View\-Controller \(MVC\)\-Muster definiert die Textansicht, die die Formatierung der anzeigen, Elemente wie z. B. die Bildlaufleiste, und die Einfügemarke. Alle Elemente der Visual Studio\-Editor basieren auf WPF.  
  
#### Text\-Ansichten  
 Die <xref:Microsoft.VisualStudio.Text.Editor.ITextView> \-Schnittstelle ist eine plattformunabhängige Darstellung angezeigt. Dient in erster Linie zur Text\-Dokumenten in einem Fenster angezeigt, aber es kann auch verwendet werden für andere Zwecke, z. B. in einer QuickInfo angezeigt.  
  
 Die Textansicht verweist auf verschiedene Arten von Textpuffer. Die <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> Eigenschaft bezieht sich auf ein <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> \-Objekt, das auf diese drei anderen Text\-Puffer verweist: im Datenpuffer ist der oberste Datenebene Puffer, den Bearbeitungspuffer, in welche Bearbeitung auftritt und visuellen Puffer, die der Puffer ist, in der Textansicht angezeigt wird.  
  
 Der Text wird formatiert basierend auf Klassifizierer ab, die die zugrunde liegenden Textpuffer zugeordnet sind, und versehen ist, durch die Verwendung der Randsteuerelement\-Anbieter, die die Textansicht selbst zugeordnet sind.  
  
#### Das Koordinatensystem des Text\-Ansicht  
 Das Koordinatensystem des Text\-Ansicht gibt die Positionen in der Textansicht an. In diesem Koordinatensystem der x Wert 0,0 entspricht dem linken Rand der Text angezeigt wird, und die y Wert 0,0 entspricht dem oberen Rand des Textes. Die x nimmt von links nach rechts zu koordinieren und die y nimmt von oben nach unten zu koordinieren.  
  
 Ein Viewport \(der Teil des Texts im Textfenster angezeigt\) kann nicht auf die gleiche Weise ein horizontaler Bildlauf durchgeführt werden wie ein vertikaler Bildlauf durchgeführt wird. Ein Viewport ist ein horizontaler Bildlauf durch die linke Koordinate geändert, sodass es in Bezug auf die Zeichenoberfläche verschiebt durchgeführt. Allerdings ein Viewport Bildlauf möglich vertikal nur durch ändern den zu rendernde Text, wodurch ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Ereignis ausgelöst wird.  
  
 Abstände im Koordinatensystem entsprechen den logischen Pixeln. Wenn die Text\-Rendering\-Oberfläche ohne eine Skalierungstransformation angezeigt wird, entspricht einer Einheit in den Textrendering\-Koordinatensystem ein Pixel auf dem Bildschirm.  
  
#### Seitenränder  
 Die <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> Schnittstelle stellt einen Rand und aktiviert die Steuerung der Sichtbarkeit der Rand\- und seine Größe. Es gibt vier vordefinierten Ränder, die "Top", "Left", "Right" und "Bottom" benannt werden und mit oben, unten, links oder rechts einer Ansicht verknüpft sind. Diese Ränder sind Container, die in denen anderen Rändern platziert werden können. Die\-Schnittstelle definiert Methoden, die Größe des Rands und die Sichtbarkeit von einem Rand. Ränder sind visuelle Elemente, die zusätzliche Informationen über die Textansicht bereitstellen, mit denen sie verbunden sind. Beispielsweise zeigt die Zeilennummer Rand Zeilennummern für die Textansicht. Der Symbolrand Zeigt Elemente der Benutzeroberfläche.  
  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Schnittstelle behandelt die Erstellung und Platzierung der Ränder. Ränder können in Bezug auf die anderen Rändern angeordnet sein. Höhere Priorität Ränder befinden sich näher anzuzeigende Text. Beispielsweise wird angezeigt, wenn es zwei linken Ränder, A und B gibt und Rand B hat eine geringere Priorität als Rand ein, Margin B auf der linken Seite des Rands A.  
  
#### Anzeigen des Hosts Text  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Schnittstelle enthält die Textansicht und alle angrenzenden Dekorationen, die die Ansicht, z. B. Bildlaufleisten begleiten. Anzeigen des Hosts Text enthält auch die Ränder, die einen Rahmen der Ansicht zugeordnet sind.  
  
#### Formatierter Text  
 In einer Textansicht angezeigte Text besteht aus <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Objekte. Eine Textzeile in der Textansicht entspricht jede Zeile Text anzeigen. Lange Zeilen im zugrunde liegenden Textpuffer können entweder teilweise verdeckt \(wenn Zeilenumbruch nicht aktiviert ist\) oder in mehreren Textansicht Zeilen aufgeteilt. Die <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Schnittstelle enthält Methoden und Eigenschaften für die Zuordnung zwischen Koordinaten und Zeichen, und die Details, die der Zeile zugeordnet werden können.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Objekte werden erstellt, mithilfe einer <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> Schnittstelle. Wenn Sie nur den Text, die derzeit in der Ansicht angezeigt wird befürchten, können Sie die Quelle die Formatierung ignorieren. Wenn Sie das Format des Texts interessiert sind, die nicht angezeigt wird, in der Ansicht \(z. B. zur Unterstützung von Rich\-Text Ausschneiden und Einfügen\), können Sie <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> zum Formatieren von Text in einem Textpuffer.  
  
 Die Textansicht formatiert eine <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> zu einem Zeitpunkt.  
  
## Editor\-Funktionen  
 Die Funktionen des Editors sind so gestaltet, dass die Definition der Funktion unabhängig von seiner Implementierung. Der Editor enthält die folgenden Features:  
  
-   Tags und Klassifizierer  
  
-   Details  
  
-   Projection  
  
-   Gliedern  
  
-   Maus und Tastatur Bindungen  
  
-   Vorgänge und primitive  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> Tags und Klassifizierer  
 Tags sind die Marker, die einen Textabschnitt zugeordnet sind. Sie können auf verschiedene Arten, z. B. dargestellt werden mithilfe von Farben für Text, unterstrichen, Grafiken oder Popups. Klassifizierer sind eine Art von Tags.  
  
 Andere Arten von Tags sind <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> für die Hervorhebung von Text <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> für Gliedern und <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> für Kompilierungsfehler.  
  
#### Klassifizierungstypen  
 Eine <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Schnittstelle eine äquivalenzklasse, die eine abstrakte Kategorie des Texts darstellt. Klassifizierungstypen können mehrere\-andere Klassifizierungstypen erben. Z. B. programming Language Klassifikationen gehören "Schlüsselwort", "Comment" und "Bezeichner", die alle von "Code" erben. Natürliche Sprache Klassifizierungstypen gehören "Nomen", "Verb" und "Adjektiv", die alle von "natürlicher Sprache" erben.  
  
#### Klassifizierungen  
 Eine Klassifizierung ist eine Instanz einer bestimmten Klassifizierung\-Typs in der Regel über einen Zeitraum von Text. Ein <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> wird verwendet, um eine Klassifizierung darstellen. Eine Klassifizierung Spanne kann als Bezeichnung betrachtet werden, die einen bestimmten Textabschnitt behandelt und weist das System, das für einen bestimmten Klassifizierungstyp dieses Textabschnitts ist.  
  
#### Klassifizierer  
 Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> ist ein Mechanismus, durch die Text in einen Satz von Klassifikationen unterbrochen. Klassifizierer müssen für bestimmte Inhaltstypen definiert und für bestimmte Textpuffer instanziiert werden. Clients müssen implementieren <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> textklassifizierung teilnehmen.  
  
#### Klassifizierung Aggregatoren  
 Ein Classifier\-Aggregator ist ein Mechanismus, der alle Klassifizierer für eine Textpuffer in nur einem Satz von Klassifikationen kombiniert. Beispielsweise konnte ein C\#\-Klassifizierung und einen englischsprachigen Klassifizierer Klassifikationen über einen Kommentar in einer C\#\-Datei erstellen. Betrachten Sie diesen Kommentar:  
  
```  
// This method produces a classifier  
```  
  
 Eine C\#\-Klassifizierung kann die gesamte Spanne als Kommentar Bezeichnung, und die Klassifizierung der englischen Sprache möglicherweise als "Verb" und "Method" als ein "Nomen" klassifizieren "erstellt". Der Aggregator erstellt eine Gruppe von nicht überlappenden Klassifikationen, und der Typ der Menge basiert auf alle Ihre Beiträge.  
  
 Ein Classifier\-Aggregator ist auch eine Classifier, da sie Text in einen Satz von Klassifikationen unterbrochen. Der Klassifizierungsaggregator stellt außerdem sicher, dass keine überlappenden Klassifikationen vorhanden sind und dass die Klassifikationen sortiert sind. Einzelne Klassifizierer sind ein Satz von Klassifikationen, in beliebiger Reihenfolge zurückgeben und überlappende in keiner Weise.  
  
#### Klassifizierung Formatierung und Text Codefarben  
 Formatieren von Text ist ein Beispiel für eine Funktion, die Klassifizierung von Texten erstellt wird. Es wird von der Ansicht Textebene verwendet, um die Anzeige von Text in einer Anwendung zu ermitteln. Die Formatierung Textbereich ist abhängig von WPF die logische Definition der Klassifikationen ist hingegen nicht.  
  
 Ein Klassifizierungsformat ist eine Reihe von Eigenschaften für einen bestimmten Klassifizierungstyp. Diese Formate werden aus dem Format des übergeordneten Elements den Klassifizierungstyp erben.  
  
 Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> ist eine Zuordnung von einem Klassifizierungstyp einer Reihe von Formatierungseigenschaften. Die Implementierung des gekachelten im Editor behandelt alle Exporte der Klassifizierung Formate.  
  
###  <a name="adornments"></a> Details  
 Details sind Grafikeffekte, die nicht direkt mit der Schriftart und Farbe der Zeichen in der Textansicht verknüpft sind. Z. B. die rote Wellenlinie unterstrichen, die verwendet wird, nicht Kompilieren von Code in vielen Programmiersprachen markiert ist, ein eingebettetes Zusatzelement und QuickInfos sind Popupfenster Zusatzelemente. Zusatzelemente abgeleitet sind <xref:System.Windows.UIElement> und implementieren Sie <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Zwei spezielle Arten von Adornment Tag sind die <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, für Zusatzelemente, die den gleichen Speicherplatz wie der Text in einer Ansicht zu belegen und die <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, für die Wellenlinie unterstrichen.  
  
 Eingebettete Zusatzelemente sind Grafiken, die Teil der formatierten Textansicht bilden. Sie sind in verschiedenen Schichten der Z\-Reihenfolge angeordnet. Bestehen die folgenden drei integrierte Ebenen: Text, der Einfügemarke und die Auswahl. Entwickler können jedoch weitere Ebenen definieren, und platzieren Sie sie in der Reihenfolge zueinander. Die drei Arten von eingebetteten Zusatzelemente sind Text relativ Zusatzelemente \(das Verschieben, wenn der Text bewegt und werden gelöscht, wenn der Text gelöscht wird\), Ansicht Relative Zusatzelemente \(die mit nicht\-Text\-Teilen der Ansicht zu tun haben\) und Besitzer\-gesteuerten Zusatzelemente \(der Entwickler muss die Platzierung verwalten\).  
  
 Popup Zusatzelemente sind Grafiken, die in einem kleinen Fenster über der Textansicht, z. B. QuickInfos angezeigt werden.  
  
###  <a name="projection"></a> Projection  
 Projektion ist ein Verfahren zum Erstellen einer anderen Art von Textpuffer, die nicht tatsächlich Text gespeichert, sondern stattdessen kombiniert Text aus anderen Textpuffer. Beispielsweise kann ein Projektionspuffer verwendet werden, zum Verketten von Text aus zwei anderen Puffer und zeigt das Ergebnis wird in nur einem Puffer oder Teile des Texts in einem Puffer auszublenden. Ein Projektionspuffer kann als einen Quellpuffer in einen anderen Projektionspuffer fungieren. Ein Satz von Puffern, die von der Projektion beziehen kann erstellt werden, um Text auf unterschiedliche Weise neu anordnen. \(Eine Gruppe wird auch ein *Pufferdiagramm*.\) Die Gliederungsfunktion des Visual Studio\-Text wird mithilfe eines Projektionspuffers zum Ausblenden des reduzierten Text implementiert, und der Visual Studio\-Editor für ASP.NET\-Seiten Projektion verwendet, um eingebettete Sprachen wie Visual Basic und c\# unterstützen.  
  
 Ein <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> wird erstellt, indem Sie mithilfe von <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Ein Projektionspuffer wird durch eine geordnete Sequenz von dargestellt <xref:Microsoft.VisualStudio.Text.ITrackingSpan> Objekte, die als bekanntermaßen *source Spannen*. Der Inhalt dieser Spannen werden als eine Folge von Zeichen dargestellt. Der Textpuffer aus der Quellspannen gezeichnet werden, werden mit dem Namen *Puffer source*. Clients eines Puffers Projektion ist nicht erforderlich, beachtet werden, dass es eine gewöhnliche Textpuffer unterscheidet.  
  
 Der Projektionspuffer Lauscht auf Text\-Change\-Ereignissen auf der Quellpuffer. Wenn der Text in einer Quelle umfassen Änderungen, Projektionspuffer die geänderten Text Koordinaten in eigenen Koordinaten und löst Ereignisse aus entsprechenden Text ändern. Betrachten Sie z. B. Quellpuffer A und B, die diesen Inhalt haben:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Wenn Projektionspuffer P aus zwei Textabschnitte, d. h. alle Puffer, die gültig ist, andere, die alle Puffer B enthält P den folgenden Inhalt:  
  
```  
P: ABCDEvwxyz  
```  
  
 Wenn die Teilzeichenfolge `xy` aus Puffer B gelöscht wird, und klicken Sie dann Puffer P löst ein Ereignis aus, der angibt, dass die Zeichen an Position 7 und 8 gelöscht wurden.  
  
 Der Projektionspuffer kann auch direkt bearbeitet werden. Es gibt Änderungen an die entsprechenden Quellpuffer weiter. Beispielsweise wird Puffer P an Position 6 \(die ursprüngliche Position der Buchstaben "V"\) eine Zeichenfolge eingefügt wird, die Einfügemarke in Puffer B an Position 1 weitergegeben.  
  
 Es gibt Einschränkungen auf die Quellspannen, die auf einen Projektionspuffer beitragen. Quellspannen dürfen nicht überlappen; eine Position in einem Projektionspuffer nicht mehr als einer Position in einem Quellpuffer zuordnen und ein Speicherort in einem Quellpuffer nicht mehr als einer Position in einem Projektionspuffer zuordnen. In der Quelle Puffer Beziehung sind keine Circularities zulässig.  
  
 Ereignisse werden ausgelöst, wenn der Satz von Puffern für eine Projektion Puffer ändert und wenn der Satz von Änderungen umfasst.  
  
 Ein Elisionspuffer ist eine besondere Art von Projektionspuffer. Es wird hauptsächlich für eine Gliederung und für Vorgänge, die erweitern und Reduzieren von Textblöcken. Ein Elisionspuffer basiert auf nur einen Quellpuffer und die Spannen im Elisionspuffer bestellt werden müssen, die gleiche wie diese in der Quellpuffer angeordnet werden.  
  
##### Der Pufferdiagramm  
 Die <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Schnittstelle ermöglicht die Zuordnung über Projektionspuffer in einem Diagramm dargestellt. Alle Textpuffer und Projektionspuffer werden in einem gerichteten Diagramm azyklisch, ähnlich wie die abstrakte Syntaxstruktur gesammelt, die durch einen Sprachcompiler erzeugt wird. Das Diagramm ist der oberste Puffer, Textpuffer werden kann definiert. Das Pufferdiagramm kann von einem Punkt im oberen Puffer zu einem Punkt in einem Quellpuffer oder aus einem Bereich im oberen Puffer einer Reihe von Bereichen in einem Quellpuffer zuordnen. Auf ähnliche Weise können sie ordnen Sie einen Punkt oder aus einem Quellpuffer an eine Stelle im oberen Puffer umfassen. Puffer Diagramme werden erstellt, mit der <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
##### Ereignisse und Projektionspuffer  
 Ein Projektionspuffer geändert wurde, werden die Änderungen aus dem Projektionspuffer in den Puffer gesendet, die davon abhängen. Wenn alle Puffer geändert wurden, werden Änderungsereignisse Puffer beginnend mit der tiefsten Puffer ausgelöst.  
  
###  <a name="outlining"></a> Gliedern  
 Das Gliedern ist die Möglichkeit zum Erweitern oder reduzieren unterschiedliche Textblöcke in einer Textansicht. Gliederung ist definiert als eine Art von <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, in der gleichen Weise wie Zusatzelemente definiert sind. Ein <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ist ein Tag, das einen Textbereich definiert, die erweitert oder reduziert werden können. Um Gliederung zu verwenden, importieren Sie die <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> zum Abrufen einer <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Die Gliederung\-Manager listet, reduziert und erweitert die verschiedenen Blöcken, die als dargestellt werden <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> \-Objekte und löst Ereignisse entsprechend.  
  
###  <a name="mousebindings"></a> Maus\-Bindungen  
 Maus Bindungen verknüpfen Maus mit verschiedenen Befehlen. Mithilfe von Maus Bindungen definiert eine <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, und mithilfe von Tastenkombinationen definiert eine <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automatisch alle Bindungen instanziiert und verbindet diese mit Mausereignisse in der Ansicht.  
  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> Schnittstelle enthält vorab zu verarbeiten und nach der Verarbeitung Ereignishandler für verschiedene Mausereignisse. Handle eines der Ereignisse, überschreiben Sie einige der Methoden in <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Editor\-Vorgänge  
 Editor\-Vorgänge können zum Automatisieren der Interaktion mit dem Editor, für das Skripting oder andere Zwecke verwendet werden. Können importiert werden die <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> für Access\-Vorgänge in einer bestimmten <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Dann können diese Objekte die Auswahl ändern, führen Sie einen Bildlauf der Ansicht oder verschiebt die Einfügemarke an verschiedenen Teilen der Ansicht.  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense unterstützt Anweisungsabschluss, Signaturhilfe \(auch bekannt als ParameterInfo\), QuickInfo und Glühbirnen.  
  
 Anweisungsabschluss bietet Popuplisten mit potenziellen Abschlüssen für Methodennamen, XML und andere Elemente zu codieren oder Markup. Im Allgemeinen wird eine Benutzeraktion eine Sitzung Abschluss aufgerufen. Die Sitzung wird die Liste der potenziellen Abschlüssen, und der Benutzer auswählen, oder schließen Sie die Liste kann. Die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> ist verantwortlich für das Erstellen und Auslösen der <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. Die <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> berechnet die <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> Abschluss Elemente für die Sitzung.  
  
## Siehe auch  
 [Language Service und Erweiterungspunkte\-Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Imports\-Editor](../extensibility/editor-imports.md)