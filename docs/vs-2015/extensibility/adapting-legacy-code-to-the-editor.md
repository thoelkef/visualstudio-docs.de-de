---
title: Anpassen von Legacy Code an den Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184918"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Anpassen von Legacycode für den Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Visual Studio-Editor verfügt über viele Funktionen, auf die Sie über vorhandene Code Komponenten zugreifen können. Die folgenden Anweisungen zeigen, wie Sie eine nicht-MEF-Komponente (z. b. ein VSPackage) anpassen können, um die Editor-Funktionalität zu nutzen. Außerdem wird erläutert, wie Adapter verwendet werden, um die Dienste des Editors in verwaltetem und nicht verwaltetem Code zu erhalten.  
  
## <a name="editor-adapters"></a>Editor-Adapter  
 Editor-Adapter oder Shims sind Wrapper für Editor-Objekte, die auch die Klassen und Schnittstellen in der <xref:Microsoft.VisualStudio.TextManager.Interop> API verfügbar machen. Sie können die Adapter verwenden, um zwischen nicht-Editor-Diensten zu wechseln, z. b. Visual Studio Shell-Befehle und Editor-Dienste. (Auf diese Weise wird der Editor zurzeit in Visual Studio gehostet.) Mit Adaptern können auch ältere Editor-und Sprachdienst Erweiterungen in Visual Studio ordnungsgemäß funktionieren.  
  
## <a name="using-editor-adapters"></a>Verwenden von Editor Adaptern  
 Die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> stellt Methoden bereit, die zwischen den neuen Editor Schnittstellen und den Legacy Schnittstellen wechseln, sowie Methoden, mit denen Adapter erstellt werden.  
  
 Wenn Sie diesen Dienst in einem MEF-Komponenten Teil verwenden, können Sie den Dienst wie folgt importieren.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Wenn Sie diesen Dienst in einer nicht-MEF-Komponente verwenden möchten, befolgen Sie die Anweisungen im Abschnitt "Verwenden der Visual Studio-Editor-Dienste in einer nicht-MEF-Komponente" weiter unten in diesem Thema.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Wechseln zwischen der neuen Editor-API und der Legacy-API  
 Verwenden Sie die folgenden Methoden, um zwischen einem Editor-Objekt und einer Legacy Schnittstelle zu wechseln.  
  
|Methode|Konvertierung|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Konvertiert einen <xref:Microsoft.VisualStudio.Text.ITextBuffer> in einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Konvertiert einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> in einen <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Konvertiert einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> in einen <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Konvertiert einen <xref:Microsoft.VisualStudio.Text.Editor.ITextView> in einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Konvertiert einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in einen <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Erstellen von Adaptern  
 Verwenden Sie die folgenden Methoden zum Erstellen von Adaptern für Legacy Schnittstellen.  
  
|Methode|Konvertierung|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Erstellt einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> für einen angegebenen <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Erstellt einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> für einen <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Erstellen von Adaptern in nicht verwaltetem Code  
 Alle Adapter Klassen sind für die lokale zusammen fügende Funktion registriert und können mithilfe der-Funktion instanziiert werden `VsLocalCreateInstance()` .  
  
 Alle Adapter werden mithilfe der GUIDs erstellt, die in der vsshlids. h-Datei in der definiert sind. Ordner \visualstudiointegration\common\inc\ der Visual Studio SDK-Installation. Um eine Instanz von vstextbufferadapter zu erstellen, verwenden Sie den folgenden Code.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Erstellen von Adaptern in verwaltetem Code  
 In verwaltetem Code können Sie die Adapter auf die gleiche Weise wie für nicht verwalteten Code erstellen. Sie können auch einen MEF-Dienst verwenden, mit dem Sie Adapter erstellen und mit diesen interagieren können. Diese Art, einen Adapter zu erhalten, ermöglicht eine präzisere Steuerung als bei der Erstellung.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>So erstellen Sie einen Adapter für IVsTextView  
  
1. Fügen Sie einen Verweis auf Microsoft.VisualStudio.Editor.dll hinzu. Stellen Sie sicher, dass `CopyLocal` auf `false` festgelegt ist.  
  
2. Instanziieren Sie <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> wie folgt.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Rufen Sie die `CreateX()` -Methode auf.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Verwenden des Visual Studio-Editors direkt aus nicht verwaltetem Code  
 Der Microsoft. VisualStudio. Platform. VSEditor-Namespace und der Microsoft. VisualStudio. Platform. VSEditor. Interop-Namespace machen com-Aufruf Bare Schnittstellen als ivx *-Schnittstellen verfügbar. Beispielsweise ist die Microsoft. VisualStudio. Platform. VSEditor. Interop. ivxtextbuffer-Schnittstelle die com-Version der <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle. Im `IVxTextBuffer` können Sie auf die Puffer Momentaufnahmen zugreifen, den Puffer ändern, auf Text Änderungs Ereignisse im Puffer lauschen und Überwachungspunkte und spannen erstellen. Die folgenden Schritte zeigen, wie Sie über einen auf einen zugreifen `IVxTextBuffer` `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>So erhalten Sie einen ivxtextbuffer  
  
1. Die Definitionen für die ivx *-Schnittstellen befinden sich in der Datei "VSEditor. h" im. Ordner \visualstudiointegration\common\inc\ der Visual Studio SDK-Installation.  
  
2. Der folgende Code instanziiert einen Text Puffer mithilfe der- `IVsUserData->GetData()` Methode. Im folgenden Code `pData` ist ein Zeiger auf ein- `IVsUserData` Objekt.  
  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Verwenden der Visual Studio-Editor-Dienste in einer nicht-MEF-Komponente  
 Wenn Sie über eine vorhandene Komponente für verwalteten Code verfügen, die MEF nicht verwendet, und Sie die Dienste von Visual Studio-Editor verwenden möchten, müssen Sie einen Verweis auf die Assembly hinzufügen, die das VSPackage componentmodelhost enthält, und den scomponentmodel-Dienst erhalten.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>So verwenden Sie Visual Studio-Editor-Komponenten aus einer nicht-MEF-Komponente  
  
1. Fügen Sie in der Microsoft.VisualStudio.ComponentModelHost.dll-Assembly einen Verweis hinzu. Ordner "\common7\ide\" der Visual Studio-Installation. Stellen Sie sicher, dass `CopyLocal` auf `false` festgelegt ist.  
  
2. Fügen `IComponentModel` Sie der Klasse, in der Sie die Visual Studio-Editor-Dienste verwenden möchten, wie folgt ein privates Mitglied hinzu.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Instanziieren Sie das Komponentenmodell in der Initialisierungs Methode für die Komponente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Danach können Sie einen der Visual Studio-Editor-Dienste abrufen, indem Sie die- `IComponentModel.GetService<T>()` Methode für den gewünschten Dienst aufrufen.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
