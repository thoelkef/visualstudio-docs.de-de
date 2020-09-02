---
title: 'Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editor-Erweiterung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
caps.latest.revision: 47
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0312d98dd6959cb5d67d593c4bf0af39fa1889eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693363"
---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editor-Erweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aus einem VSPackage können Sie Features wie Menübefehle zum Editor hinzufügen. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einer Textansicht im Editor ein Zusatzelement hinzugefügt wird, indem ein Menübefehl aufgerufen wird.  
  
 In dieser exemplarischen Vorgehensweise wird die Verwendung eines VSPackages zusammen mit einem Managed Extensibility Framework Komponenten Teil (MEF) veranschaulicht. Sie müssen ein VSPackage verwenden, um den Menübefehl in der Visual Studio-Shell zu registrieren, und Sie können den Befehl verwenden, um auf den MEF-Komponenten Teil zuzugreifen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl  
 Erstellen Sie ein VSPackage, das einen Menübefehl mit dem Namen **Zusatzelement hinzufügen** **im Menü Extras** einfügt.  
  
1. Erstellen Sie ein c#-VSIX-Projekt mit dem Namen `MenuCommandTest` , und fügen Sie einen benutzerdefinierten Befehls Element-Vorlagen Namen **addadornment**hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Eine Projekt Mappe mit dem Namen menucommandtest wird geöffnet. Die menucommandtestpackage-Datei enthält den Code, der den Menübefehl erstellt und ihn im **Menü Extras** einfügt. An diesem Punkt bewirkt der Befehl lediglich, dass ein Meldungs Feld angezeigt wird. In späteren Schritten wird gezeigt, wie Sie diesen Wert ändern, um das Kommentar Zusatzelement anzuzeigen.  
  
3. Öffnen Sie im VSIX-Manifest-Editor die Datei "source.extension.vsixmanifest". Die `Assets` Registerkarte muss über eine Zeile für ein Microsoft. VisualStudio. VSPackage mit dem Namen menucommandtest verfügen.  
  
4. Speichern und schließen Sie die Datei "Source. Extension. vsixmanifest".  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>Hinzufügen einer MEF-Erweiterung zur Befehls Erweiterung  
  
1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, klicken Sie auf **Hinzufügen**und dann auf **Neues Projekt**. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** unter **Visual c#** auf **Erweiterbarkeit** und dann auf **VSIX-Projekt**. Benennen Sie das Projekt mit `CommentAdornmentTest`.  
  
2. Da dieses Projekt mit der VSPackage-Assembly mit starkem Namen interagiert, müssen Sie die Assembly signieren. Sie können die Schlüsseldatei wieder verwenden, die bereits für die VSPackage-Assembly erstellt wurde.  
  
    1. Öffnen Sie die Projekteigenschaften, und wählen Sie die Registerkarte **Signierung** .  
  
    2. Wählen Sie **Assembly signieren**aus.  
  
    3. Wählen Sie unter **Schlüsseldatei mit starkem Namen auswählen**die Key. SNK-Datei aus, die für die menucommandtest-Assembly generiert wurde.  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>Verweisen auf die MEF-Erweiterung im VSPackage-Projekt  
 Da Sie dem VSPackage eine MEF-Komponente hinzufügen, müssen Sie beide Arten von Assets im Manifest angeben.  
  
> [!NOTE]
> Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>So verweisen Sie auf die MEF-Komponente im VSPackage-Projekt  
  
1. Öffnen Sie im menucommandtest-Projekt im VSIX-Manifest-Editor die Datei "Source. Extension. vsixmanifest".  
  
2. Klicken Sie auf der Registerkarte **Objekte** auf **neu**.  
  
3. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent**aus.  
  
4. Wählen Sie **Source** in der Liste Quelle **ein Projekt in der aktuellen Projekt**Mappe aus.  
  
5. Wählen Sie in der Liste **Projekt** die Option **commentadornmenttest**aus.  
  
6. Speichern und schließen Sie die Datei "Source. Extension. vsixmanifest".  
  
