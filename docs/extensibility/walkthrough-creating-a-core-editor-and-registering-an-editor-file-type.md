---
title: Ein Kern-Editor erstellen und registrieren einen Dateityp-Editor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 29
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: dec3e53df108377dacfc53ba308029933654b789
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Exemplarische Vorgehensweise: Erstellen eines Kern-Editors, und registrieren einen Dateityp-Editor
Diese exemplarische Vorgehensweise veranschaulicht, wie eine VSPackage erstellen, die beginnt, den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor, wenn eine Datei mit der Dateinamenerweiterung .myext geladen wird.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Speicherorte für die Visual Studio-Paket-Projektvorlage  
 Die VSPackage-Projektvorlage finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt** :  
  
1.  Unter Visual Basic-Erweiterungen. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Unter C#-Erweiterungen. Die Standardsprache des Projekts ist C#.  
  
3.  Unter den Erweiterungen für andere Projekttypen. Die Standardsprache des Projekts ist C++.  
  
### <a name="to-create-the-vspackage"></a>So erstellen Sie das VSPackage  
  
-   Starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , und erstellen Sie eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage mit dem Namen `MyPackage`, wie im [Exemplarische Vorgehensweise: Erstellen eines Menüs Befehl VSPackage](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>So fügen Sie die Editor-Factory hinzu  
  
1.  Mit der rechten Maustaste die **MyPackage** Projekt, zeigen Sie auf **hinzufügen** , und klicken Sie dann auf **Klasse**.  
  
2.  In der **neues Element hinzufügen** Dialogfeld stellen Sie sicher, dass die **Klasse** Vorlage ausgewählt ist, geben `EditorFactory.cs` für den Namen ein, und klicken Sie dann auf **hinzufügen** So fügen Sie der Klasse zu Ihrem Projekt hinzu.  
  
     Die Datei EditorFactory.cs sollte automatisch geöffnet werden.  
  
3.  Verweisen auf die folgenden Assemblys aus dem Code.  
  
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
  
4.  Hinzufügen einen GUID, um die `EditorFactory` -Klasse durch das Hinzufügen der `Guid` Attribut unmittelbar vor der Klassendeklaration.  
  
     Sie können eine neue GUID mit dem Programm "guidgen.exe" zu generieren die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Befehl ein, oder indem Sie auf **GUID erstellen** auf die **Tools** Menü. Die hier verwendete GUID dient nur als Beispiel; Verwenden Sie es nicht in Ihrem Projekt.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  Fügen Sie in der Klassendefinition zwei private Variablen, die das übergeordnete Paket und ein Dienstanbieter enthalten.  
  
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
  
6.  Fügen Sie einen öffentliche Klasse-Konstruktor, der einen Parameter des Typs akzeptiert <xref:Microsoft.VisualStudio.Shell.Package>:  
  
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
  
7.  Ändern der `EditorFactory` -Klassendeklaration Ableitung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  Mit der rechten Maustaste <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, klicken Sie auf **Schnittstelle implementieren**, und klicken Sie dann auf **Schnittstelle explizit implementieren**.  
  
     Dadurch wird die vier Methoden, die in implementiert werden müssen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle.  
  
9. Ersetzen Sie den Inhalt der `IVsEditorFactory.Close`-Methode durch folgenden Code.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Ersetzen Sie den Inhalt von der `IVsEditorFactory.SetSite` durch den folgenden Code.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Ersetzen Sie den Inhalt der `IVsEditorFactory.MapLogicalView`-Methode durch folgenden Code.  
  
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
  
12. Ersetzen Sie den Inhalt der `IVsEditorFactory.CreateEditorInstance`-Methode durch folgenden Code.  
  
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
  
### <a name="to-register-the-editor-factory"></a>So registrieren die Editor-factory  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf die Datei "Resources.resx", um sie in der Zeichenfolgentabelle, in denen geöffnet den Eintrag **Zeichenfolge1** ausgewählten.  
  
2.  Ändern Sie den Namen des Bezeichners zu `IDS_EDITORNAME` und der Text, der **MyPackage-Editor.** Diese Zeichenfolge wird als Namen für den Editor angezeigt.  
  
3.  Öffnen Sie die Datei VSPackage.resx, und fügen Sie einen neuen Zeichenfolge, die den Namen **101** und den Wert auf `IDS_EDITORNAME`. Dies bietet eine Ressourcen-ID, die Zeichenfolge, die Sie gerade erstellt haben, den Zugriff auf das Paket.  
  
    > [!NOTE]
    >  Enthält die VSPackage.resx-Datei eine andere Zeichenfolge, die `name` -Attributsatz zur **101**, ersetzen Sie einen anderen eindeutigen, numerischen Wert hier und in den folgenden Schritten.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie die Datei MyPackagePackage.cs.  
  
     Dies ist die Haupt-Paketdatei.  
  
5.  Fügen Sie die folgenden Attribute kurz vor dem Ausführen der `Guid` Attribut.  
  
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
  
     Die <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> Attribut ordnet die Dateierweiterung .myext der Editorfactory, damit jedes Mal, wenn eine Datei, die Erweiterung geladen wird, wird der Editorfactory aufgerufen wird.  
  
6.  Fügen Sie eine private Variable, die `MyPackage` Klasse, unmittelbar vor dem Konstruktor, und weisen Sie ihm den Typ `EditorFactory`.  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7.  Suchen der `Initialize` Methode (müssen unter Umständen zum Öffnen der `Package Members` ausgeblendeten Bereich) und fügen Sie den folgenden Code nach dem Aufruf von `base.Initialize()`.  
  
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
  
8.  Kompilieren Sie das Programm, und vergewissern Sie sich, dass keine Fehler vorliegen.  
  
     Dieser Schritt wird die Editor-Factory registriert, in der experimentellen Registrierungsstruktur für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Wenn Sie aufgefordert werden, um resource.h-Datei zu überschreiben, klicken Sie auf **OK**.  
  
9. Erstellen Sie eine Beispieldatei, die mit dem Namen TextFile1.myext.  
  
10. Drücken Sie **F5** zu eine Instanz von der experimentellen Instanz öffnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. In der experimentellen Instanz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]auf die **Datei** Sie im Menü **öffnen** , und klicken Sie dann auf **Datei**.  
  
