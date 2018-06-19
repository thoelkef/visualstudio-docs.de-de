---
title: 'Exemplarische Vorgehensweise: Anzeigen von Glühbirne Vorschläge | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 750e3b0915478b4249ce8db1ac294c1f2a3006f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148700"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Exemplarische Vorgehensweise: Anzeigen von Glühbirne-Vorschläge
Glühbirnen sind Symbole, die in der Visual Studio-Editor verwendet, die erweitert werden, um eine Reihe von Aktionen anzuzeigen, z. B. Korrekturen für Probleme, die von den integrierten Code-Analyzer oder refactoring von Code.  
  
 In den Visual c# und Visual Basic-Editoren können Sie auch die .NET Compiler Platform ("Roslyn") verwenden, zu schreiben und Packen Sie Ihre eigenen Code-Analyzer mit Aktionen, die Glühbirnen automatisch angezeigt. Weitere Informationen finden Sie unter:  
  
-   [Gewusst wie: Schreiben einer C#-Diagnose- und Codekorrektur](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Gewusst wie: Schreiben einer Visual Basic-Diagnose- und Codekorrektur](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Andere Sprachen wie C++ bieten auch Glühbirnen für einige schnellen Aktionen, z. B. einen Vorschlag für das Erstellen einer Stubimplementierung dieser Funktion.  
  
 Im folgenden wird eine Glühbirne aussieht. In einem Visual Basic- oder Visual C#-Projekt wird eine rote Wellenlinie unter einen Variablennamen angezeigt, wenn er ungültig ist. Wenn Sie die Maus über die ungültige ID, wird neben dem Cursor eine Glühbirne angezeigt.  
  
 ![Glühbirne](../extensibility/media/lightbulb.png "Glühbirne")  
  
 Wenn Sie den Pfeil nach unten durch die Glühbirne klicken, wird eine Reihe von vorgeschlagenen Aktionen sowie eine Vorschau der ausgewählten Aktion angezeigt. In diesem Fall zeigt es die Änderungen, die in Ihrem Code vorgenommen werden, wenn Sie die Aktion ausführen.  
  
 ![Glühbirne mit Vorschau](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Glühbirnen können Sie eigene vorgeschlagenen Aktionen bereitzustellen. Beispielsweise könnten Sie anhand geeigneter Aktionen zum Verschieben, öffnen geschweifte Klammern in einer neuen Zeile oder ans Ende der vorherigen Zeile. Die folgende exemplarische Vorgehensweise veranschaulicht das Erstellen Sie einer Glühbirne, die angezeigt wird, für das aktuelle Wort und verfügt über zwei empfohlene Aktionen beinhaltet: **in Großschreibung konvertieren** und **in Kleinbuchstaben umwandeln**.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekts**.) Nennen Sie die Projektmappe `LightBulbTest`.  
  
2.  Hinzufügen einer **Editor Klassifizierer** Elementvorlage zum Projekt. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie den folgenden Verweis auf das Projekt, und legen **lokale Kopie** auf `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Fügen Sie eine neue Klassendatei hinzu, und nennen Sie sie **LightBulbTest**.  
  
6.  Fügen Sie die folgenden using-Anweisungen:  
  
    ```csharp  
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
  
## <a name="implementing-the-light-bulb-source-provider"></a>Implementieren den Quellenanbieter Glühbirne  
  
1.  Löschen Sie in der Klassendatei LightBulbTest.cs die LightBulbTest-Klasse. Fügen Sie eine Klasse mit dem Namen **TestSuggestedActionsSourceProvider** implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exportieren Sie es mit einem Namen eines **vorgeschlagene Aktionen vom Test** und ein <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text".  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Importieren Sie in der Quelle Provider-Klasse, die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> und als eine Eigenschaft hinzufügen.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> -Methode zur Rückgabe einer <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> Objekt. Die Quelle im nächsten Abschnitt wird erläutert.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>Implementieren die ISuggestedActionSource  
 Die empfohlene Aktion-Quelle ist verantwortlich für den Satz von vorgeschlagene Aktionen sammeln und diese im entsprechenden Kontext hinzufügen. In diesem Fall der Kontext für das aktuelle Wort ist und die empfohlenen Aktionen sind **UpperCaseSuggestedAction** und **LowerCaseSuggestedAction**, die wir im folgenden Abschnitt erläutert.  
  
1.  Fügen Sie eine Klasse **TestSuggestedActionsSource** implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Fügen Sie private schreibgeschützte Felder für Quellenanbieter empfohlene Aktion, die den Textpuffer und Textansicht hinzu.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Fügen Sie einen Konstruktor, der die privaten Felder festlegt.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Fügen Sie eine private Methode, die das Wort zurückgibt, das sich derzeit unter dem Cursor befindet. Die folgende Methode sucht an der aktuellen Position des Cursors und fordert der Textstruktur-Navigator für das Ausmaß des Worts. Wenn der Cursor in ein Wort, das <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> ist in der Out-Parameter zurückgegeben, andernfalls die `out` Parameter ist `null` und die Methode gibt `false`.  
  
    ```csharp  
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
  
5.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>-Methode. Der Editor ruft diese Methode zu ermitteln, ob die Glühbirne anzuzeigen. Dieser Aufruf erfolgt häufig, z. B. wenn der Cursor aus einer Zeile in einen anderen bewegt wird, oder wenn die Maus bewegt wird, auf eine Wellenlinie Fehler. Es ist damit können andere UI-Vorgänge auf durchführen, während diese Methode arbeitet asynchron. In den meisten Fällen wird, die diese Methode einige analysieren und die Analyse der aktuellen Zeile ausführen muss, kann die Verarbeitung also einige Zeit dauern.  
  
     In unserer Implementierung ruft es asynchron die <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> und bestimmt, ob der Block signifikant sind, d. h., ob es sich um Text als Leerzeichen verfügt.  
  
    ```csharp  
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
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> Methode, die ein Array von zurückgibt <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> Objekte, die die verschiedenen enthalten <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> Objekte. Diese Methode wird aufgerufen, wenn die Glühbirne erweitert wird.  
  
    > [!WARNING]
    >  Sie sollten sicherstellen, dass die Implementierungen von `HasSuggestedActionsAsync()` und `GetSuggestedActions()` sind konsistent; die, sofern `HasSuggestedActionsAsync()` gibt `true`, klicken Sie dann `GetSuggestedActions()` müssen einige Aktionen angezeigt. In vielen Fällen `HasSuggestedActionsAsync()` wird aufgerufen, kurz bevor `GetSuggestedActions()`, dies ist jedoch nicht immer die Groß-/Kleinschreibung. Angenommen, wenn der Benutzer durch Drücken der Glühbirne Aktionen aufruft (STRG +.) nur `GetSuggestedActions()` aufgerufen wird.  
  
    ```csharp  
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
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Um die Implementierung zu abzuschließen, fügen Sie die Implementierungen für die `Dispose()` und `TryGetTelemetryId()` Methoden. Wir möchten nicht, führen Sie Telemetrie, also "false" zurückgeben und die GUID auf leer festgelegt.  
  
    ```csharp  
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
  
## <a name="implementing-light-bulb-actions"></a>Implementieren von Aktionen für Glühbirne  
  
1.  Fügen Sie im Projekt einen Verweis auf Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll und **lokale Kopie** auf `False`.  
  
2.  Erstellen Sie zwei Klassen, die erste mit dem Namen `UpperCaseSuggestedAction` und die zweite mit dem Namen `LowerCaseSuggestedAction`. Beide Klassen implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Beide Klassen sind bis auf eine mit dem Unterschied, dass eine ruft <xref:System.String.ToUpper%2A> und die andere <xref:System.String.ToLower%2A>. In den folgenden Schritten wird nur die Klasse für die Umwandlung in Großbuchstaben behandelt; Sie müssen aber beide Klassen implementieren. Verwenden Sie diese Schritte als Muster für die Implementierung der Aktion zur Umwandlung in Kleinbuchstaben.  
  
3.  Fügen Sie die folgenden using-Anweisungen für diese Klassen:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Deklarieren Sie einen Satz privater Felder.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Fügen Sie einen Konstruktor hinzu, der die Felder festlegt.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> Methode, sodass die It die Aktion Vorschau wird angezeigt.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> Methode, sodass dieser eine leere zurückgegeben <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> Enumeration.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implementieren Sie die Eigenschaften wie folgt:  
  
    ```csharp  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
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
  
9. Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> Methode, indem Sie den Text im Bereich durch entsprechende Großbuchstaben ersetzen.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Die Glühbirne Aktion **Invoke** Methode erwartet keine Benutzeroberfläche angezeigt werden.  Wenn Ihre Aktion die neue Benutzeroberfläche (z. B. ein Dialogfeld Vorschau oder Auswahl) aufzurufen, die Benutzeroberfläche direkt aus nicht anzeigen der **Invoke** Methode aber stattdessen planen, um die Benutzeroberfläche anzuzeigen, nach der Rückgabe vom **Invoke**.  
  
10. Um die Implementierung abzuschließen, fügen Sie der `Dispose()` und `TryGetTelemetryId()` Methoden.  
  
    ```csharp  
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
  
11. Vergessen Sie nicht dasselbe, was zum `LowerCaseSuggestedAction` ändern den Anzeigetext auf "" {0}"in Kleinschreibung konvertieren" und der Aufruf <xref:System.String.ToUpper%2A> auf <xref:System.String.ToLower%2A>.  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die LightBulbTest-Projektmappe, und führen Sie sie in der experimentellen Instanz.  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie Text ein. Daraufhin sollte eine Glühbirne auf der linken Seite des Texts.  
  
     ![die Glühbirne testen](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Zeigen Sie auf die Glühbirne. Daraufhin sollte einen Pfeil nach unten.  
  
5.  Wenn Sie die Glühbirne klicken, sollten zwei empfohlene Aktionen zusammen mit der Vorschau der ausgewählten Aktion angezeigt.  
  
     ![Erweiterte Glühbirne testen](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Wenn Sie auf die erste Aktion klicken, sollte der gesamte Text im aktuellen Wort in Großbuchstaben umgewandelt werden. Wenn Sie auf die zweite Aktion klicken, sollte der gesamte Text im aktuellen Wort in Kleinbuchstaben umgewandelt werden.  
  