---
title: 'Exemplarische Vorgehensweise: Verwenden eines Shell-Befehls mit der Erweiterung-Editor | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
caps.latest.revision: 46
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 349b2fab80b6dd8a15e1f38669dc2644708aab96
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>Exemplarische Vorgehensweise: Verwenden eines Shell-Befehls mit der Erweiterung-Editor
Aus einem VSPackage können Sie Funktionen, z. B. Menübefehlen in den Editor hinzufügen. In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine Textansicht im Editor ein Randsteuerelement hinzugefügt, durch den Aufruf eines Menübefehls.  
  
 Diese exemplarische Vorgehensweise veranschaulicht die Verwendung eines VSPackage zusammen mit einer Komponente Managed Extensibility Framework (MEF). Sie müssen eine VSPackage verwenden, um den Menübefehl mit der Visual Studio-Shell zu registrieren, und verwenden Sie den Befehl auf den MEF-Komponente.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Erstellen eine Erweiterung mit einem Menübefehl  
 Erstellen ein VSPackage, das einen Menübefehl, mit dem Namen setzt **hinzufügen Randsteuerelement** auf die **Tools** Menü.  
  
1.  Erstellen Sie ein C#-VSIX-Projekt namens `MenuCommandTest`, und fügen Sie einen benutzerdefinierten Befehl Element Vorlagennamen **AddAdornment**. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Eine Lösung mit dem Namen MenuCommandTest wird geöffnet. Die MenuCommandTestPackage-Datei enthält den Code, den Menübefehl erstellt und speichert sie auf, der **Tools** Menü. An diesem Punkt bewirkt, dass der Befehl nur ein Meldungsfeld angezeigt werden. Später zeigen, wie so ändern Sie diese Option, um die Randsteuerelement Kommentar angezeigt wird.  
  
3.  Öffnen Sie im VSIX-Manifest-Editor die Datei "source.extension.vsixmanifest". Die `Assets` Registerkarte müsste eine Zeile für eine Microsoft.VisualStudio.VsPackage MenuCommandTest mit der Bezeichnung.  
  
4.  Speichern Sie und schließen Sie die Datei "Source.Extension.vsixmanifest".  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>Hinzufügen einer MEF-Erweiterung der Befehl-Erweiterung  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, klicken Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**. In der **neues Projekt hinzufügen** (Dialogfeld), klicken Sie auf **Erweiterbarkeit** unter **Visual C#-**, klicken Sie dann **VSIX-Projekt**. Benennen Sie das Projekt mit `CommentAdornmentTest`.  
  
2.  Da dieses Projekt mit der VSPackage-Assembly mit starkem Namen interagiert, müssen Sie die Assembly signieren. Sie können die Schlüsseldatei, die bereits für die VSPackage-Assembly erstellt wiederverwenden.  
  
    1.  Öffnen Sie die Projekteigenschaften, und wählen Sie die **Signierung** Registerkarte.  
  
    2.  Wählen Sie **zum Signieren der Assembly**.  
  
    3.  Klicken Sie unter **Schlüsseldatei mit starkem Namen auswählen**, wählen Sie die Key.snk-Datei, die für die Assembly MenuCommandTest generiert wurde.  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>Verweisen auf die MEF-Erweiterung in der VSPackage-Projekt  
 Da Sie das VSPackage MEF-Komponente hinzufügen möchten, müssen Sie beide Arten von Ressourcen im Manifest angeben.  
  
> [!NOTE]
>  Weitere Informationen über MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Zum Verweisen auf den MEF-Komponente in der VSPackage-Projekt  
  
1.  Öffnen Sie im Projekt MenuCommandTest der Datei source.extension.vsixmanifest im VSIX-Manifest-Editor ein.  
  
2.  Auf der **Bestand** auf **neu**.  
  
3.  In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.  
  
4.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
5.  In der **Projekt** wählen **CommentAdornmentTest**.  
  
6.  Speichern Sie und schließen Sie die Datei "Source.Extension.vsixmanifest".  
  
7.  Stellen Sie sicher, dass das MenuCommandTest Projekt einen Verweis auf das Projekt CommentAdornmentTest.  
  
