---
title: 'Vorgehensweise: Registrieren Sie die Editor-Dateitypen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042040"
---
# <a name="how-to-register-editor-file-types"></a>Vorgehensweise: Register-Editor-Dateitypen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die einfachste Möglichkeit zum Registrieren von Editor-Dateitypen wird mit den Registrierung-Attributen, die als Teil der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] managed Package Framework (MPF)-Klassen. Wenn Sie das Paket in systemeigenen implementieren [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], Sie können auch eine Registrierungsdatei, der den Editor und den verbundenen nebenanschlüssen registriert schreiben.  
  
## <a name="registration-using-mpf-classes"></a>Registrierung mithilfe von MPF-Klassen  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Editor für Dateitypen, die mithilfe von MPF-Klassen zu registrieren  
  
1. Geben Sie die <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> Klasse mit den entsprechenden Parametern für den Editor in der Klasse Ihres VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Wobei ". Beispiel"ist die Erweiterung, die für diesen Editor registriert ist, und"32"wird die Prioritätsstufe.  
  
     Die `projectGuid` ist die GUID für verschiedene Dateitypen, die in definierten <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Die Typ der beliebigen Datei wird bereitgestellt, so, dass die resultierende Datei nicht Teil des Buildprozesses werden soll.  
  
     `TemplateDir` steht für den Ordner, der die Vorlagendateien enthält, die mit dem Editor für verwaltete basic-Beispiel enthalten sind.  
  
     `NameResourceID` in der Datei Resources.h der BasicEditorUI-Projekts definiert ist, und gibt den Editor als "Meine-Editor".  
  
2. Überschreiben Sie die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>-Methode.  
  
     In der Implementierung von der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> -Methode, rufen die <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> Methode und übergeben Sie die Instanz Ihrer Editor-Factory, wie unten veranschaulicht.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Dieser Schritt wird sowohl die Dateierweiterungen für den Editor als auch die Editor-Factory registriert.  
  
3. Aufheben der Registrierung der editorfactorys.  
  
     Editorfactorys werden automatisch aufgehoben, wenn das VSPackage verworfen wird. Wenn der Editor-Factory-Objekt implementiert die <xref:System.IDisposable> -Schnittstelle, die `Dispose` Methode wird aufgerufen, nachdem Sie mit die Factory aufgehoben wurde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="registration-using-a-registry-script"></a>Registrierung mithilfe eines Skripts für die Registrierung  
 Registrieren von editorfactorys und Dateitypen in systemeigenen [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] erfolgt mithilfe eines Skripts für die Registrierung um in der Windows-Registrierung zu schreiben, wie im folgenden dargestellt.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Editor für Dateitypen, die mithilfe eines Skripts für die Registrierung registrieren  
  
1. Definieren Sie in Ihrem Registrierungsskript, die Editor-Factory und die Editorfactory-GUID-Zeichenfolge ein, siehe die `GUID_BscEditorFactory` Abschnitt das folgende Registrierungsskript. Außerdem definieren Sie die Erweiterung und die Priorität der editorerweiterung:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     Die Dateierweiterung "Editor" in diesem Beispiel wird als "RTF" identifiziert, und die Priorität wird auf "50". Die GUID-Zeichenfolgen werden in Resource.h-Datei des Beispielprojekts BscEdit definiert.  
  
2. Registrieren Sie das VSPackage.  
  
3. Die Editor-Factory zu registrieren.  
  
     Die Editor-Factory registriert ist, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Implementierung.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     Die GUID-Zeichenfolgen werden in Resource.h-Datei des Projekts BscEdit definiert.
