---
title: 'Exemplarische Vorgehensweise: Anzeigen von Glühbirnenvorschlägen | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697470"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Walkthrough: Anzeigen von Glühbirnenvorschlägen
Glühbirnen sind Symbole im Visual Studio-Editor, die erweitert werden, um eine Reihe von Aktionen anzuzeigen, z. B. Korrekturen für Probleme, die von den integrierten Codeanalysatoren oder der Codeumgestaltung identifiziert wurden.

 In den Visual C- und Visual Basic-Editoren können Sie auch die .NET Compiler Platform ("Roslyn") verwenden, um eigene Codeanalysatoren mit Aktionen zu schreiben und zu verpacken, die Glühbirnen automatisch anzeigen. Weitere Informationen finden Sie unter:

- [Gewusst wie: Schreiben einer C-Diagnose- und Codekorrektur](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Gewusst wie: Schreiben einer Visual Basic-Diagnose und Codekorrektur](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Andere Sprachen wie C++ stellen auch Glühbirnen für einige schnelle Aktionen bereit, z. B. einen Vorschlag zum Erstellen einer Stubimplementierung dieser Funktion.

  So sieht eine Glühbirne aus. In einem Visual Basic- oder Visual C-Projekt wird eine rote Wellenlinie unter einem Variablennamen angezeigt, wenn sie ungültig ist. Wenn Sie mit der Maus über den ungültigen Bezeichner fahren, wird eine Glühbirne in der Nähe des Cursors angezeigt.

  ![Glühbirne](../extensibility/media/lightbulb.png "Glühbirne")

  Wenn Sie auf den Pfeil nach unten durch die Glühbirne klicken, wird eine Reihe von vorgeschlagenen Aktionen zusammen mit einer Vorschau der ausgewählten Aktion angezeigt. In diesem Fall werden die Änderungen angezeigt, die an Ihrem Code vorgenommen werden, wenn Sie die Aktion ausführen.

  ![Vorschau für Glühbirne](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Sie können Glühbirnen verwenden, um Ihre eigenen vorgeschlagenen Aktionen bereitzustellen. Sie können z. B. Aktionen bereitstellen, um öffnende geschweifte Geschwenen in eine neue Zeile zu verschieben oder sie an das Ende der vorherigen Zeile zu verschieben. Die folgende exemplarische Vorgehensweise zeigt, wie Sie eine Glühbirne erstellen, die im aktuellen Wort angezeigt wird und zwei vorgeschlagene Aktionen enthält: Konvertieren in **Großbuchstaben** und **Konvertieren in Kleinbuchstaben**.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)

1. Erstellen Sie ein Projekt von C-VSIX. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C/ Erweiterbarkeit**aus, dann **VSIX-Projekt**.) Benennen Sie `LightBulbTest`die Lösung .

2. Fügen Sie dem Projekt eine **Editor-Klassifierelementvorlage** hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

4. Fügen Sie den folgenden Verweis zum Projekt `False`hinzu, und legen Sie Lokal **kopieren** auf:

     *Microsoft.VisualStudio.Language.Intellisense*

5. Fügen Sie eine neue Klassendatei hinzu und nennen Sie sie **LightBulbTest**.

6. Fügen Sie die folgenden using-Direktiven hinzu:

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

## <a name="implement-the-light-bulb-source-provider"></a>Implementieren des Glühbirnenquellenanbieters

1. Löschen *Sie* in der LightBulbTest.cs-Klassendatei die LightBulbTest-Klasse. Fügen Sie eine Klasse mit dem <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>Namen **TestSuggestedActionsSourceProvider** hinzu, die implementiert. Exportieren Sie es mit einem Namen <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> der **vorgeschlagenen Testaktionen** und einem von "Text".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Importieren Sie die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> innerhalb der Quellanbieterklasse, und fügen Sie sie als Eigenschaft hinzu.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> Methode, um ein Objekt zurückzugeben. Die Quelle wird im nächsten Abschnitt erläutert.

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
 Die vorgeschlagene Aktionsquelle ist dafür verantwortlich, den Satz der vorgeschlagenen Aktionen zu sammeln und im richtigen Kontext hinzuzufügen. In diesem Fall ist der Kontext das aktuelle Wort, und die vorgeschlagenen Aktionen sind **UpperCaseSuggestedAction** und **LowerCaseSuggestedAction**, die im folgenden Abschnitt erläutert werden.

1. Fügen Sie eine Klasse **TestSuggestedActionsSource** hinzu, die <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>implementiert.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Fügen Sie private, schreibgeschützte Felder für den vorgeschlagenen Aktionsquellenanbieter, den Textpuffer und die Textansicht hinzu.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Fügen Sie einen Konstruktor hinzu, der die privaten Felder festlegt.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Fügen Sie eine private Methode hinzu, die das Wort zurückgibt, das sich derzeit unter dem Cursor befindet. Die folgende Methode betrachtet die aktuelle Position des Cursors und fragt den Textstrukturnavigator nach der Ausdehnung des Wortes. Wenn sich der Cursor auf <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> einem Wort befindet, wird der im out-Parameter zurückgegeben. Andernfalls ist `out` `null` der Parameter und `false`die Methode gibt zurück.

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

5. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>-Methode. Der Editor ruft diese Methode auf, um herauszufinden, ob die Glühbirne angezeigt werden soll. Dieser Aufruf erfolgt häufig, z. B. wenn sich der Cursor von einer Zeile zur anderen bewegt oder wenn die Maus über einen Fehler squiggle bewegt wird. Es ist asynchron, damit andere UI-Vorgänge weitergehen können, während diese Methode funktioniert. In den meisten Fällen muss diese Methode einige Analysen und Analysen der aktuellen Zeile durchführen, sodass die Verarbeitung einige Zeit in Anspruch nehmen kann.

     In dieser Implementierung ruft sie <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> asynchron ab und bestimmt, ob die Ausdehnung signifikant ist, z. B. in, ob sie einen anderen Text als Leerzeichen enthält.

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

6. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> Sie die Methode, <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> die ein Array <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> von Objekten zurückgibt, die die verschiedenen Objekte enthalten. Diese Methode wird aufgerufen, wenn die Glühbirne erweitert wird.

    > [!WARNING]
    > Sie sollten sicherstellen, dass `HasSuggestedActionsAsync()` die `GetSuggestedActions()` Implementierungen von und konsistent sind; Das heißt, `HasSuggestedActionsAsync()` `true`wenn `GetSuggestedActions()` zurückgegeben wird, sollten dann einige Aktionen angezeigt werden. In vielen `HasSuggestedActionsAsync()` Fällen wird `GetSuggestedActions()`kurz vor aufgerufen, aber dies ist nicht immer der Fall. Wenn der Benutzer z. B. die Glühbirnenaktionen aufruft, `GetSuggestedActions()` indem er nur (**STRG+** .) drückt, wird aufgerufen.

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

7. Definieren `SuggestedActionsChanged` Sie ein Ereignis.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Um die Implementierung abzuschließen, fügen `Dispose()` `TryGetTelemetryId()` Sie Implementierungen für die und Methoden hinzu. Sie möchten keine Telemetrie tun, also `false` kehren Sie einfach `Empty`zurück und legen Sie die GUID auf .

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

## <a name="implement-light-bulb-actions"></a>Implementieren von Glühbirnenaktionen

1. Fügen Sie im Projekt einen Verweis auf *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* hinzu, und legen Sie **Lokal kopieren** auf `False`fest.

2. Erstellen Sie zwei Klassen, die erste mit dem Namen `UpperCaseSuggestedAction` und die zweite mit dem Namen `LowerCaseSuggestedAction`. Beide Klassen implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Beide Klassen sind bis auf eine Ausnahme identisch: Die eine ruft <xref:System.String.ToUpper%2A> und die andere <xref:System.String.ToLower%2A> auf. In den folgenden Schritten wird nur die Klasse für die Umwandlung in Großbuchstaben behandelt; Sie müssen aber beide Klassen implementieren. Verwenden Sie diese Schritte als Muster für die Implementierung der Aktion zur Umwandlung in Kleinbuchstaben.

3. Fügen Sie die folgenden Verwendungsdirektiven für diese Klassen hinzu:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Deklarieren Sie einen Satz privater Felder.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Fügen Sie einen Konstruktor hinzu, der die Felder festlegt.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> Sie die Methode so, dass die Aktionsvorschau angezeigt wird.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> Sie die Methode so, dass sie eine leere <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> Enumeration zurückgibt.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Implementieren Sie die Eigenschaften wie folgt:

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
    > Es wird nicht erwartet, dass die Glühbirnenaktion **Invoke-Methode** benutzeroberfläche anzeigt. Wenn Ihre Aktion eine neue Benutzeroberfläche (z. B. ein Vorschau- oder Auswahldialogfeld) aufruft, zeigt sie die Benutzeroberfläche nicht direkt innerhalb der **Invoke-Methode** an, sondern plant stattdessen, die Benutzeroberfläche nach der Rückgabe von **Invoke**anzuzeigen.

10. Um die Implementierung abzuschließen, fügen Sie die `Dispose()` und `TryGetTelemetryId()` Methoden hinzu.

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

11. Vergessen Sie nicht, dasselbe `LowerCaseSuggestedAction` zu tun, um den{0}Anzeigetext in "Konvertieren <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A>' ' in Kleinbuchstaben" und den Aufruf von zu zu ändern.

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die LightBulbTest-Lösung, und führen Sie sie in der Experimental-Instanz aus.

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein. Sie sollten eine Glühbirne links neben dem Text sehen.

     ![Die Glühbirne testen](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Zeigen Sie auf die Glühbirne. Sie sollten einen Abwärtspfeil sehen.

5. Wenn Sie auf die Glühbirne klicken, sollten zwei vorgeschlagene Aktionen zusammen mit der Vorschau der ausgewählten Aktion angezeigt werden.

     ![Glühbirne testen, erweitert](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Wenn Sie auf die erste Aktion klicken, sollte der gesamte Text im aktuellen Wort in Großbuchstaben konvertiert werden. Wenn Sie auf die zweite Aktion klicken, sollte der gesamte Text in Kleinbuchstaben konvertiert werden.