8.  Legen Sie im Projekt CommentAdornmentTest das Projekt eine Assembly zu erzeugen. In der **Projektmappen-Explorer**, wählen Sie das Projekt, und suchen Sie in der **Eigenschaften** Fenster für die **Kopie erstellen Ausgabe OutputDirectory** -Eigenschaft, und legen Sie dafür **"true"**.  
  
## <a name="defining-a-comment-adornment"></a>Definieren einen Kommentar Zusatzelement (adornment)  
 Der Kommentar Randsteuerelement selbst besteht aus einer <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , verfolgt den markierten Text, und einige Zeichenfolgen, die dem Autor und die Beschreibung des Texts darstellen.  
  
#### <a name="to-define-a-comment-adornment"></a>Definieren Sie einen Kommentar Zusatzelement (adornment)  
  
1.  Klicken Sie im Projekt CommentAdornmentTest fügen Sie eine neue Klassendatei hinzu, und nennen Sie sie `CommentAdornment`.  
  
2.  Fügen Sie die folgenden Verweise hinzu:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  Fügen Sie die folgenden `using` Anweisung.  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  Die Datei muss eine Klasse namens enthalten `CommentAdornment`.  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5.  Hinzufügen von drei Feldern für die `CommentAdornment` -Klasse für die <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, dem Autor und der Beschreibung.  
  
    ```csharp  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  Fügen Sie einen Konstruktor, der die Felder initialisiert, hinzu.  
  
    ```csharp  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="creating-a-visual-element-for-the-adornment"></a>Erstellen ein visuelles Element, für die Zusatzelement (adornment)  
 Sie müssen auch ein visuelles Element für Ihre Zusatzelement (adornment) definieren. In dieser exemplarischen Vorgehensweise definieren Sie ein Steuerelement, das von der Windows Presentation Foundation (WPF)-Klasse erbt <xref:System.Windows.Controls.Canvas>.  
  
1.  Erstellen Sie eine Klasse im Projekt CommentAdornmentTest, und nennen Sie sie `CommentBlock`.  
  
2.  Fügen Sie die folgenden `using`-Anweisungen hinzu.  
  
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
  
3.  Stellen Sie die `CommentBlock` Klasse erben <xref:System.Windows.Controls.Canvas>.  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  Fügen Sie einige private Felder zum Definieren der visuellen Aspekte der Zusatzelement (adornment) hinzu.  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  Fügen Sie einen Konstruktor, der den Kommentar Zusatzelement (adornment) definiert und fügt den entsprechenden Text hinzu.  
  
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
  
6.  Implementieren Sie außerdem eine <xref:System.Windows.Controls.Panel.OnRender%2A> Ereignishandler, der die Randsteuerelement zeichnet.  
  
    ```csharp  
    protected override void OnRender(DrawingContext dc)  
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
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>Hinzufügen einer IWpfTextViewCreationListener  
 Die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> eine MEF-Komponente, die Sie verwenden können, zum Anzeigen der Ereignisse beim Erstellen von überwacht wird.  
  
1.  Das CommentAdornmentTest-Projekt eine Klassendatei hinzu, und nennen Sie sie `Connector`.  
  
2.  Fügen Sie die folgenden `using`-Anweisungen hinzu.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Deklarieren Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>, und exportieren Sie sie mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und eine <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> von <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>. Der Content-Type-Attribut gibt an, die Art des Inhalts auf die Komponente angewendet wird. Der Texttyp ist der Basistyp für alle Typen von nicht binären Dateien. Aus diesem Grund werden fast jeder Textansicht, die erstellt wird dieses Typs. Der Text anzeigen Rolle-Attribut gibt an, die Art der Textansicht, die auf die Komponente angewendet wird. Dokument Text Ansicht Rollen zeigen im Allgemeinen Text, besteht aus Linien und wird in einer Datei gespeichert.  
  
     [!code-vb[VSSDKMenuCommandTest #11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)][!code-csharp[VSSDKMenuCommandTest Nr. 11  ](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, sodass die statische aufgerufen `Create()` -Ereignis für die `CommentAdornmentManager`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  Fügen Sie eine Methode, die Sie verwenden können, um den Befehl auszuführen.  
  
    ```csharp  
    static public void Execute(IWpfTextViewHost host)  
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
  