7. Stellen Sie sicher, dass das menucommandtest-Projekt einen Verweis auf das commentadornmenttest-Projekt enthält.  
  
8. Legen Sie im commentadornmenttest-Projekt fest, dass das Projekt eine Assembly erzeugt. Wählen Sie im **Projektmappen-Explorer**das Projekt aus, und suchen Sie im **Eigenschaften** Fenster nach der Eigenschaft **Build-Ausgabe in OutputDirectory kopieren** , und legen Sie Sie auf **true**fest.  
  
## <a name="defining-a-comment-adornment"></a>Definieren eines Kommentar Zusatz Elements  
 Das Kommentar Zusatzelement selbst besteht aus einem, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> das den ausgewählten Text nachverfolgt, und einigen Zeichen folgen, die den Autor und die Beschreibung des Texts darstellen.  
  
#### <a name="to-define-a-comment-adornment"></a>So definieren Sie ein Kommentar Zusatzelement  
  
1. Fügen Sie im commentadornmenttest-Projekt eine neue Klassendatei hinzu, und benennen Sie Sie `CommentAdornment` .  
  
2. Fügen Sie die folgenden Verweise hinzu:  
  
    1. Microsoft. VisualStudio. coreutility  
  
    2. Microsoft. VisualStudio. Text. Data  
  
    3. Microsoft. VisualStudio. Text. Logic  
  
    4. Microsoft. VisualStudio. Text. UI  
  
    5. Microsoft. VisualStudio. Text. UI. WPF  
  
    6. System.ComponentModel.Composition  
  
    7. PresentationCore  
  
    8. PresentationFramework  
  
    9. WindowsBase  
  
3. Fügen Sie die folgende `using` -Anweisung hinzu.  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4. Die Datei sollte eine Klasse mit dem Namen enthalten `CommentAdornment` .  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5. Fügen Sie der `CommentAdornment` -Klasse drei Felder für <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , den Autor und die Beschreibung hinzu.  
  
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
  
## <a name="creating-a-visual-element-for-the-adornment"></a>Erstellen eines visuellen Elements für das Zusatz Element  
 Sie müssen auch ein visuelles Element für das Zusatzelement definieren. Definieren Sie für diese exemplarische Vorgehensweise ein Steuerelement, das von der Windows Presentation Foundation (WPF)-Klasse erbt <xref:System.Windows.Controls.Canvas> .  
  
1. Erstellen Sie im commentadornmenttest-Projekt eine Klasse, und benennen Sie Sie `CommentBlock` .  
  
2. Fügen Sie die folgenden `using`-Anweisungen hinzu:  
  
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
  
3. Legen Sie die `CommentBlock` Klasse von ab <xref:System.Windows.Controls.Canvas> .  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4. Fügen Sie einige private Felder hinzu, um die visuellen Aspekte des Zusatz Elements zu definieren.  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5. Fügen Sie einen Konstruktor hinzu, der das Kommentar Zusatzelement definiert, und fügen Sie den relevanten Text hinzu.  
  
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
  
6. Implementieren Sie außerdem einen <xref:System.Windows.Controls.Panel.OnRender%2A> Ereignishandler, der das Zusatzelement zeichnet.  
  
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
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>Hinzufügen eines iwpftextviewkreationlistener  
 Der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> ist ein MEF-Komponenten Teil, den Sie verwenden können, um auf Ansichts Erstellungs Ereignisse zu lauschen.  
  
1. Fügen Sie dem commentadornmenttest-Projekt eine Klassendatei hinzu, und benennen Sie Sie `Connector` .  
  