12. Suchen Sie TextFile1.myext, und klicken Sie dann auf **öffnen**.  
  
     Die Datei sollte nun geladen werden.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor behandelt eine Vielzahl von Dateitypen textbasierten und arbeitet eng mit Language-Dienste, um einen umfangreichen Satz von Funktionen, z. B. syntaxhervorhebung, zugehörige Klammer ermöglichen und Wort vervollständigen und Member Vervollständigung IntelliSense-Listen. Wenn Sie mit textbasierte Dateien arbeiten, können Sie Core Editor zusammen mit einem benutzerdefinierten Sprachdienst verwenden, die speziellen Dateitypen unterstützt.  
  
 Eine VSPackage kann Aufrufen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor, indem Sie eine Editorfactory angeben. Dieser Editorfactory wird verwendet, wenn eine Datei, die ihm zugeordnete geladen werden. Wenn die Datei Teil eines Projekts ist, wird die Core-Editor automatisch aufgerufen, es sei denn, durch das VSPackage außer Kraft gesetzt. Jedoch wenn die Datei außerhalb eines Projekts geladen wird, muss dann die Core-Editor explizit durch das VSPackage aufgerufen werden.  
  
 Weitere Informationen zu den Core-Editor, finden Sie unter [innerhalb der Core-Editor](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Siehe auch  
 [In der Core-Editor](../extensibility/inside-the-core-editor.md)   
 [Instanziieren den Core-Editor mithilfe der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
