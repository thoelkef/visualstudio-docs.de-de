---
title: 'Exemplarische Vorgehensweise: Erstellen eines Core-Editors und Registrieren eines Editor-Datentyps | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687632"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Exemplarische Vorgehensweise: Erstellen eines Core-Editors und Registrieren eines Editordateityps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein VSPackage erstellt wird, das den Kern-Editor startet, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Wenn eine Datei mit der Dateinamenerweiterung ". myext" geladen wird.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Speicherorte für die Visual Studio-Paket-Projektvorlage  
 Die VSPackage-Projektvorlage finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt** :  
  
1. Unter Visual Basic-Erweiterungen. Die Standardsprache des Projekts ist Visual Basic.  
  
2. Unter C#-Erweiterungen. Die Standardsprache des Projekts ist C#.  
  
3. Unter den Erweiterungen für andere Projekttypen. Die Standardsprache des Projekts ist C++.  
  
### <a name="to-create-the-vspackage"></a>So erstellen Sie das VSPackage  
  
- Starten Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , und erstellen Sie ein [!INCLUDE[csprcs](../includes/csprcs-md.md)] VSPackage mit dem Namen, wie unter Exemplarische Vorgehensweise `MyPackage` [: Erstellen eines Menübefehls "VSPackage](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32)" beschrieben.  
  
### <a name="to-add-the-editor-factory"></a>So fügen Sie die Editorfactory hinzu  
  
1. Klicken Sie mit der rechten Maustaste auf das Projekt **myPackage** , zeigen Sie auf **Hinzufügen** und dann auf **Klasse**.  
  
2. Stellen Sie im Dialogfeld **Neues Element hinzufügen** sicher, dass die **Klassen** Vorlage ausgewählt ist, geben `EditorFactory.cs` Sie für den Namen ein, und klicken Sie dann auf **Hinzufügen** , um die Klasse zu Ihrem Projekt hinzuzufügen.  
  
     Die EditorFactory.cs-Datei sollte automatisch geöffnet werden.  
  
3. Verweisen Sie im Code auf die folgenden Assemblys.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4. Fügen Sie der Klasse eine GUID hinzu, `EditorFactory` indem Sie das- `Guid` Attribut direkt vor der Klassen Deklaration hinzufügen.  
  
     Sie können eine neue GUID generieren, indem Sie das Programm guidgen.exe an der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Eingabeaufforderung verwenden, oder indem Sie im Menü Extras **Tools** auf **GUID erstellen** klicken. Die hier verwendete GUID ist nur ein Beispiel. Verwenden Sie Sie nicht in Ihrem Projekt.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. Fügen Sie in der Klassendefinition zwei private Variablen hinzu, die das übergeordnete Paket und einen Dienstanbieter enthalten.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6. Fügen Sie einen öffentlichen Klassenkonstruktor hinzu, der einen Parameter vom Typ annimmt <xref:Microsoft.VisualStudio.Shell.Package> :  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7. Ändern `EditorFactory` Sie die Klassen Deklaration, um von der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle abzuleiten.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. Klicken Sie mit der rechten Maustaste auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> **Schnittstelle implementieren**, und klicken Sie dann auf **Schnittstelle explizit implementieren**.  
  
     Dadurch werden die vier Methoden hinzugefügt, die in der-Schnittstelle implementiert werden müssen <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  
  
9. Ersetzen Sie den Inhalt der `IVsEditorFactory.Close`-Methode durch den nachstehenden Code.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Ersetzen Sie den Inhalt von `IVsEditorFactory.SetSite` durch den folgenden Code.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Ersetzen Sie den Inhalt der `IVsEditorFactory.MapLogicalView`-Methode durch den nachstehenden Code.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Ersetzen Sie den Inhalt der `IVsEditorFactory.CreateEditorInstance`-Methode durch den nachstehenden Code.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Kompilieren Sie das Projekt, und stellen Sie sicher, dass keine Fehler vorliegen.  
  
### <a name="to-register-the-editor-factory"></a>So registrieren Sie die Editorfactory  
  
1. Doppelklicken Sie in **Projektmappen-Explorer**auf die Datei Resources. resx, um Sie in der Zeichen folgen Tabelle zu öffnen, in der der Eintrag **Zeichenfolge1 ausgewählt ist** .  
  
2. Ändern Sie den Namen des Bezeichners in `IDS_EDITORNAME` und den Text in **myPackage Editor.** Diese Zeichenfolge wird als Name des Editors angezeigt.  
  
3. Öffnen Sie die Datei VSPackage. resx, und fügen Sie eine neue Zeichenfolge hinzu, und legen Sie den Namen auf **101** und den Wert auf fest `IDS_EDITORNAME` . Dadurch erhält das Paket eine Ressourcen-ID für den Zugriff auf die soeben erstellte Zeichenfolge.  
  
    > [!NOTE]
    > Wenn die Datei "VSPackage. resx" eine andere Zeichenfolge enthält, die für das- `name` Attribut auf **101**festgelegt ist, ersetzen Sie hier und in den folgenden Schritten durch einen anderen eindeutigen, numerischen Wert.  
  
4. Öffnen Sie in **Projektmappen-Explorer**die Datei MyPackagePackage.cs.  
  
     Dies ist die Hauptpaket Datei.  
  
5. Fügen Sie die folgenden Benutzerattribute direkt vor dem- `Guid` Attribut hinzu.  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     Das- <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> Attribut ordnet die Dateierweiterung myext ihrer Editorfactory zu, sodass jedes Mal, wenn eine Datei mit dieser Erweiterung geladen wird, die Editorfactory aufgerufen wird.  
  
6. Fügen Sie der Klasse eine private Variable `MyPackage` direkt vor dem Konstruktor hinzu, und geben Sie Ihr den Typ `EditorFactory` .  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. Suchen `Initialize` Sie die-Methode (möglicherweise müssen Sie den ausgeblendeten `Package Members` Bereich öffnen), und fügen Sie den folgenden Code nach dem-Vorgang hinzu `base.Initialize()` .  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8. Kompilieren Sie das Programm, und vergewissern Sie sich, dass keine Fehler vorliegen.  
  
     In diesem Schritt wird die Editorfactory in der experimentellen Registrierungs Struktur für registriert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Wenn Sie aufgefordert werden, die Datei "Resource. h" außer Kraft zu setzen, klicken Sie auf **OK**.  
  
9. Erstellen Sie eine Beispieldatei mit dem Namen TextFile1. myext.  
  
10. Drücken Sie **F5** , um eine Instanz des experimentellen zu öffnen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
11. Zeigen Sie im experimentellen im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Menü **Datei** auf **Öffnen** , und klicken Sie dann auf **Datei**.  
  
12. Suchen Sie TextFile1. myext, und klicken Sie dann auf **Öffnen**.  
  
     Die Datei sollte nun geladen werden.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kern-Editor verarbeitet eine breite Palette textbasierter Dateitypen und arbeitet eng mit Sprachdiensten zusammen, um einen umfangreichen Satz von Features wie Syntax Hervorhebung, übereinstimmende Klammern, IntelliSense-Wortvervollständigung und Element Vervollständigungs Listen bereitzustellen. Wenn Sie mit textbasierten Dateien arbeiten, können Sie den Kern-Editor zusammen mit einem benutzerdefinierten Sprachdienst verwenden, der Ihre spezifischen Dateitypen unterstützt.  
  
 Ein VSPackage kann den Kern-Editor aufrufen, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] indem er eine Editorfactory bereitstellt. Diese Editorfactory wird immer dann verwendet, wenn eine Datei, die ihr zugeordnet ist, geladen wird. Wenn die Datei Teil eines Projekts ist, wird der Core-Editor automatisch aufgerufen, es sei denn, Sie wird durch das VSPackage überschrieben. Wenn die Datei jedoch außerhalb eines Projekts geladen wird, muss der Core-Editor von Ihrem VSPackage explizit aufgerufen werden.  
  
 Weitere Informationen zum Kern-Editor finden Sie unter [im Kern-Editor](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Im Kern-Editor](../extensibility/inside-the-core-editor.md)   
 [Instanziieren des Core-Editors mit der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
