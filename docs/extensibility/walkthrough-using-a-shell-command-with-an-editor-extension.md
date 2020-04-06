---
title: 'Exemplarische Vorgehensweise: Verwenden eines Shell-Befehls mit einer Editorerweiterung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697170"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editorerweiterung
In einem VSPackage können Sie dem Editor Funktionen wie Menübefehle hinzufügen. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie einer Textansicht im Editor eine Verzierung hinzufügen, indem Sie einen Menübefehl aufrufen.

 In dieser exemplarischen Vorgehensweise wird die Verwendung eines VSPackage zusammen mit einem MEF-Komponententeil (Managed Extensibility Framework) veranschaulicht. Sie müssen ein VSPackage verwenden, um den Menübefehl bei der Visual Studio-Shell zu registrieren. Und Sie können den Befehl verwenden, um auf das MEF-Komponententeil zuzugreifen.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl
 Erstellen Sie ein VSPackage, das einen Menübefehl mit dem Namen **Adornment hinzufügen** im Menü **Extras** abgibt.

1. Erstellen Sie ein Projekt `MenuCommandTest`mit dem Namen , und fügen Sie einen benutzerdefinierten Befehlselementvorlagennamen **AddAdornment**hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Eine Lösung mit dem Namen MenuCommandTest wird geöffnet. Die MenuCommandTestPackage-Datei hat den Code, der den Menübefehl erstellt und im Menü **Extras** ablegt. An diesem Punkt bewirkt der Befehl nur, dass ein Meldungsfeld angezeigt wird. In späteren Schritten wird angezeigt, wie Sie dies ändern, um die Kommentarverzierung anzuzeigen.

3. Öffnen Sie die Datei *source.extension.vsixmanifest* im VSIX-Manifest-Editor. Die `Assets` Registerkarte sollte eine Zeile für ein Microsoft.VisualStudio.VsPackage mit dem Namen MenuCommandTest haben.

4. Speichern und schließen Sie die Datei *source.extension.vsixmanifest.*

## <a name="add-a-mef-extension-to-the-command-extension"></a>Hinzufügen einer MEF-Erweiterung zur Befehlserweiterung

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, klicken Sie auf **Hinzufügen**, und dann auf **Neues Projekt**. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** auf **Erweiterbarkeit** unter **Visual C,** dann **auf VSIX Project**. Geben Sie dem Projekt den Namen `CommentAdornmentTest`.

2. Da dieses Projekt mit der VSPackage-Assembly mit starkem Namen interagiert, müssen Sie die Assembly signieren. Sie können die Schlüsseldatei wiederverwenden, die bereits für die VSPackage-Assembly erstellt wurde.

    1. Öffnen Sie die Projekteigenschaften, und wählen Sie die Registerkarte **Signieren** aus.

    2. Wählen Sie **Baugruppe signieren**aus.

    3. Wählen Sie unter **Schlüsseldatei mit starkem Namen**die *Key.snk-Datei* aus, die für die MenuCommandTest-Assembly generiert wurde.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Siehe die MEF-Erweiterung im VSPackage-Projekt
 Da Sie dem VSPackage eine MEF-Komponente hinzufügen, müssen Sie beide Arten von Assets im Manifest angeben.

> [!NOTE]
> Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>So verweisen Sie auf die MEF-Komponente im VSPackage-Projekt

1. Öffnen Sie im MenuCommandTest-Projekt die Datei *source.extension.vsixmanifest* im VSIX-Manifest-Editor.

2. Klicken Sie auf der Registerkarte **Assets** auf **Neu**.

3. Wählen Sie in der **Liste Typ** **Microsoft.VisualStudio.MefComponent**aus.

4. Wählen Sie in der **Liste Quelle** die Option Ein Projekt in der **aktuellen Projektmappe**aus.

5. Wählen Sie in der **Projektliste** **CommentAdornmentTest**aus.

6. Speichern und schließen Sie die Datei *source.extension.vsixmanifest.*

7. Stellen Sie sicher, dass das MenuCommandTest-Projekt über einen Verweis auf das CommentAdornmentTest-Projekt verfügt.

8. Legen Sie im CommentAdornmentTest-Projekt fest, dass das Projekt eine Baugruppe erzeugt. Wählen Sie im **Projektmappen-Explorer**das Projekt aus, und suchen Sie im **Eigenschaftenfenster** nach der Eigenschaft **Buildausgabe in OutputDirectory kopieren,** und legen Sie es auf **true**fest.

