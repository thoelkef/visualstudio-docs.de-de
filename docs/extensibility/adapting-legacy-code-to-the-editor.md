---
title: "Anpassen von Legacycode in den Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Adapter"
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Anpassen von Legacycode in den Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Visual Studio\-Editor verfügt über viele Features, die Sie vorhandenen Codekomponenten zugreifen können. Die folgenden Schritte zeigen, wie nicht\-MEF\-Komponente, z. B. ein VSPackage\-Editor\-Funktionen nutzen können. Die Anweisungen zeigen auch, wie Adapter verwenden, um die Dienste des Editors in verwaltetem und nicht verwaltetem Code abgerufen.  
  
## Editor\-Adapter  
 Editor\-Adapter oder Shims, sind Wrapper für editorobjekte, die auch die Klassen und Schnittstellen verfügbar machen die <xref:Microsoft.VisualStudio.TextManager.Interop> API. Sie können die Adapter Bewegen zwischen nicht\-Editor, Visual Studio\-Shell\-Befehle und Editor Dienste verwenden. \(Dies ist wie der Editor in Visual Studio derzeit gehostet wird.\) Adapter ermöglichen auch die legacy\-Editor, und Language Service\-Erweiterungen in Visual Studio korrekt funktioniert.  
  
## Editor\-Adapter  
 Die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> bietet Methoden, die zwischen der neue Editor\-Schnittstellen und die legacy\-Schnittstellen wechseln und außerdem Methoden zum Erstellen von Adaptern.  
  
 Wenn Sie diesen Dienst in einer MEF\-Komponente verwenden, können Sie den Dienst wie folgt importieren.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Wenn Sie diesen Dienst in einer nicht\-MEF\-Komponente verwenden möchten, gehen Sie im Abschnitt "Mithilfe von Visual Studio\-Editor\-Dienste in einer nicht\-MEF\-Komponente" weiter unten in diesem Thema.  
  
## Wechseln zwischen der neuen Editor\-API und die Legacy\-API  
 Verwenden Sie die folgenden Methoden zum Wechseln zwischen ein Editor\-Objekt und ein legacy\-Schnittstelle.  
  
|Methode|Umwandeln|  
|-------------|---------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Konvertiert ein <xref:Microsoft.VisualStudio.Text.ITextBuffer> zu einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Konvertiert ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> zu einer <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Konvertiert ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> zu einer <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Konvertiert ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView> zu einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Konvertiert ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zu einer <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## Erstellen von Adaptern  
 Verwenden Sie die folgenden Methoden zum Erstellen von Adaptern für legacy\-Schnittstellen.  
  
|Methode|Umwandeln|  
|-------------|---------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Erstellt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Erstellt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> für einen angegebenen <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Erstellt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Erstellt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Erstellt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Erstellt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## Erstellen von Adaptern in nicht verwaltetem Code  
 Alle Adapterklassen werden registriert, damit lokale zusammen erstellt und instanziiert werden kann, mithilfe der `VsLocalCreateInstance()` Funktion.  
  
 Alle Adapter werden mithilfe der GUIDs, die in der Datei vsshlids.h definiert sind erstellt das... \\VisualStudioIntegration\\Common\\Inc\\\-Ordner, der die Installation von Visual Studio SDK. Um eine Instanz von VsTextBufferAdapter zu erstellen, verwenden Sie den folgenden Code.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## Erstellen von Adaptern in verwaltetem Code  
 In verwaltetem Code können Sie die Adapter gemeinsam auf die gleiche Weise wie unter beschrieben für nicht verwalteten Code erstellen. Sie können auch einen MEF\-Dienst, mit dem Sie das Erstellen von und interagieren mit Adaptern. Auf diese Weise erhalten Sie einen Adapter ermöglicht eine präzisere Kontrolle als bei der Erstellung gemeinsam sind.  
  
#### So erstellen Sie einen Adapter für IVsTextView  
  
1.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Editor.dll hinzu. Stellen Sie sicher, dass `CopyLocal` Wert `false`.  
  
2.  Instanziieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, wie folgt.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Rufen Sie die `CreateX()`\-Methode auf.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## Mithilfe der Visual Studio\-Editor direkt aus dem nicht verwalteten Code  
 Der Microsoft.VisualStudio.Platform.VSEditor\-Namespace und den Namespace Microsoft.VisualStudio.Platform.VSEditor.Interop COM\-aufrufbare Schnittstellen als IVx \* Schnittstellen verfügbar gemacht. Die Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer\-Schnittstelle ist z. B. die COM\-Version von der <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle. Aus der `IVxTextBuffer`, Sie erhalten Sie Zugriff auf die Momentaufnahmen Puffer, den Puffer ändern, Lauschen auf Text\-Ereignisse im Puffer und Überwachungspunkte und Spannen erstellen. Die folgenden Schritte zeigen, wie für den Zugriff auf ein `IVxTextBuffer` aus einem `IVsTextBuffer`.  
  
#### Ein IVxTextBuffer abrufen  
  
1.  Die Definitionen für die IVx \*\-Schnittstellen sind in der Datei VSEditor.h in das... \\VisualStudioIntegration\\Common\\Inc\\\-Ordner, der die Installation von Visual Studio SDK.  
  
2.  Der folgende Code instanziiert einen Textpuffer mit der `IVsUserData->GetData()` Methode. Im folgenden Code wird `pData` ist ein Zeiger auf ein `IVsUserData` Objekt.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## Verwenden von Visual Studio\-Editor\-Diensten in nicht MEF\-Komponente  
 Sie haben eine vorhandene verwaltete Codekomponente, die keine MEF verwendet, und die Dienste von Visual Studio\-Editor verwenden möchten, müssen fügen Sie einen Verweis auf die Assembly, die das ComponentModelHost VSPackage enthält und seine SComponentModel\-Dienst.  
  
#### Visual Studio\-Editor\-Komponenten von nicht\-MEF\-Komponente verarbeitet  
  
1.  Fügen Sie einen Verweis auf die Assembly Microsoft.VisualStudio.ComponentModelHost.dll in das... \\Common7\\IDE\\ Ordner der Visual Studio\-Installation. Stellen Sie sicher, dass `CopyLocal` Wert `false`.  
  
2.  Fügen Sie eine Private `IComponentModel` Member der Klasse, die in der Visual Studio\-Editor\-Dienste wie folgt verwendet werden soll.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Instanziieren Sie das Komponentenmodell in der Initialisierungsmethode für die Komponente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Danach erhalten Sie eine Visual Studio\-Editor Dienste durch Aufrufen der `IComponentModel.GetService<T>()` \-Methode für den gewünschten Dienst.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```