---
title: Erstellen einen Kern-Editor, und registrieren einen Dateityp-Editor | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aac1298c13cb931eba889e6323faff9b1640f8b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411032"
---
# <a name="walkthrough-create-a-core-editor-and-registering-an-editor-file-type"></a>Exemplarische Vorgehensweise: Erstellen Sie einen Kern-Editor und registrieren einen Dateityp-Editor-
In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie eine VSPackage zu erstellen, die beginnt die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Kern-Editor eine Datei mit den *.myext* Dateinamenerweiterung geladen wird.

## <a name="prerequisites"></a>Vorraussetzungen
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Speicherorte für die Visual Studio-Paket-Projektvorlage
 Die VSPackage-Projektvorlage finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt** :

1. Unter **Visual Basic Erweiterungen**. Die Standardsprache des Projekts ist Visual Basic.

2. Unter **C# Erweiterungen**. Die Standardsprache des Projekts ist C#.

3. Unter **Andere Projekttypen Erweiterungen**. Die Standardsprache des Projekts ist C++.

### <a name="to-create-the-vspackage"></a>Um das VSPackage zu erstellen.

- Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , und erstellen Sie eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage mit dem Namen `MyPackage`, wie unter [Exemplarische Vorgehensweise: Erstellen eines Menübefehls VSPackage](https://msdn.microsoft.com/library/d699c149-5d1e-47ff-94c7-e1222af02c32).

### <a name="to-add-the-editor-factory"></a>Die Editor-Factory hinzufügen

1. Mit der rechten Maustaste die **"myPackage"** Projekt, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Klasse**.

2. In der **neues Element hinzufügen** Dialogfeld stellen Sie sicher, dass die **Klasse** Vorlage ausgewählt ist, geben `EditorFactory.cs` für den Namen ein, und klicken Sie dann auf **hinzufügen** die Klasse zu Ihrem Projekt hinzufügen.

    Die *EditorFactory.cs* sollten Sie automatisch geöffnet.

3. Verweisen Sie die folgenden Assemblys aus dem Code.

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

4. Fügen Sie eine GUID, die die `EditorFactory` -Klasse durch das Hinzufügen der `Guid` Attribut direkt vor der Klassendeklaration.

    Sie können eine neue GUID generieren, mit der *guidgen.exe* am Programm die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Befehl ein, oder indem Sie auf **GUID erstellen** auf die **Tools** Menü. Die hier verwendete GUID ist nur ein Beispiel. Verwenden Sie es nicht in Ihrem Projekt.

   ```vb
   <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _
   ```

   ```csharp
   [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]
   ```

5. Fügen Sie in der Klassendefinition zwei private Variablen, um das übergeordnete Paket und ein Dienstanbieter enthalten.

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

6. Fügen Sie einen öffentlichen Klasse-Konstruktor, der einen Parameter des Typs akzeptiert <xref:Microsoft.VisualStudio.Shell.Package>:

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

7. Ändern der `EditorFactory` Klassendeklaration für die Ableitung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle.

   ```vb
   Class EditorFactory Implements IVsEditorFacto
   ```

   ```csharp
   class EditorFactory : IVsEditorFactory

   ```

8. Mit der rechten Maustaste <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, klicken Sie auf **Schnittstelle implementieren**, und klicken Sie dann auf **Schnittstelle explizit implementieren**.

    Dieser Schritt fügt die vier Methoden, die in implementiert werden, müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle.

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

### <a name="to-register-the-editor-factory"></a>Um die Editor-Factory zu registrieren.

1. In **Projektmappen-Explorer**, doppelklicken Sie auf die **"Resources.resx"** zu öffnenden auf die Tabelle, in der Datei den Eintrag **String1 ist** ausgewählten.

2. Ändern Sie den Namen des Bezeichners zu `IDS_EDITORNAME` und der Text, der **"myPackage"-Editor.** Diese Zeichenfolge wird als Name des Editors angezeigt.

3. Öffnen der **VSPackage.resx** Datei, fügen Sie eine neue Zeichenfolge hinzu, legen Sie den Namen **101**, und legen Sie den Wert `IDS_EDITORNAME`. Dieser Schritt umfasst das Paket mit einer Ressourcen-ID auf die Zeichenfolge, die Sie erstellt haben.

   > [!NOTE]
   > Wenn die **VSPackage.resx** -Datei enthält eine andere Zeichenfolge, die `name` -Attributsatz auf **101**, einen anderen eindeutigen, numerischen Wert ersetzen, hier und in die folgenden Schritte aus.

4. In **Projektmappen-Explorer**öffnen die **MyPackagePackage.cs** Datei.

    Diese Datei ist die Haupt-Paketdatei.

5. Fügen Sie die folgenden Benutzerattribute unmittelbar vor der `Guid` Attribut.

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

    Die <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> -Attribut ordnet das *.myext* Dateierweiterung mit Ihrer Editorfactory, damit jedes Mal, wenn eine Datei, die Erweiterung geladen wird, wird der Editorfactory aufgerufen wird.

6. Fügen Sie eine private Variable, die die `MyPackage` Klasse unmittelbar vor dem Konstruktor, und geben sie den Typ `EditorFactory`.

   ```vb
   Private editorFactory As EditorFactory
   ```

   ```csharp
   private EditorFactory editorFactory;
   ```

7. Suchen der `Initialize` Methode (möglicherweise müssen Sie Sie öffnen die `Package Members` ausgeblendeten Bereich), und fügen Sie den folgenden Code nach dem Aufruf von `base.Initialize()`.

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

    Dieser Schritt wird die Editor-Factory registriert, in der experimentellen Registrierungsstruktur für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Wenn Sie aufgefordert werden, überschreiben die *resource.h* , klicken Sie auf **OK**.

9. Erstellen Sie eine Beispieldatei, die mit dem Namen *TextFile1.myext*.

10. Drücken Sie **F5** zu eine Instanz von der experimentellen Instanz öffnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

11. In der experimentellen Instanz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]auf die **Datei** Startmenü **öffnen** , und klicken Sie dann auf **Datei**.

12. Suchen **TextFile1.myext** , und klicken Sie dann auf **öffnen**.

     Die Datei sollte nun laden.

## <a name="robust-programming"></a>Stabile Programmierung
 Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Kern-Editor behandelt eine Vielzahl von textbasierten Dateitypen und arbeitet eng mit Sprachdienste bieten eine Vielzahl von Features wie syntaxhervorhebung, zugehörige Klammern und IntelliSense-wortvervollständigung und membervervollständigung führt. Wenn Sie mit einem textbasierten Dateien arbeiten, können Sie die Kern-Editor, zusammen mit einem benutzerdefinierten Sprachdienst, die von Ihr bestimmte Dateitypen unterstützt.

 Rufen Sie eine VSPackage kann die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] durch Angabe einer Editor-Factory-Kern-Editor. Dieser Editorfactory wird jedes Mal verwendet, wenn eine Datei, die zugeordnet hat geladen wird. Wenn die Datei Teil eines Projekts ist, wird die Kern-Editor automatisch aufgerufen, es sei denn, durch das VSPackage außer Kraft gesetzt. Jedoch, wenn die Datei außerhalb eines Projekts geladen wird, muss die Kern-Editor explizit durch das VSPackage aufgerufen werden.

 Weitere Informationen zu den Kern-Editor, finden Sie unter [innerhalb der Kern-Editor](../extensibility/inside-the-core-editor.md).

## <a name="see-also"></a>Siehe auch
- [In der Kern-editor](../extensibility/inside-the-core-editor.md)
- [Instanziieren Sie die Kern-Editor, indem Sie die legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)