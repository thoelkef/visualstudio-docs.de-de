---
title: 'Exemplarische Vorgehensweise: Markieren von Text | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99dbc928834cddade1c434f9d5d5d8e68c40825b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106032"
---
# <a name="walkthrough-highlight-text"></a>Exemplarische Vorgehensweise: Hervorheben von text
Sie können unterschiedliche optische Effekte auf den Editor hinzufügen, durch das Erstellen von Komponenten des Managed Extensibility Framework (MEF). Diese exemplarische Vorgehensweise veranschaulicht das jedes Vorkommen des aktuellen Worts in einer Textdatei zu markieren. Wenn ein Wort mehr als einmal in eine Textdatei tritt, und Sie die Einfügemarke in einem Vorkommen positionieren, wird jedes Vorkommen hervorgehoben.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

1. Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `HighlightWordTest`.

2. Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="define-a-textmarkertag"></a>Definieren Sie eine TextMarkerTag
 Der erste Schritt beim Markieren von Text ist, um eine Unterklasse <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> und seine Darstellung zu definieren.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Zum Definieren einer TextMarkerTag und eine MarkerFormatDefinition

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie **HighlightWordTag**.

2. Fügen Sie die folgenden Verweise hinzu:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Presentation.Core

    8. Presentation.Framework

3. Importieren Sie die folgenden Namespaces ein.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. Erstellen Sie eine Klasse, die von erbt <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> und nennen Sie sie `HighlightWordTag`.

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Erstellen Sie eine zweite Klasse, die von erbt <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, und nennen Sie sie `HighlightWordFormatDefinition`. Um dieser Formatdefinition für Ihr Tag zu verwenden, müssen Sie es mit den folgenden Attributen exportieren:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Tags Hiermit können Sie um dieses Format zu verweisen.

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Dies führt dazu, dass das Format, das in der Benutzeroberfläche angezeigt werden.

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. Definieren Sie im Konstruktor für HighlightWordFormatDefinition Anzeigename und Darstellung. Die Background-Eigenschaft definiert die Füllfarbe aus, während die Foreground-Eigenschaft die Rahmenfarbe definiert.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. Übergeben Sie im Konstruktor für HighlightWordTag den Namen der Formatdefinition, die Sie erstellt haben.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementieren einer ITagger
 Der nächste Schritt besteht zum Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Schnittstelle. Diese Schnittstelle weist einen angegebenen Textpuffer, Tags, die textmarkierung bereitstellen und andere visuelle Effekte auf.

### <a name="to-implement-a-tagger"></a>Zum Implementieren eines Taggers

1. Erstellen Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> des Typs `HighlightWordTag`, und nennen Sie sie `HighlightWordTagger`.

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Fügen Sie die folgenden privaten Felder und Eigenschaften der Klasse hinzu:

    - Ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, entspricht der aktuellen Textansicht.

    - Ein <xref:Microsoft.VisualStudio.Text.ITextBuffer>, entspricht der Textpuffer, der die Textansicht zugrunde liegt.

    - Ein <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, die zum Suchen von Text verwendet wird.

    - Ein <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, die über Methoden zur Navigation in Textspannen verfügt.

    - Ein <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, enthält den Satz von Wörtern zu markieren.

    - Ein <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, das das aktuelle Wort entspricht.

    - Ein <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, das die aktuelle Position des Textcursors entspricht.

    - Ein Sperrobjekt.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Fügen Sie einen Konstruktor, der initialisiert die Eigenschaften, die zuvor aufgeführten und fügt <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> -Ereignishandler.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. Die Ereignishandler, die beide rufen die `UpdateAtCaretPosition` Methode.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. Sie müssen auch Folgendes hinzufügen: ein `TagsChanged` -Ereignis, das von der Update-Methode aufgerufen wird.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. Die `UpdateAtCaretPosition()` Methode findet jedes Wort im Textpuffer, der identisch mit dem Wort ist, in dem sich der Cursor positioniert ist und erstellt eine Liste der <xref:Microsoft.VisualStudio.Text.SnapshotSpan> Objekte, die die Vorkommen des Worts entsprechen. Es ruft dann `SynchronousUpdate`, löst dadurch die `TagsChanged` Ereignis.

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. Die `SynchronousUpdate` führt eine synchrone Aktualisierung für die `WordSpans` und `CurrentWord` Eigenschaften und löst die `TagsChanged` Ereignis.

    ```vb
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. Sie müssen implementieren die <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode. Diese Methode akzeptiert eine Auflistung von <xref:Microsoft.VisualStudio.Text.SnapshotSpan> Objekte und gibt eine Enumeration von Tagspannen.

     Implementieren Sie in C# geschrieben diese Methode als eine "yield"-Iterator, der ermöglicht die verzögerte Auswertung (d. h. als Evaluierungsversion des Satzes nur, wenn einzelne Elemente zugegriffen werden), der Tags. Klicken Sie in Visual Basic eine Liste der Tags hinzugefügt und Zurückgeben einer Liste.

     Hier die Methode gibt eine <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> Objekt mit einer "Blau" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, dem bietet es sich um eines blauen Hintergrunds.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Erstellen Sie einen Tagger-Anbieter
 Um Ihre Tagger erstellen zu können, müssen Sie implementieren eine <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Diese Klasse ist einer MEF-Komponente, damit Sie die richtigen Attribute festlegen müssen, damit diese Erweiterung erkannt wird.

> [!NOTE]
>  Weitere Informationen über MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Zum Erstellen eines Anbieters Taggers

1. Erstellen Sie eine Klasse, die mit dem Namen `HighlightWordTaggerProvider` , implementiert <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, und exportieren Sie es mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Müssen Sie zwei Editor-Dienste: Importieren der <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> und <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, um den Tagger zu instanziieren.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> -Methode zur Rückgabe einer Instanz von `HighlightWordTagger`.

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projektmappe HighlightWordTest, und führen Sie es in der experimentellen Instanz.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Zum Erstellen und Testen der Lösung HighlightWordTest

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text in dem die Wörter wiederholt werden, z. B. "Hello Hello Hello".

4. Positionieren Sie den Cursor in einem Vorkommen der "Hello" ein. Jedes Vorkommen sollten in blau hervorgehoben werden.

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Verknüpfen Sie einen Inhaltstyp mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)