## <a name="define-a-comment-adornment"></a>Definieren einer Kommentarverzierung
 Die Kommentarverzierung selbst <xref:Microsoft.VisualStudio.Text.ITrackingSpan> besteht aus einer, die den markierten Text nachverfolgt, und aus einigen Zeichenfolgen, die den Autor und die Beschreibung des Textes darstellen.

#### <a name="to-define-a-comment-adornment"></a>So definieren Sie eine Kommentarverzierung

1. Fügen Sie im CommentAdornmentTest-Projekt eine neue `CommentAdornment`Klassendatei hinzu, und benennen Sie sie .

2. Fügen Sie die folgenden Verweise hinzu:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Fügen Sie `using` die folgende Direktive hinzu.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Die Datei sollte eine `CommentAdornment`Klasse mit dem Namen enthalten.

    ```csharp
    internal class CommentAdornment
    ```

5. Fügen Sie der `CommentAdornment` Klasse <xref:Microsoft.VisualStudio.Text.ITrackingSpan>für die , den Autor und die Beschreibung drei Felder hinzu.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Fügen Sie einen Konstruktor hinzu, der die Felder initialisiert.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Erstellen eines visuellen Elements für die Verzierung
 Definieren Sie ein visuelles Element für Ihre Verzierung. Definieren Sie für diese exemplarische Vorgehensweise ein Steuerelement, das von <xref:System.Windows.Controls.Canvas>der Windows Presentation Foundation (WPF)-Klasse erbt.

1. Erstellen Sie eine Klasse im CommentAdornmentTest-Projekt, und benennen Sie sie `CommentBlock`.

2. Fügen Sie `using` die folgenden Direktiven hinzu.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Lassen `CommentBlock` Sie die Klasse <xref:System.Windows.Controls.Canvas>von erben.

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Fügen Sie einige private Felder hinzu, um die visuellen Aspekte der Verzierung zu definieren.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Fügen Sie einen Konstruktor hinzu, der die Kommentarverzierung definiert und den entsprechenden Text hinzufügt.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Implementieren Sie <xref:System.Windows.Controls.Panel.OnRender%2A> auch einen Ereignishandler, der die Verzierung zeichnet.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Hinzufügen eines IWpfTextViewCreationListeners
 Der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> ist ein MEF-Komponententeil, mit dem Sie Erstellungsereignisse anhören können.

1. Fügen Sie dem CommentAdornmentTest-Projekt eine `Connector`Klassendatei hinzu, und benennen Sie sie .

2. Fügen Sie `using` die folgenden Direktiven hinzu.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Deklarieren Sie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>eine Klasse, die <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> implementiert, und <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> exportieren <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>Sie sie mit einem von "text" und a von . Das Inhaltstypattribut gibt die Art des Inhalts an, auf den die Komponente angewendet wird. Der Texttyp ist der Basistyp für alle nicht binären Dateitypen. Daher wird fast jede Textansicht, die erstellt wird, von diesem Typ sein. Das Textansichtsrollenattribut gibt die Art der Textansicht an, auf die die Komponente angewendet wird. Dokumenttextansichtsrollen zeigen im Allgemeinen Text an, der aus Zeilen besteht und in einer Datei gespeichert wird.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implementieren <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Sie die Methode so, dass sie das statische `Create()` Ereignis der aufruft. `CommentAdornmentManager`

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Fügen Sie eine Methode hinzu, die Sie zum Ausführen des Befehls verwenden können.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Definieren einer Verzierungsebene
 Um eine neue Verzierung hinzuzufügen, müssen Sie einen Verzierungs-Layer definieren.

### <a name="to-define-an-adornment-layer"></a>So definieren Sie eine Verzierungsebene

1. Deklarieren Sie in `Connector` der <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>Klasse ein öffentliches <xref:Microsoft.VisualStudio.Utilities.NameAttribute> Feld vom Typ , und exportieren <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Sie es mit einem, der einen eindeutigen Namen für den Verzierungs-Layer und einen angibt, der die Z-Order-Beziehung dieser Verzierungsebene zu den anderen Textansichtsebenen (Text, Einserung und Auswahl) definiert.

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Kommentierenvonzieren
 Wenn Sie eine Verzierung definieren, implementieren Sie auch einen Kommentarverzierungsanbieter und einen Kommentarverzierungs-Manager. Der Kommentarverzierungsanbieter führt eine Liste von <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Kommentarverzierungen, hört Ereignisse im zugrunde liegenden Textpuffer ab und löscht Kommentarverzierungen, wenn der zugrunde liegende Text gelöscht wird.

1. Fügen Sie dem CommentAdornmentTest-Projekt eine `CommentAdornmentProvider`neue Klassendatei hinzu, und benennen Sie sie .