## <a name="defining-an-adornment-layer"></a>Definieren eine Ebene Zusatzelement (adornment)  
 Um eine neue Zusatzelement (adornment) hinzuzufügen, müssen Sie eine Randsteuerelement Ebene definieren.  
  
#### <a name="to-define-an-adornment-layer"></a>Um ein Randsteuerelement-Ebene zu definieren.  
  
1.  In der `Connector` Klasse deklarieren Sie ein öffentliches Feld vom Typ <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>, und exportieren Sie sie mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , die einen eindeutigen Namen für die Ebene Zusatzelement (adornment) angibt und ein <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , definiert die Beziehung der Z-Reihenfolge dieser Randsteuerelement-Ebene der restliche Text Zeigen Sie Ebenen (Text, Caretzeichen und Auswahl).  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>Kommentar Zusatzelemente bereitstellen  
 Wenn Sie ein Randsteuerelement definieren, müssen Sie auch implementieren Sie einen Kommentar Randsteuerelement-Anbieter und einen Kommentar Randsteuerelement-Manager. Der Kommentar Randsteuerelement-Anbieter führt eine Liste der Kommentar Zusatzelemente, überwacht <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignisse auf die zugrunde liegenden Textpuffer und Löschvorgänge Kommentar Zusatzelemente, wenn die zugrunde liegenden Text gelöscht wurde.  
  
1.  Das CommentAdornmentTest-Projekt eine neue Klassendatei hinzu, und nennen Sie sie `CommentAdornmentProvider`.  
  
2.  Fügen Sie die folgenden `using`-Anweisungen hinzu.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  Fügen Sie eine Klasse mit dem Namen `CommentAdornmentProvider`.  
  
    ```csharp  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  Fügen Sie private Felder für den Textpuffer und die Liste der Kommentar Zusatzelemente im Zusammenhang mit dem Puffer.  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  Fügen Sie einen Konstruktor für `CommentAdornmentProvider`. Dieser Konstruktor privaten Zugriff haben sollten, da der Anbieter von instanziiert wird die `Create()` Methode. Fügt der Konstruktor der `OnBufferChanged` -Ereignishandler, um die <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis.  
  
    ```csharp  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  Fügen Sie die `Create()`-Methode hinzu.  
  
    ```csharp  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  Fügen Sie die `Detach()`-Methode hinzu.  
  
    ```csharp  
    public void Detach()  
    {  
        if (this.buffer != null)  
        {  
            //remove the Changed listener   
            this.buffer.Changed -= OnBufferChanged;  
            this.buffer = null;  
        }  
    }  
    ```  
  
8.  Hinzufügen der `OnBufferChanged` -Ereignishandler.  
  
    ```csharp  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
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
  
     [!code-csharp[VSSDKMenuCommandTest #21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)][!code-vb[VSSDKMenuCommandTest #21  ](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. Fügen Sie eine Deklaration für eine `CommentsChanged` Ereignis.  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Erstellen Sie eine `Add()` Methode, um die Zusatzelement (adornment) hinzuzufügen.  
  
    ```csharp  
    public void Add(SnapshotSpan span, string author, string text)  
    {  
        if (span.Length == 0)  
            throw new ArgumentOutOfRangeException("span");  
        if (author == null)  
            throw new ArgumentNullException("author");  
        if (text == null)  
            throw new ArgumentNullException("text");  
  
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
  
11. Hinzufügen einer `RemoveComments()` Methode.  
  
    ```csharp  
    public void RemoveComments(SnapshotSpan span)  
    {  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
  
        //Get a list of all the comments that are being kept   
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
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
  
12. Hinzufügen einer `GetComments()` Methode, die alle Kommentare in einer angegebenen Momentaufnahmespanne zurückgibt.  
  
    ```csharp  
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)  
    {  
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();  
        foreach (CommentAdornment comment in this.comments)  
        {  
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
                overlappingComments.Add(comment);  
        }  
  
        return new Collection<CommentAdornment>(overlappingComments);  
    }  
    ```  
  
13. Fügen Sie eine Klasse mit dem Namen `CommentsChangedEventArgs`wie folgt.  
  
    ```csharp  
    internal class CommentsChangedEventArgs : EventArgs  
    {  
        public readonly CommentAdornment CommentAdded;  
  
        public readonly CommentAdornment CommentRemoved;  
  
        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)  
        {  
            this.CommentAdded = added;  
            this.CommentRemoved = removed;  
        }  
    }  
    ```  
  
## <a name="managing-comment-adornments"></a>Verwalten von Kommentar-Zusatzelemente  
 Der Kommentar Randsteuerelement-Manager erstellt die Zusatzelement (adornment) und die Randsteuerelement-Ebene hinzugefügt. Überwacht, die <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Ereignisse so, dass die It kann verschieben oder löschen die Zusatzelement (adornment). Außerdem überwacht, die `CommentsChanged` Ereignis, das vom Anbieter Randsteuerelement Kommentar ausgelöst wird, wenn Kommentare hinzugefügt oder entfernt werden.  
  
1.  Das CommentAdornmentTest-Projekt eine Klassendatei hinzu, und nennen Sie sie `CommentAdornmentManager`.  
  
2.  Fügen Sie die folgenden `using`-Anweisungen hinzu.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  Fügen Sie eine Klasse mit dem Namen `CommentAdornmentManager`.  
  
    ```csharp  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  Fügen Sie einige private Felder hinzu.  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  Fügen Sie einen Konstruktor, der den Manager abonniert die <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Ereignisse, und auch mit der `CommentsChanged` Ereignis. Der Konstruktor ist privat, da der Manager, von der statischen instanziiert wird `Create()` Methode.  
  
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
  
6.  Hinzufügen der `Create()` Methode, die einen Anbieter ruft oder bei Bedarf erstellt.  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  Hinzufügen der `CommentsChanged` Handler.  
  
    ```csharp  
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)  
    {  
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag).   
        if (e.CommentRemoved != null)  
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);  
  
        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout).   
        if (e.CommentAdded != null)  
            this.DrawComment(e.CommentAdded);  
    }  
    ```  
  
8.  Hinzufügen der <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Handler.  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Hinzufügen der <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Handler.  
  
    ```csharp  
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
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
  
