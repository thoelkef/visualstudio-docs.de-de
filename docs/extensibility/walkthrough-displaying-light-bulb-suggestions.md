---
title: 'Exemplarische Vorgehensweise: Displaying Light Bulb Suggestions | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1ce64b3fe8d41d1ceb865555d93e6e464b25fb42
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935007"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Exemplarische Vorgehensweise: Anzeigen einer Glühbirne gekennzeichneten Vorschlägen
Glühbirnen sind Symbole in Visual Studio-Editor, die erweitert werden, um einen Satz von Aktionen, z. B. Fehlerbehebungen für Probleme identifiziert, die von der integrierten Code-Analyzer oder Umgestaltung von Code anzuzeigen.  
  
 In der Visual c# und Visual Basic-Editoren können Sie auch das .NET Compiler Platform ("Roslyn") verwenden, schreiben und Packen Ihren eigenen Code-Analyzer mit Aktionen, die automatisch angezeigt werden Glühbirnen. Weitere Informationen finden Sie unter:  
  
- [How To: Schreiben einer C# Diagnose, und Korrigieren von Code](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
- [How To: Schreiben Sie eine Visual Basic-Diagnose und Codefix](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
  Andere Sprachen wie C++ bieten auch Glühbirnen für einige schnellen Aktion verwenden, z. B. einen Vorschlag zum Erstellen einer Stubimplementierung dieser Funktion.  
  
  Hier ist, wie eine Glühbirne aussieht. In einem Visual Basic oder Visual C#-Projekt wird eine rote Wellenlinie unter dem Namen einer Variablen angezeigt, wenn er ungültig ist. Wenn Sie den Mauszeiger über einem ungültigen Bezeichner, wird Sie neben dem Cursor eine Glühbirne angezeigt.  
  
  ![Glühbirne](../extensibility/media/lightbulb.png "Glühbirne")  
  
  Wenn Sie den Pfeil nach unten durch die Glühbirne klicken, wird eine Reihe von empfohlenen Aktionen sowie eine Vorschau der ausgewählten Aktion angezeigt. In diesem Fall wird die Änderungen, die an Ihrem Code vorgenommen werden, wenn Sie den Vorgang auszuführen.  
  
  ![Light Bulb-Vorschau](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
  Glühbirnen können Sie Ihre eigenen Vorschlägen für Aktionen bieten. Beispielsweise können Sie Aktionen zum Öffnen von geschweiften Klammern in eine neue Zeile zu verschieben, oder verschieben Sie sie am Ende der vorherigen Zeile bereitstellen. Die folgende exemplarische Vorgehensweise veranschaulicht, wie erstellen Sie eine Glühbirne, die angezeigt wird, für das aktuelle Wort und verfügt über zwei empfohlene Aktionen beinhaltet: **In Großschreibung konvertieren** und **in Kleinbuchstaben umwandeln**.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen Sie ein Projekt Managed Extensibility Framework (MEF)  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `LightBulbTest`.  
  
2.  Hinzufügen einer **Editor Klassifizierer** Elementvorlage zum Projekt. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
4.  Fügen Sie den folgenden Verweis auf das Projekt, und legen **lokale Kopie** zu `False`:  
  
     *Microsoft.VisualStudio.Language.Intellisense*  
  
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
  
## <a name="implement-the-light-bulb-source-provider"></a>Implementieren der Quellenanbieter Glühbirne  
  
1.  In der *LightBulbTest.cs* Klassendatei, löschen Sie die LightBulbTest-Klasse. Fügen Sie eine Klasse, die mit dem Namen **TestSuggestedActionsSourceProvider** implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exportieren Sie es mit dem Namen **Test vorgeschlagene Aktionen** und <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text".  
  
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
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> -Methode zur Rückgabe einer <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> Objekt. Die Quelle wird im nächsten Abschnitt erläutert.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null || textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implement-the-isuggestedactionsource"></a>Implementieren der ISuggestedActionSource  
 Die empfohlene Aktion-Quelle ist verantwortlich für das Sammeln der Satz von Vorschlägen für Aktionen, und sie in den richtigen Kontext hinzufügen. In diesem Fall der Kontext ist das aktuelle Wort, und die vorgeschlagenen Aktionen sind **UpperCaseSuggestedAction** und **LowerCaseSuggestedAction**, die im folgenden Abschnitt erläutert wird.  
  
1.  Fügen Sie eine Klasse **TestSuggestedActionsSource** implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Fügen Sie private, schreibgeschützte Felder, für der Quellenanbieter empfohlene Aktion, die den Textpuffer und die Textansicht.  
  
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
  
4.  Fügen Sie eine private Methode, die das Wort zurückgibt, die derzeit unter dem Cursor hinzu. Die folgende Methode sucht nach der aktuellen Position des Cursors und fordert die Textstruktur-Navigator das Extent des Worts. Wenn der Cursor auf ein Wort, ist die <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> ist in der Out-Parameter zurückgegeben, andernfalls die `out` Parameter `null` und die Methode gibt `false`.  
  
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
  
5.  Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>-Methode. Der Editor ruft diese Methode, um zu ermitteln, ob die Glühbirne anzuzeigen. Dieser Aufruf erfolgt häufig, z. B., wenn der Cursor über mehrere Zeilen in eine andere verschoben wird, oder wenn der Mauszeiger auf einen Fehlerschnörkel loszuwerden zeigt. Es ist damit können andere UI-Vorgänge ausführen, während der Arbeit mit dieser Methode ist asynchron. Diese Methode muss in den meisten Fällen führen einige Analyse und Analyse von der aktuellen Zeile, aus, damit die Verarbeitung einige Zeit dauern kann.  
  
     In dieser Implementierung wird es Ruft die <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> und bestimmt, ob der Block wichtig ist, z. B., ob sie den Text als Leerzeichen verfügt.  
  
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
    >  Sie sollten sicherstellen, dass die Implementierungen der `HasSuggestedActionsAsync()` und `GetSuggestedActions()` sind konsistent; die, wenn `HasSuggestedActionsAsync()` gibt `true`, klicken Sie dann `GetSuggestedActions()` müssen einige Aktionen angezeigt. In vielen Fällen `HasSuggestedActionsAsync()` wird aufgerufen, kurz bevor `GetSuggestedActions()`, aber dies ist nicht immer der Fall. Wenn der Benutzer die Glühbirne Aktionen durch Drücken von ruft z. B. (**STRG +** .) nur `GetSuggestedActions()` aufgerufen wird.  
  
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
  
8.  Um die Implementierung abzuschließen, fügen Sie Implementierungen für die `Dispose()` und `TryGetTelemetryId()` Methoden. Sie nicht möchten, führen Sie die Telemetriedaten, daher Rückgabe `false` , und legen Sie die GUID auf `Empty`.  
  
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
  
## <a name="implement-light-bulb-actions"></a>Glühbirne Aktionen implementiert  
  
1.  Fügen Sie im Projekt einen Verweis auf *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* und **lokale Kopie** zu `False`.  
  
2.  Erstellen Sie zwei Klassen, die erste mit dem Namen `UpperCaseSuggestedAction` und die zweite mit dem Namen `LowerCaseSuggestedAction`. Beide Klassen implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Beide Klassen sind bis auf eine Ausnahme identisch: Die eine ruft <xref:System.String.ToUpper%2A> und die andere <xref:System.String.ToLower%2A> auf. In den folgenden Schritten wird nur die Klasse für die Umwandlung in Großbuchstaben behandelt; Sie müssen aber beide Klassen implementieren. Verwenden Sie diese Schritte als Muster für die Implementierung der Aktion zur Umwandlung in Kleinbuchstaben.  
  
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
    private string m_upper;  
    private string m_display;  
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
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> Methode, sodass die It die Vorschau der Aktion wird angezeigt.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementieren der <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> Methode so, dass die It eine leere zurückgegeben <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> Enumeration.  
  
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
  
9. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>-Methode, indem Sie den Text im Bereich durch entsprechende Großbuchstaben ersetzen.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Die Glühbirne Aktion **Invoke** Methode nicht erwartet, dass die Benutzeroberfläche anzuzeigen. Wenn die neue Benutzeroberfläche (z. B. ein Dialogfeld "Preview" oder "Auswahl") die Aktion angezeigt, die Benutzeroberfläche direkt aus nicht anzeigen der **Invoke** Methode jedoch planen Sie stattdessen die Benutzeroberfläche angezeigt wird, nach der Rückgabe vom **Invoke**.  
  
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
  
11. Vergessen Sie nicht das gleiche tun für `LowerCaseSuggestedAction` ändern den Anzeigetext zu "konvertieren"{0}"in Kleinbuchstaben" und der Aufruf <xref:System.String.ToUpper%2A> zu <xref:System.String.ToLower%2A>.  
  
## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe LightBulbTest, und führen Sie es in der experimentellen Instanz.  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie Text ein. Daraufhin sollte eine Glühbirne auf der linken Seite des Texts.  
  
     ![die Glühbirne testen](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Zeigen Sie auf die Glühbirne. Sie sollten einen Pfeil nach unten sehen.  
  
5.  Wenn Sie die Glühbirne klicken, sollten zwei empfohlene Aktionen angezeigt, zusammen mit der Vorschau der ausgewählten Aktion.  
  
     ![Erweiterte Glühbirne testen](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Wenn Sie die erste Aktion klicken, sollte der gesamte Text im aktuellen Wort in Großbuchstaben konvertiert werden. Wenn Sie die zweite Aktion klicken, sollte der gesamte Text in Kleinbuchstaben konvertiert werden.  
