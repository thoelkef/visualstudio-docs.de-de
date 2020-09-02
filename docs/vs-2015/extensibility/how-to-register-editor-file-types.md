---
title: 'Vorgehensweise: Registrieren von Editor-Dateitypen | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204115"
---
# <a name="how-to-register-editor-file-types"></a>Vorgehensweise: Registrieren von Editordateitypen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die einfachste Möglichkeit zum Registrieren von Editor-Dateitypen ist die Verwendung der Registrierungs Attribute, die als Teil der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] MPF-Klassen (Managed Package Framework) bereitgestellt werden. Wenn Sie das Paket in System eigenem System implementieren [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , können Sie auch ein Registrierungs Skript schreiben, das den Editor und die zugehörigen Erweiterungen registriert.  
  
## <a name="registration-using-mpf-classes"></a>Registrierung mit MPF-Klassen  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>So registrieren Sie Editor-Dateitypen mithilfe von MPF-Klassen  
  
1. Stellen Sie die- <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> Klasse mit den entsprechenden Parametern für Ihren Editor in der-Klasse des VSPackages bereit.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Dabei ist ". Beispiel: "ist die Erweiterung, die für diesen Editor registriert ist, und" 32 "ist die Prioritätsstufe.  
  
     `projectGuid`Ist die GUID für verschiedene Dateitypen, die in definiert sind <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . Der Dateityp "Sonstige" wird bereitgestellt, sodass die resultierende Datei nicht Teil des Buildprozesses ist.  
  
     `TemplateDir` stellt den Ordner dar, der die Vorlagen Dateien enthält, die im Managed Basic Editor-Beispiel enthalten sind.  
  
     `NameResourceID` wird in der Datei Resources. h des basiceditorui-Projekts definiert und identifiziert den Editor als "My Editor".  
  
2. Überschreiben Sie die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> -Methode.  
  
     Nennen Sie in der Implementierung der- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode die <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> -Methode, und übergeben Sie die Instanz der Editorfactory, wie unten gezeigt.  
  
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
  
     In diesem Schritt werden die Editorfactory und die Editor-Dateierweiterungen registriert.  
  
3. Aufheben der Registrierung der editorfactorys.  
  
     Die Registrierung von editorfactorys wird automatisch aufgehoben, wenn das VSPackage verworfen wird. Wenn das editorfactoryobjekt die- <xref:System.IDisposable> Schnittstelle implementiert, wird die- `Dispose` Methode aufgerufen, nachdem die Registrierung der Factory bei aufgehoben wurde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>Registrierung mithilfe eines Registrierungs Skripts  
 Das Registrieren von editorfactorys und Dateitypen im systemeigenen Modus erfolgt [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] mithilfe eines Registrierungs Skripts zum Schreiben in die Windows-Registrierung, wie im folgenden veranschaulicht.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>So registrieren Sie Editor-Dateitypen mithilfe eines Registrierungs Skripts  
  
1. Definieren Sie in Ihrem Registrierungs Skript die Editorfactory und die Editorfactory-GUID-Zeichenfolge, wie im `GUID_BscEditorFactory` Abschnitt des folgenden Registrierungs Skripts gezeigt. Definieren Sie außerdem die Erweiterung und die Priorität der Editor-Erweiterung:  
  
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
  
     Die Editor-Dateierweiterung in diesem Beispiel wird als RTF identifiziert, und die Priorität ist "50". Die GUID-Zeichen folgen werden in der Datei "Resource. h" des bscedit-Beispielprojekts definiert.  
  
2. Registrieren Sie das VSPackage.  
  
3. Registrieren Sie die Editorfactory.  
  
     Die Editorfactory ist in der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Implementierung registriert.  
  
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
  
     Die GUID-Zeichen folgen werden in der Datei "Resource. h" des bscedit-Projekts definiert.
