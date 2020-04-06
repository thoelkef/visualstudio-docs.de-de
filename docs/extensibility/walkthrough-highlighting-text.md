---
title: 'Exemplarische Vorgehensweise: Hervorheben von Text | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697403"
---
# <a name="walkthrough-highlight-text"></a>Exemplarische Vorgehensweise: Text hervorheben
Sie können dem Editor verschiedene visuelle Effekte hinzufügen, indem Sie MEF-Komponenten (Managed Extensibility Framework) erstellen. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie jedes Vorkommen des aktuellen Wortes in einer Textdatei hervorheben. Wenn ein Wort mehr als einmal in einer Textdatei auftritt und Sie die Einserstelle in einem Vorkommen positionieren, wird jedes Vorkommen hervorgehoben.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

1. Erstellen Sie ein Projekt von C-VSIX. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C/ Erweiterbarkeit**aus, dann **VSIX-Projekt**.) Benennen Sie `HighlightWordTest`die Lösung .

2. Fügen Sie dem Projekt eine Editor-Klassifierelementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="define-a-textmarkertag"></a>Definieren eines TextMarkerTags
 Der erste Schritt beim Hervorheben <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> von Text besteht darin, die Unterklasse zu unterklassen und ihre Darstellung zu definieren.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>So definieren Sie ein TextMarkerTag und eine MarkerFormatDefinition

1. Fügen Sie eine Klassendatei hinzu und nennen Sie sie **HighlightWordTag**.

2. Fügen Sie die folgenden Verweise hinzu:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Präsentation.Core

    8. Präsentation.Rahmen

3. Importieren Sie die folgenden Namespaces.

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

4. Erstellen Sie eine Klasse, <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> von `HighlightWordTag`der erbt, und benennen Sie sie .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Erstellen Sie eine zweite Klasse, die <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> `HighlightWordFormatDefinition`von erbt, und benennen Sie sie . Um diese Formatdefinition für Ihr Tag zu verwenden, müssen Sie es mit den folgenden Attributen exportieren:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Tags verwenden dies, um auf dieses Format zu verweisen

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Dies bewirkt, dass das Format in der Benutzeroberfläche angezeigt wird

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. Definieren Sie im Konstruktor für HighlightWordFormatDefinition den Anzeigenamen und die Darstellung. Die Background-Eigenschaft definiert die Füllfarbe, während die Foreground-Eigenschaft die Rahmenfarbe definiert.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. Übergeben Sie im Konstruktor für HighlightWordTag den Namen der von Ihnen erstellten Formatdefinition.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementieren eines ITagger
 Der nächste Schritt besteht <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> darin, die Schnittstelle zu implementieren. Diese Schnittstelle weist einem bestimmten Textpuffer Tags zu, die Texthervorhebung und andere visuelle Effekte bereitstellen.

### <a name="to-implement-a-tagger"></a>So implementieren Sie einen Tagger

1. Erstellen Sie eine <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Klasse, `HighlightWordTag`die vom `HighlightWordTagger`Typ implementiert, und benennen Sie sie .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Fügen Sie der Klasse die folgenden privaten Felder und Eigenschaften hinzu:

    - Eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, die der aktuellen Textansicht entspricht.

    - Eine <xref:Microsoft.VisualStudio.Text.ITextBuffer>, die dem Textpuffer entspricht, der der Textansicht zugrunde liegt.

    - Eine <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, die zum Suchen von Text verwendet wird.

    - Eine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, die Methoden zum Navigieren innerhalb von Textspannen enthält.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, der den Satz von zu markierenden Wörtern enthält.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, die dem aktuellen Wort entspricht.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, die der aktuellen Position der Einstelle entspricht.

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

3. Fügen Sie einen Konstruktor hinzu, der <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> die <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> zuvor aufgeführten Eigenschaften initialisiert und Ereignishandler hinzufügt.

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

4. Die Ereignishandler rufen `UpdateAtCaretPosition` beide die Methode auf.

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

5. Sie müssen auch `TagsChanged` ein Ereignis hinzufügen, das von der Updatemethode aufgerufen wird.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. Die `UpdateAtCaretPosition()` Methode findet jedes Wort im Textpuffer, das mit dem Wort identisch <xref:Microsoft.VisualStudio.Text.SnapshotSpan> ist, in dem der Cursor positioniert ist, und erstellt eine Liste von Objekten, die den Vorkommen des Wortes entsprechen. Anschließend wird `SynchronousUpdate`der Fall `TagsChanged` ausrufen, wodurch das Ereignis auslöst.

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

7. Der `SynchronousUpdate` führt eine synchrone `WordSpans` `CurrentWord` Aktualisierung der und-Eigenschaften durch und löst das `TagsChanged` Ereignis aus.

    ```csharp
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

8. Sie müssen <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> die Methode implementieren. Diese Methode nimmt <xref:Microsoft.VisualStudio.Text.SnapshotSpan> eine Auflistung von Objekten und gibt eine Enumeration von Tag-Spannen zurück.

     Implementieren Sie diese Methode in C- als Ertragsiterator, der eine verzögerte Auswertung (d. h. die Auswertung des Satzes nur beim Zugriff auf einzelne Elemente) der Tags ermöglicht. Fügen Sie in Visual Basic die Tags zu einer Liste hinzu, und geben Sie die Liste zurück.

     Hier gibt die <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> Methode ein Objekt <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>zurück, das über einen "blauen" verfügt, der einen blauen Hintergrund bereitstellt.

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

## <a name="create-a-tagger-provider"></a>Erstellen eines Tagger-Anbieters
 Um Ihren Tagger zu erstellen, müssen Sie eine <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>implementieren. Diese Klasse ist ein MEF-Komponententeil, daher müssen Sie die richtigen Attribute festlegen, damit diese Erweiterung erkannt wird.

> [!NOTE]
> Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>So erstellen Sie einen Tagger-Anbieter

1. Erstellen Sie `HighlightWordTaggerProvider` eine Klasse <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>mit dem Namen <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , die implementiert, und exportieren Sie sie mit einem von "text" und a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Sie müssen zwei Editordienste <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> importieren, die und die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, um den Tagger zu instanziieren.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implementieren <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> Sie die Methode, `HighlightWordTagger`um eine Instanz von zurückzugeben.

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
 Um diesen Code zu testen, erstellen Sie die HighlightWordTest-Lösung, und führen Sie sie in der experimentellen Instanz aus.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>So erstellen und testen Sie die HighlightWordTest-Lösung

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, in dem die Wörter wiederholt werden, z. B. "hallo hallo hello".

4. Positionieren Sie den Cursor in einem der Vorkommen von "hello". Jedes Vorkommen sollte blau hervorgehoben werden.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