10. Fügen Sie die private Methode, die den Kommentar zeichnet.  
  
     [!code-csharp[VSSDKMenuCommandTest #35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)][!code-vb[VSSDKMenuCommandTest #35  ](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>Verwenden den Menübefehl zum Hinzufügen von den Kommentar Zusatzelement (adornment)  
 Können Sie den Menübefehl zum Erstellen von einem Kommentar Zusatzelement (adornment) durch die Implementierung der `MenuItemCallback` Methode des VSPackage.  
  
1.  Fügen Sie die folgenden Verweise dem Projekt MenuCommandTest hinzu:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  Öffnen Sie die Datei AddAdornment.cs, und fügen Sie die folgenden `using` Anweisungen.  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  Löschen Sie die ShowMessageBox()-Methode, und fügen Sie den folgenden Befehlshandler hinzu.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  Fügen Sie Code, um die aktive Ansicht zu erhalten. Sie benötigen die `SVsTextManager` der Visual Studio-Shell zum Abrufen des aktives `IVsTextView`.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  Wenn diese Textansicht eine Instanz einer Ansicht der Editor Text ist, können Sie es zum Umwandeln der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> Schnittstelle, und rufen Sie anschließend die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> und die zugehörigen <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Verwenden der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> zum Aufrufen der `Connector.Execute()` -Methode, die Ruft den Kommentar Randsteuerelement-Anbieter ab und fügt die Zusatzelement (adornment). Der Befehlshandler sollte jetzt wie folgt aussehen:  
  
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
  
6.  Legen Sie die AddAdornmentHandler-Methode als den Handler für den Befehl AddAdornment im AddAdornment-Konstruktor.  
  
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
  
1.  Erstellen Sie die Lösung und beginnen Sie mit dem Debuggen. Die experimentelle Instanz sollte angezeigt werden.  
  
2.  Erstellen einer Textdatei Geben Sie etwas Text ein, und wählen Sie ihn.  
  
3.  Auf der **Tools** Menü klicken Sie auf **hinzufügen Randsteuerelement Aufrufen**. Eine Sprechblase auf der rechten Seite des Textfensters angezeigt werden soll, und muss Text enthalten, der etwa dem folgenden Text entspricht.  
  
     Ihr Benutzername  
  
     Fourscore...  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
