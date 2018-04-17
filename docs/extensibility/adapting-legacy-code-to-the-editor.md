---
title: Anpassen von Legacycode auf den Editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e90a0f8ba27199e3837c59cd7980f027d0485a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="adapting-legacy-code-to-the-editor"></a>Anpassen von Legacycode auf den Editor
Der Visual Studio-Editor verfügt über zahlreiche Funktionen, die Sie über vorhandene Codekomponenten zugreifen können. Die folgenden Anweisungen zeigen, wie eine nicht MEF-Komponente, z. B. ein VSPackage-Editor-Funktionen nutzen angepasst werden kann. Die Anweisungen zeigen auch, wie Adapter verwenden, um die Dienste des Editors in verwaltetem und nicht verwaltetem Code abzurufen.  
  
## <a name="editor-adapters"></a>Editor-Adapter  
 Editor-Adapter oder Shims, davon sind Wrapper für Editor-Objekte, die auch die Klassen und Schnittstellen in verfügbar machen die <xref:Microsoft.VisualStudio.TextManager.Interop> API. Sie können die Adapter, z. B. zwischen nicht-Editor-Diensten zu verschieben, Visual Studio-Shell-Befehle und Editor Dienste verwenden. (Dies ist wie der Editor in Visual Studio derzeit gehostet wird.) Adapter ermöglichen außerdem die legacy-Editor und Language Service-Erweiterungen in Visual Studio korrekt funktioniert.  
  
## <a name="using-editor-adapters"></a>Mithilfe von Editor-Adaptern  
 Die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> bietet Methoden, die zwischen dem neuen Editor und älteren Schnittstellen wechseln und außerdem Methoden zum Erstellen von Adaptern.  
  
 Wenn Sie diesen Dienst in einer MEF-Komponente verwenden, können Sie den Dienst wie folgt importieren.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Wenn Sie diesen Dienst in einer nicht-MEF-Komponente verwenden möchten, folgen Sie den Anweisungen im Abschnitt "Mithilfe von Visual Studio-Editor-Dienste in einer nicht-MEF-Komponente" weiter unten in diesem Thema.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Umschalten zwischen der neuen API zum Editor und die Legacy-API  
 Anhand der folgenden Methoden zum Wechseln zwischen ein Editor-Objekt und ein legacy-Schnittstelle.  
  
|Methode|Umwandeln|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.Text.ITextBuffer> auf eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> auf eine <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> auf eine <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView> auf eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> auf eine <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Erstellen von Adaptern  
 Anhand der folgenden Methoden zum Erstellen von Adaptern für legacy-Schnittstellen.  
  
|Methode|Umwandeln|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> für einen angegebenen <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Erstellen von Adaptern in nicht verwaltetem Code  
 Alle Adapterklassen werden registriert, um lokale werden gemeinsam erstellbares und instanziiert werden kann, mithilfe der `VsLocalCreateInstance()` Funktion.  
  
 Alle Adapter werden mithilfe der GUIDs, die in der Datei vsshlids.h definiert sind erstellt die... \VisualStudioIntegration\Common\Inc\ Ordner der Installation des Visual Studio SDK. Um eine Instanz von VsTextBufferAdapter zu erstellen, verwenden Sie den folgenden Code.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Erstellen von Adaptern in verwaltetem Code  
 In verwaltetem Code können Sie die Adapter gemeinsam auf die gleiche Weise wie für nicht verwalteten Code beschrieben erstellen. Sie können auch einen MEF-Dienst, mit dem Sie das Erstellen von und interagieren mit Adaptern. Auf diese Weise erhalten Sie einen Adapter ermöglicht eine präzisere Kontrolle als bei der Erstellung gemeinsam sind.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>So erstellen Sie einen Adapter für IVsTextView  
  
1.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Editor.dll. Stellen Sie sicher, dass `CopyLocal` festgelegt ist, um `false`.  
  
2.  Instanziieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>wie folgt.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Rufen Sie die `CreateX()`-Methode auf.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Verwenden im Visual Studio-Editor direkt aus nicht verwaltetem Code  
 Der Microsoft.VisualStudio.Platform.VSEditor-Namespace und den Namespace Microsoft.VisualStudio.Platform.VSEditor.Interop aufrufbaren COM Schnittstellen als IVx * Schnittstellen verfügbar gemacht. Beispielsweise ist die Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer-Schnittstelle der COM-Version von der <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle. Aus der `IVxTextBuffer`, Sie erhalten Zugriff auf die Momentaufnahmen Puffer, ändern Sie den Puffer, Lauschen textänderung Ereignissen im Puffer und Überwachungspunkte und Spannen erstellen. Die folgenden Schritte zeigen, wie Sie den Zugriff auf eine `IVxTextBuffer` aus einem `IVsTextBuffer`.  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Ein IVxTextBuffer abrufen  
  
1.  Die Definitionen für die Schnittstellen der IVx * sind in der Datei VSEditor.h in der... \VisualStudioIntegration\Common\Inc\ Ordner der Installation des Visual Studio SDK.  
  
2.  Instanziiert der folgende Code einen Textpuffer mithilfe der `IVsUserData->GetData()` Methode. Im folgenden Code `pData` ist ein Zeiger auf ein `IVsUserData` Objekt.  
  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Mithilfe von Visual Studio-Editor-Dienste in einer nicht-MEF-Komponente  
 Wenn Sie eine vorhandene verwaltetem Code-Komponente, die keine MEF verwendet haben, und Sie die Dienste der Visual Studio-Editor verwenden möchten, müssen Sie fügen einen Verweis auf die Assembly, die das ComponentModelHost VSPackage enthält und dessen SComponentModel-Dienst abrufen.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Visual Studio-Editor-Komponenten von nicht-MEF-Komponente verarbeitet  
  
1.  Fügen Sie einen Verweis auf die Assembly Microsoft.VisualStudio.ComponentModelHost.dll in der... \Common7\IDE\ Ordner der Visual Studio-Installation. Stellen Sie sicher, dass `CopyLocal` festgelegt ist, um `false`.  
  
2.  Hinzufügen eine privaten `IComponentModel` Member der Klasse, die in der Visual Studio-Editor-Dienste wie folgt verwendet werden sollen.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Instanziieren der Komponentenmodell in die Initialisierungsmethode für die Komponente an.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Danach erhalten Sie eine Visual Studio-Editor Dienste durch Aufrufen der `IComponentModel.GetService<T>()` Methode für den gewünschten Dienst.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```