2. Fügen Sie die folgenden `using`-Anweisungen hinzu:  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3. Deklarieren Sie eine Klasse <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> , die implementiert, und exportieren Sie Sie mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und einem <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> . Das Inhaltstyp Attribut gibt die Art des Inhalts an, auf den die Komponente angewendet wird. Der Texttyp ist der Basistyp für alle nicht binären Dateitypen. Daher ist fast jede Textansicht, die erstellt wird, von diesem Typ. Das Attribut "Text Ansichts Rolle" gibt die Art der Textansicht an, auf die die Komponente angewendet wird. In Dokument Text Ansichts Rollen wird normalerweise Text angezeigt, der aus Zeilen besteht und in einer Datei gespeichert ist.  
  
     [!code-csharp[VSSDKMenuCommandTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkmenucommandtest/cs/commentadornmenttest/connector.cs#11)]
     [!code-vb[VSSDKMenuCommandTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkmenucommandtest/vb/commentadornmenttest/connector.vb#11)]  
  
4. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, sodass Sie das statische- `Create()` Ereignis von aufruft `CommentAdornmentManager` .  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5. Fügen Sie eine Methode hinzu, mit der Sie den Befehl ausführen können.  
  
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
  
## <a name="defining-an-adornment-layer"></a>Definieren einer Adornment-Ebene  
 Um ein neues Zusatzelement hinzuzufügen, müssen Sie eine Zusatzelement-Ebene definieren.  
  
#### <a name="to-define-an-adornment-layer"></a>So definieren Sie eine Zusatzelement-Ebene  
  
1. `Connector`Deklarieren Sie in der-Klasse ein öffentliches Feld vom Typ <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> , und exportieren Sie es mit einem, <xref:Microsoft.VisualStudio.Utilities.NameAttribute> das einen eindeutigen Namen für die Zusatzelement-Schicht und einen angibt, <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> der die Z-Reihenfolge Beziehung dieser Zusatzelement-Schicht zu anderen Text Ansichts Schichten (Text, Caretzeichen und Auswahl) definiert.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>Bereitstellen von Kommentar Zusatzelementen  
 Wenn Sie ein Zusatzelement definieren, implementieren Sie auch einen Kommentar Zusatz Anbieter und einen Kommentar Zusatz-Manager. Der Kommentar Zusatzelement-Anbieter speichert eine Liste von Kommentar Zusatzelementen, lauscht auf <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignisse auf dem zugrunde liegenden Text Puffer und löscht Kommentar Zusatzelemente, wenn der zugrunde liegende Text gelöscht wird.  
  
1. Fügen Sie dem commentadornmenttest-Projekt eine neue Klassendatei hinzu, und benennen Sie Sie `CommentAdornmentProvider` .  
  
2. Fügen Sie die folgenden `using`-Anweisungen hinzu:  
  
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
  
4. Fügen Sie private Felder für den Text Puffer und die Liste der Kommentar Zusatzelemente hinzu, die mit dem Puffer verknüpft sind.  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5. Fügen Sie einen Konstruktor für hinzu `CommentAdornmentProvider` . Dieser Konstruktor sollte privaten Zugriff haben, da der Anbieter von der-Methode instanziiert wird `Create()` . Der-Konstruktor fügt dem- `OnBufferChanged` Ereignis den Ereignishandler hinzu <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .  
  
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
  
8. Fügen Sie den `OnBufferChanged` Ereignishandler hinzu.  
  
    ```csharp  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-csharp[VSSDKMenuCommandTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkmenucommandtest/cs/commentadornmenttest/commentadornmentprovider.cs#21)]
     [!code-vb[VSSDKMenuCommandTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkmenucommandtest/vb/commentadornmenttest/commentadornmentprovider.vb#21)]  
  
9. Fügen Sie eine Deklaration für ein- `CommentsChanged` Ereignis hinzu.  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Erstellen Sie eine- `Add()` Methode, um das Zusatzelement hinzuzufügen.  
  
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
  
11. Fügen Sie eine- `RemoveComments()` Methode hinzu.  
  
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
  
12. Fügen Sie eine `GetComments()` Methode hinzu, die alle Kommentare in einer bestimmten Momentaufnahme Spanne zurückgibt.  
  
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
  
13. Fügen Sie wie folgt eine Klasse mit dem Namen hinzu `CommentsChangedEventArgs` .  
  
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
  
## <a name="managing-comment-adornments"></a>Verwalten von Kommentar Zusatzelementen  
 Der Kommentar Zusatz-Manager erstellt das Zusatzelement und fügt es der Zusatzelement-Ebene hinzu. Er lauscht auf das <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> -Ereignis und das- <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Ereignis, sodass das Zusatzelement verschoben oder gelöscht werden kann. Außerdem lauscht das Ereignis auf das `CommentsChanged` Ereignis, das vom Kommentar Zusatz Anbieter ausgelöst wird, wenn Kommentare hinzugefügt oder entfernt werden.  
  
1. Fügen Sie dem commentadornmenttest-Projekt eine Klassendatei hinzu, und benennen Sie Sie `CommentAdornmentManager` .  
  
2. Fügen Sie die folgenden `using`-Anweisungen hinzu:  
  
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
  
5. Fügen Sie einen Konstruktor hinzu, der den Manager für das <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> -Ereignis und das-Ereignis abonniert <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> , und auch für das- `CommentsChanged` Ereignis. Der Konstruktor ist privat, da der Manager von der statischen-Methode instanziiert wird `Create()` .  
  
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
  
6. Fügen Sie die `Create()` Methode hinzu, die einen Anbieter abruft, oder erstellen Sie bei Bedarf eine.  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7. Fügen Sie den- `CommentsChanged` Handler hinzu.  
  
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
  
8. Fügen Sie den- <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Handler hinzu.  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Fügen Sie den- <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Handler hinzu.  
  
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
  
     [!code-csharp[VSSDKMenuCommandTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkmenucommandtest/cs/commentadornmenttest/commentadornmentmanager.cs#35)]
     [!code-vb[VSSDKMenuCommandTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkmenucommandtest/vb/commentadornmenttest/commentadornmentmanager.vb#35)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>Verwenden des Menübefehls zum Hinzufügen des Kommentar Zusatz Elements  
 Sie können den Menübefehl verwenden, um ein Kommentar Zusatzelement zu erstellen, indem Sie die- `MenuItemCallback` Methode des VSPackage implementieren.  
  
1. Fügen Sie dem menucommandtest-Projekt die folgenden Verweise hinzu:  
  
    - Microsoft. VisualStudio. Text Manager. Interop  
  
    - Microsoft. VisualStudio. Editor  
  
    - Microsoft. VisualStudio. Text. UI. WPF  
  
2. Öffnen Sie die Datei AddAdornment.cs, und fügen Sie die folgenden `using` Anweisungen hinzu.  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3. Löschen Sie die ShowMessageBox ()-Methode, und fügen Sie den folgenden Befehls Handler hinzu.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4. Fügen Sie Code hinzu, um die aktive Ansicht zu erhalten. Sie müssen das `SVsTextManager` der Visual Studio-Shell erhalten, um das aktive zu erhalten `IVsTextView` .  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5. Handelt es sich bei dieser Textansicht um eine Instanz einer Editor-Textansicht, können Sie Sie in die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> Schnittstelle umwandeln und dann die und deren zugeordnete erhalten <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> . Verwenden <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Sie, um die-Methode aufzurufen `Connector.Execute()` , die den Kommentar Zusatz Anbieter abruft und das Zusatzelement hinzufügt. Der Befehls Handler sollte nun wie folgt aussehen:  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
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
  
6. Legen Sie die addadornmenthandler-Methode als Handler für den addadornment-Befehl im addadornment-Konstruktor fest.  
  
    ```csharp  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
  
1. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Die experimentelle Instanz sollte angezeigt werden.  
  
2. Erstellen einer Textdatei Geben Sie Text ein, und wählen Sie ihn aus.  
  
3. Klicken Sie **im Menü Extras** auf die Option **Zusatzelement hinzufügen**. Eine Sprechblase sollte auf der rechten Seite des Text Fensters angezeigt werden und sollte Text enthalten, der dem folgenden Text ähnelt.  
  
     IhrBenutzername  
  
     Vierscore...  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