2. Fügen Sie `using` die folgenden Direktiven hinzu.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Fügen Sie eine Klasse namens `CommentAdornmentProvider`hinzu.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Fügen Sie private Felder für den Textpuffer und die Liste der Kommentarverzierungen hinzu, die sich auf den Puffer beziehen.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Fügen Sie einen `CommentAdornmentProvider`Konstruktor für hinzu. Dieser Konstruktor sollte über privaten Zugriff verfügen, da `Create()` der Anbieter von der Methode instanziiert wird. Der Konstruktor `OnBufferChanged` fügt dem <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis den Ereignishandler hinzu.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Fügen Sie die `Create()`-Methode hinzu.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Fügen Sie die `Detach()`-Methode hinzu.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Fügen `OnBufferChanged` Sie den Ereignishandler hinzu.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Fügen Sie eine `CommentsChanged` Deklaration für ein Ereignis hinzu.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Erstellen `Add()` Sie eine Methode, um die Verzierung hinzuzufügen.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Fügen `RemoveComments()` Sie eine Methode hinzu.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Fügen `GetComments()` Sie eine Methode hinzu, die alle Kommentare in einer bestimmten Momentaufnahmespanne zurückgibt.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Fügen Sie `CommentsChangedEventArgs`eine Klasse mit dem Namen , wie folgt hinzu.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Verwalten von Kommentarverzierungen
 Der Kommentarverzierungs-Manager erstellt die Verzierung und fügt sie der Verzierungsebene hinzu. Es hört die <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> und Ereignisse, so dass es die Verzierung verschieben oder löschen kann. Es überwacht auch `CommentsChanged` das Ereignis, das vom Kommentarverzierungsanbieter ausgelöst wird, wenn Kommentare hinzugefügt oder entfernt werden.

1. Fügen Sie dem CommentAdornmentTest-Projekt eine `CommentAdornmentManager`Klassendatei hinzu, und benennen Sie sie .

2. Fügen Sie `using` die folgenden Direktiven hinzu.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Fügen Sie eine Klasse namens `CommentAdornmentManager`hinzu.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Fügen Sie einige private Felder hinzu.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Fügen Sie einen Konstruktor hinzu, <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> der den Manager `CommentsChanged` für die und für die Ereignisse und auch für das Ereignis abonniert. Der Konstruktor ist privat, da der Manager `Create()` durch die statische Methode instanziiert wird.

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Fügen `Create()` Sie die Methode hinzu, die einen Anbieter abruft oder bei Bedarf einen erstellt.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Fügen `CommentsChanged` Sie den Handler hinzu.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Fügen <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Sie den Handler hinzu.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Fügen <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Sie den Handler hinzu.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Fügen Sie die private Methode hinzu, die den Kommentar zeichnet.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Verwenden Sie den Menübefehl, um die Kommentarverzierung hinzuzufügen
 Sie können den Menübefehl verwenden, um eine `MenuItemCallback` Kommentarverzierung zu erstellen, indem Sie die Methode des VSPackage implementieren.

1. Fügen Sie die folgenden Verweise zum MenuCommandTest-Projekt hinzu:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.Editor

    - Microsoft.VisualStudio.Text.UI.Wpf

2. Öffnen Sie die *AddAdornment.cs* `using` Datei, und fügen Sie die folgenden Direktiven hinzu.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Löschen `Execute()` Sie die Methode, und fügen Sie den folgenden Befehlshandler hinzu.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Fügen Sie Code hinzu, um die aktive Ansicht abzuzeigen. Sie müssen `SVsTextManager` die Visual Studio-Shell abrufen, um die aktive `IVsTextView`zu erhalten.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Wenn es sich bei dieser Textansicht um eine Instanz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> einer Editortextansicht <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> handelt, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>können Sie sie in die Benutzeroberfläche umstellen und dann die und die zugehörige abrufen. Verwenden <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Sie die `Connector.Execute()` , um die Methode aufzurufen, die den Kommentarverzierungsanbieter abruft und die Verzierung hinzufügt. Der Befehlshandler sollte nun wie folgt aussehen:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Legen Sie die AddAdornmentHandler-Methode als Handler für den AddAdornment-Befehl im AddAdornment-Konstruktor fest.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes

1. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Die experimentelle Instanz sollte angezeigt werden.

2. Erstellen einer Textdatei Geben Sie Text ein, und wählen Sie ihn aus.

3. Klicken Sie im Menü **Extras** auf **Adornment hinzufügen**auf . Eine Sprechblase sollte auf der rechten Seite des Textfensters angezeigt werden und Text enthalten, der dem folgenden Text ähnelt.

     YourUserName

     Fourscore...

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
