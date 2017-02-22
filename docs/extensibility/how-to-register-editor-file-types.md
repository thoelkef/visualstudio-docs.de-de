---
title: "Gewusst wie: Registrieren von Dateitypen-Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Registrierung von Dateitypen"
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Registrieren von Dateitypen-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die einfachste Möglichkeit, dateitypen Editor registriert ist, indem die Registrierung von Attributen verwendet, die als Teil der bereitgestellten Klassen [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] verwalteten Paketframeworks \(MPF\).  Wenn Sie das Paket im systemeigenen [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]implementieren, können Sie eine Registrierung auch Skripts schreiben, der den Editor und die zugehörigen Erweiterungen registriert.  
  
## Registrierung mithilfe MPF\-Klassen  
  
#### So registrieren MPF\-Klassen mithilfe dateitypen Editor  
  
1.  Geben Sie die <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>\-Klasse mit den entsprechenden Parametern für den Editor in der Klasse VSPackages.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Wo „. Beispiel“ ist die Erweiterung, die für diesen Editor registriert ist, und die Prioritätsebene ist „32 ".  
  
     `projectGuid` ist die GUID für verschiedene Dateitypen, definiert in <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>.  Der andere Dateityp wird bereitgestellt, sodass die resultierende Datei nicht Teil des Buildprozesses sein wird.  
  
     `TemplateDir` stellt den Ordner dar, der die Vorlagendateien enthält, die mit dem verwalteten einfachen Editor Beispiel enthalten sind.  
  
     `NameResourceID` wird in der Resources.h\-Datei des BasicEditorUI\-Projekts definiert und den Editor als „My Notepad“ bezeichnet.  
  
2.  Überschreiben der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>\-Methode.  
  
     In der Implementierung der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>\-Methode, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>\-Methode auf, und übergeben Sie die Instanz der Editor factorys, wie unten dargestellt.  
  
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
  
     Dieser Schritt der Editor registriert und der Editor. dateierweiterungen factory  
  
3.  Heben Sie die Kommentierung Editor factorys aufgehoben.  
  
     factorys Editor automatisch werden, deren Registrierung aufgehoben, wenn ein VSPackage freigegeben wird.  factory Editor Wenn das Objekt die <xref:System.IDisposable>\-Schnittstelle implementiert, wird ihre `Dispose`\-Methode aufgerufen, nachdem die Factory [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]mit deren Registrierung aufgehoben wurde.  
  
## Registrierung mithilfe eines Registrierungs\-Skripts  
 Das Registrieren von Dateitypen und \- factorys Editor im systemeigenen [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] ist mit einem Registrierungsdaten skripts auf Fenster, die Registrierung geschrieben werden soll, wie durch den folgenden Code veranschaulicht.  
  
#### So Editor mithilfe eines dateitypen skripts Registrierung registrieren  
  
1.  Definieren Sie die Registrierung von Skripts im Editor factory und die Zeichenfolge der Editor factorys GUID wie im folgenden Abschnitt des `GUID_BscEditorFactory` Registrierungsdaten skripts gezeigt.  Außerdem definieren Sie die Erweiterung und die Priorität der Editor Namespaceerweiterung:  
  
    ```  
  
                NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions             {                 val rtf = d 50             }  
        }  
    }  
    ```  
  
     Der Editor dateierweiterung in diesem Beispiel identifiziert wird, z. B. „.rtf“ und ihre Priorität „50 " ist.  Die GUID\-Zeichenfolgen werden in BscEdit\-Beispiel Resource.h\-Datei vom projekts definiert.  
  
2.  Registriert ein VSPackage.  
  
3.  Registrieren Sie den Editor factory.  
  
     Die Editor factory wird in der Implementierung des <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> registriert.  
  
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
  
     Die GUID\-Zeichenfolgen werden in Resource.h\-Datei vom BscEdit\-Projekts definiert.