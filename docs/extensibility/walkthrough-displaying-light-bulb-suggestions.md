---
title: "Exemplarische Vorgehensweise: Anzeigen von Gl&#252;hbirne Vorschl&#228;ge | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Anzeigen von Gl&#252;hbirne Vorschl&#228;ge
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Glühbirnen sind in der Visual Studio\-Editor verwendeten Symbole, die erweitert werden, um eine Reihe von Aktionen angezeigt, z. B. Korrekturen für Probleme, die durch die integrierte Code\-Analyzer oder refactoring von Quellcodes identifiziert.  
  
 In Visual c\# und Visual Basic\-Editor können Sie auch .NET Compiler Platform \("Roslyn"\) verwenden, schreiben und Verpacken Ihrer eigenen Code\-Analyzer mit Aktionen, die automatisch Glühbirnen anzeigen. Weitere Informationen finden Sie unter:  
  
-   [Gewusst wie: Schreiben einer C\#\-Diagnose\- und Codefix](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Gewusst wie: Schreiben einer Visual Basic\-Diagnose\- und Codefix](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Andere Sprachen wie C\+\+ sind auch Glühbirnen für einige schnelle Aktionen, z. B. einen Vorschlag für das Erstellen einer Stubimplementierung dieser Funktion.  
  
 Hier ist eine Glühbirne aussieht. In einem Visual Basic\- oder Visual c\#\-Projekt wird eine rote Wellenlinie unter einem Variablennamen angezeigt, wenn sie ungültig ist. Wenn Sie die Maus über die ungültige ID, wird neben dem Cursor eine Glühbirne angezeigt.  
  
 ![light bulb](../extensibility/media/lightbulb.png "LightBulb")  
  
 Wenn Sie auf den Pfeil nach unten durch die Glühbirne klicken, wird eine Vorschau der ausgewählten Aktion vorgeschlagene Aktionen angezeigt. In diesem Fall wird die Änderungen, die mit Ihrem Code vorgenommen werden, wenn Sie die Aktion ausführen.  
  
 ![light bulb preview](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Glühbirnen können eigene vorgeschlagenen Aktionen bereitgestellt. Beispielsweise könnten Sie Aktionen zum Öffnen von geschweiften Klammern in einer neuen Zeile zu verschieben, oder verschieben Sie sie am Ende der vorhergehenden Zeile angeben. Die folgenden exemplarischen Vorgehensweise erstellen Sie eine Glühbirne, die angezeigt wird, auf das aktuelle Wort und verfügt über zwei Aktionen empfohlen: **in Großschreibung konvertieren** und **in Kleinbuchstaben umwandeln**.  
  
## Erforderliche Komponenten  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts \(Managed Extensibility Framework\)  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt. \(In der **Neues Projekt** Dialogfeld **Visual c\# \/ Erweiterbarkeit**, dann **VSIX\-Projekt**.\) Nennen Sie die Projektmappe `LightBulbTest`.  
  
2.  Hinzufügen einer **Editor Klassifizierer** Elementvorlage zum Projekt. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie den folgenden Verweis auf das Projekt, und legen **lokale Kopie** auf `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Fügen Sie eine neue Klassendatei hinzu, und nennen Sie sie **LightBulbTest**.  
  
6.  Fügen Sie die folgende using\-Anweisungen:  
  
    ```c#  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## Implementieren die Glühbirne Quellenanbieter  
  
1.  Löschen Sie in der Klassendatei LightBulbTest.cs die LightBulbTest\-Klasse. Fügen Sie eine Klasse mit dem Namen **TestSuggestedActionsSourceProvider** implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exportieren Sie es mit dem Namen **Test vorgeschlagene Aktionen** und einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text".  
  
    ```c#  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Importieren Sie in der Quelle Provider\-Klasse in der <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> und als eine Eigenschaft hinzuzufügen.  
  
    ```c#  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> Methode zum Zurückgeben einer <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> Objekt. Die Quelle im nächsten Abschnitt wird erläutert.  
  
    ```c#  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## Implementieren die ISuggestedActionSource  
 Die empfohlene Aktion Quelle ist verantwortlich für das Sammeln der Satz von empfohlenen Maßnahmen und im richtigen Kontext hinzufügen. In diesem Fall ist des Kontexts des aktuellen Worts und die entsprechenden Maßnahmen sind **UpperCaseSuggestedAction** und **LowerCaseSuggestedAction**, die wir im folgenden Abschnitt erläutert wird.  
  
1.  Fügen Sie eine Klasse **TestSuggestedActionsSource** implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```c#  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Fügen Sie private schreibgeschützte Felder für vorgeschlagene Aktion Quellenanbieter, Textpuffer und der Textansicht.  
  
    ```c#  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Fügen Sie einen Konstruktor, der die privaten Felder festlegt.  
  
    ```c#  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Fügen Sie eine private Methode, die das Wort zurückgibt, das derzeit unter dem Cursor befindet. Die folgende Methode sucht nach der aktuellen Position des Cursors und fordert den Text Struktur Navigator für das Ausmaß des Worts. Wenn der Cursor auf einem Wort ist der <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> an den Out\-Parameter zurückgegeben, andernfalls die `out` Parameter ist `null` und die Methode gibt `false`.  
  
    ```c#  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>\-Methode. Der Editor ruft diese Methode zu ermitteln, ob die Glühbirne anzuzeigen. Dieser Aufruf wird beispielsweise sehr häufig durchgeführt, wenn der Cursor über mehrere Zeilen in eine andere verschoben wird, oder wenn der Mauszeiger auf einen Fehler Wellenlinie zeigt. Es ist damit können andere UI\-Vorgänge ausführen, während diese Methode arbeitet asynchron. In den meisten Fällen, die diese Methode einige analysieren und die Analyse der aktuellen Zeile ausführen muss, sodass die Verarbeitung einige Zeit in Anspruch.  
  
     In unserer Implementierung ruft es asynchron die <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> und bestimmt, ob der Block berücksichtigt, d. h., ob es sich um Text als Leerzeichen verfügt.  
  
    ```c#  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> \-Methode, die gibt ein Array von <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> \-Objekten, die die verschiedenen enthalten <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> Objekte. Diese Methode wird aufgerufen, wenn die Glühbirne erweitert wird.  
  
    > [!WARNING]
    >  Sie sollten sicherstellen, dass die Implementierung des `HasSuggestedActionsAsync()` und `GetSuggestedActions()` sind konsistent; die, wenn `HasSuggestedActionsAsync()` gibt `true`, dann `GetSuggestedActions()` müssen einige Aktionen angezeigt. In vielen Fällen `HasSuggestedActionsAsync()` wird aufgerufen, unmittelbar vor dem `GetSuggestedActions()`, dies ist jedoch nicht immer der Fall. Beispielsweise, wenn der Benutzer durch Drücken der Glühbirne Aktionen aufruft \(STRG \+.\) nur `GetSuggestedActions()` aufgerufen wird.  
  
    ```c#  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Definieren einer `SuggestedActionsChanged` Ereignis.  
  
    ```c#  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Fügen Sie zum Abschließen der Implementierungstyps Implementierungen für die `Dispose()` und `TryGetTelemetryId()` Methoden. Wir möchten Telemetriedaten führen, also gibt "false" und die GUID auf leer festgelegt.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## Glühbirne Aktionen implementieren  
  
1.  Fügen Sie im Projekt einen Verweis auf Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll und **lokale Kopie** auf `False`.  
  
2.  Erstellen Sie zwei Klassen, die zuerst mit dem Namen `UpperCaseSuggestedAction` und die zweite mit dem Namen `LowerCaseSuggestedAction`. Beide Klassen implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```c#  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Beide Klassen sind gleich, außer dass eine ruft <xref:System.String.ToUpper%2A> und die anderen Aufrufe <xref:System.String.ToLower%2A>. In den folgenden Schritten wird nur die Klasse für die Umwandlung in Großbuchstaben behandelt; Sie müssen aber beide Klassen implementieren. Verwenden Sie diese Schritte als Muster für die Implementierung der Aktion zur Umwandlung in Kleinbuchstaben.  
  
3.  Fügen Sie die folgende using\-Anweisungen für diese Klassen:  
  
    ```c#  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Deklarieren Sie einen Satz privater Felder.  
  
    ```c#  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Fügen Sie einen Konstruktor hinzu, der die Felder festlegt.  
  
    ```c#  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> Methode, sodass die It die Aktion Vorschau wird angezeigt.  
  
    ```c#  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> Methode, sodass diese eine leere zurückgegeben <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> Enumeration.  
  
    ```c#  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implementieren Sie die Eigenschaften wie folgt:  
  
    ```c#  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> \-Methode durch Ersetzen von Text in der Folge dessen Entsprechung in Großbuchstaben.  
  
    ```c#  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Die Glühbirne Aktion **Invoke** wird nicht erwartet, dass die Benutzeroberfläche angezeigt werden.  Wenn die Aktion Neue Benutzeroberfläche \(z. B. ein Dialogfeld Vorschau oder Auswahl\) gesetzt wird, soll die Benutzeroberfläche direkt aus der **Invoke** Methode aber stattdessen die Benutzeroberfläche angezeigt wird, nach der Rückgabe vom **Invoke**.  
  
10. Um die Implementierung abzuschließen, fügen Sie die `Dispose()` und `TryGetTelemetryId()` Methoden.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. Vergessen Sie nicht, das gleiche tun für `LowerCaseSuggestedAction` "{0}" in Kleinschreibung konvertieren"und der Aufruf ändern <xref:System.String.ToUpper%2A> auf <xref:System.String.ToLower%2A>.  
  
## Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe LightBulbTest, und führen Sie es in der experimentellen Instanz.  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie Text ein. Daraufhin sollte eine Glühbirne auf der linken Seite des Texts.  
  
     ![test the light bulb](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Zeigen Sie auf die Glühbirne. Daraufhin sollte einen Pfeil nach unten.  
  
5.  Wenn Sie die Glühbirne klicken, sollte zwei vorgeschlagene Aktionen zusammen mit der Vorschau der ausgewählten Aktion angezeigt werden.  
  
     ![test light bulb, expanded](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Wenn Sie auf die erste Aktion klicken, sollte der gesamte Text im aktuellen Wort in Großbuchstaben umgewandelt werden. Wenn Sie auf die zweite Aktion klicken, sollte der gesamte Text im aktuellen Wort in Kleinbuchstaben umgewandelt werden.