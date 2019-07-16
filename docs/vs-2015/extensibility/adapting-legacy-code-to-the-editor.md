---
title: Anpassen von Legacycode in den Editor | Microsoft-Dokumentation
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184918"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Anpassen von Legacycode für den Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio-Editor verfügt über viele Funktionen, die Sie über vorhandenen Codekomponenten zugreifen können. Die folgenden Anweisungen zeigen, wie Sie das Anpassen von nicht-MEF-Komponente, z. B. einem VSPackage, Editor-Funktionen nutzen. Die Anweisungen veranschaulicht auch, Adapter zu verwenden, um die Dienste des Editors in verwaltetem und nicht verwaltetem Code abzurufen.  
  
## <a name="editor-adapters"></a>Editor für Adapter  
 Editor für Adapter oder Shims sind Wrapper für editorobjekte, die auch die Klassen und Schnittstellen verfügbar machen die <xref:Microsoft.VisualStudio.TextManager.Interop> API. Sie können die Adapter zwischen Diensten mit nicht-Editor bewegen, Visual Studio-Shell-Befehle und Editor-Dienste verwenden. (Dies ist wie der Editor in Visual Studio derzeit gehostet wird.) Adapter ermöglichen auch die ältere, Editoren und Sprachen Service-Erweiterungen in Visual Studio ordnungsgemäß funktioniert.  
  
## <a name="using-editor-adapters"></a>Mithilfe von Editor-Adaptern  
 Die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> bietet Methoden, die zwischen der neue Editor-Schnittstellen und die legacy-Schnittstellen zu wechseln und außerdem Methoden zum Erstellen von Adaptern.  
  
 Wenn Sie diesen Dienst in einer MEF-Komponente verwenden, können Sie den Dienst wie folgt importieren.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Wenn Sie diesen Dienst in einer nicht-MEF-Komponente verwenden möchten, führen Sie die Anweisungen im Abschnitt "Mithilfe von Visual Studio-Editor-Dienste in einer nicht-MEF-Komponente" weiter unten in diesem Thema.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Umschalten zwischen der neuen Editor-API und die Legacy-API  
 Verwenden Sie die folgenden Methoden, um zwischen einem editorobjekt und einem legacy-Schnittstelle zu wechseln.  
  
|Methode|Umwandeln|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.Text.ITextBuffer> auf eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> auf eine <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> auf eine <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView> auf eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Konvertiert eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> auf eine <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Erstellen von Adaptern  
 Verwenden Sie die folgenden Methoden, um Adapter für legacy-Schnittstellen zu erstellen.  
  
|Methode|Umwandeln|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Erstellt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> für einen angegebenen <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Erstellt eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Erstellt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Erstellen von Adaptern in nicht verwaltetem Code  
 Alle Adapterklassen werden registriert, um lokale gemeinsam erstellbares und kann instanziiert werden, indem die `VsLocalCreateInstance()` Funktion.  
  
 Alle Adapter werden mithilfe von GUIDs, die in der Datei vsshlids.h definiert sind erstellt das... \VisualStudioIntegration\Common\Inc\-Ordner, der Visual Studio SDK-Installation. Verwenden Sie zum Erstellen einer Instanz von VsTextBufferAdapter den folgenden Code ein.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Erstellen von Adaptern in verwaltetem Code  
 In verwaltetem Code können Sie die Adapter gemeinsam auf die gleiche Weise wie für nicht verwalteten Code beschrieben erstellen. Sie können auch einen MEF-Dienst, mit dem Sie die Erstellung von / Interaktion mit Adaptern. Auf diese Weise erhalten Sie einen Adapter ermöglicht eine präzisere Kontrolle als bei der Erstellung gemeinsam sind.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>So erstellen Sie einen Adapter für IVsTextView  
  
1. Fügen Sie einen Verweis auf Microsoft.VisualStudio.Editor.dll hinzu. Stellen Sie sicher, dass `CopyLocal` nastaven NA hodnotu `false`.  
  
2. Instanziieren der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>wie folgt.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Rufen Sie die `CreateX()`-Methode auf.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Mithilfe der Visual Studio-Editor direkt aus nicht verwaltetem Code  
 Die Microsoft.VisualStudio.Platform.VSEditor-Namespace und den Namespace Microsoft.VisualStudio.Platform.VSEditor.Interop COM callable Schnittstellen als IVx * Schnittstellen verfügbar machen. Beispielsweise ist die Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer-Schnittstelle der COM-Version von der <xref:Microsoft.VisualStudio.Text.ITextBuffer> Schnittstelle. Von der `IVxTextBuffer`, Sie können erhalten Sie Zugriff auf den Puffer-Momentaufnahmen, ändern Sie den Puffer, überwachen Sie textänderung Ereignisse im Puffer und nachverfolgung Punkte und Spannen zu erstellen. Die folgenden Schritte zeigen, wie Sie den Zugriff auf eine `IVxTextBuffer` aus einem `IVsTextBuffer`.  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Um einen IVxTextBuffer zu erhalten.  
  
1. Die Definitionen für die IVx *-Schnittstellen sind in der VSEditor.h-Datei in das... \VisualStudioIntegration\Common\Inc\-Ordner, der Visual Studio SDK-Installation.  
  
2. Instanziiert der folgende Code einen Textpuffer mithilfe der `IVsUserData->GetData()` Methode. In den folgenden Code `pData` ist ein Zeiger auf ein `IVsUserData` Objekt.  
  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Verwenden von Visual Studio-Editor-Diensten in nicht-MEF-Komponente  
 Wenn Sie eine vorhandene verwaltete Codekomponente, die keine MEF verwendet haben, und Sie die Dienste von Visual Studio-Editor verwenden möchten, müssen Sie fügen einen Verweis auf die Assembly mit dem ComponentModelHost VSPackage und seine SComponentModel-Dienst abrufen.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Nutzen Sie Visual Studio-Editor-Komponenten aus einer nicht-MEF-Komponente  
  
1. Fügen Sie einen Verweis auf die Microsoft.VisualStudio.ComponentModelHost.dll-Assembly in das... Ordner "\Common7\IDE\" von Visual Studio-Installation. Stellen Sie sicher, dass `CopyLocal` nastaven NA hodnotu `false`.  
  
2. Hinzufügen eine privaten `IComponentModel` Member der Klasse, die in der Visual Studio-Editor-Diensten, wie folgt verwendet werden soll.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Instanziieren Sie das Komponentenmodell bei der Initialisierungsmethode für die Komponente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Danach erhalten Sie eine Visual Studio-Editor Dienste durch Aufrufen der `IComponentModel.GetService<T>()` Methode für den Dienst werden sollen.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
