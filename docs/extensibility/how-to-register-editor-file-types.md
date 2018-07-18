---
title: 'Vorgehensweise: Registrieren von Dateitypen-Editor | Microsoft Docs'
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4ac67139de317c15d4e85be43f7dace132373257
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129169"
---
# <a name="how-to-register-editor-file-types"></a>Vorgehensweise: Registrieren von Dateitypen-Editor
Am einfachsten Editor Dateitypen registrieren wird mithilfe von die Registrierungsattribute, die als Teil der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] managed Package Framework (MPF)-Klassen. Wenn Sie das Paket in systemeigenen implementieren [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], Sie können auch eine Registrierungsdatei, die dem Editor und die zugehörigen Erweiterungen registriert schreiben.

## <a name="registration-using-mpf-classes"></a>Die Registrierung mithilfe von MPF-Klassen

#### <a name="to-register-editor-file-types-using-mpf-classes"></a>So registrieren Editor Dateitypen, die mithilfe von MPF-Klassen

1.  Geben Sie die <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> Klasse mit den entsprechenden Parametern für den Editor in der Ihr VSPackage-Klasse.

    ```
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",
         TemplateDir = "..\\..\\Templates",
         NameResourceID = 106)]
    ```

     Wobei ". Beispiel"ist die Erweiterung, die für diesen Editor registriert ist, und"32"ist die Prioritätsstufe.

     Die `projectGuid` ist die GUID für verschiedene Dateitypen, definiert <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Der Typ der beliebigen Datei wird bereitgestellt, so, dass die resultierende Datei nicht abgelaufen ist, Teil des Buildprozesses sein.

     `TemplateDir` Stellt den Ordner, der die Dateien enthält, die mit dem Editor für verwaltete grundlegende Beispiel enthalten sind.

     `NameResourceID` in der Datei Resources.h des Projekts BasicEditorUI definiert ist, und identifiziert den Editor als "Meine Editor".

2.  Überschreiben Sie die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>-Methode.

     In der Implementierung von der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> -Methode, rufen die <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> Methode und übergeben Sie die Instanz von der Editorfactory als unten veranschaulicht.

    ```csharp
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

     Dieser Schritt wird die Editor-Factory und die Erweiterungen der Editor-Datei registriert.

3.  Aufheben der Registrierung die editorfactorys.

     Editorfactorys werden automatisch aufgehoben, wenn das VSPackage verworfen wird. Wenn die Editor-Factoryobjekt implementiert die <xref:System.IDisposable> -Schnittstelle, die `Dispose` Methode wird aufgerufen, nachdem die Factory mit aufgehoben wurde, hat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="registration-using-a-registry-script"></a>Registrierung mithilfe eines Skripts für die Registrierung
 Registrieren von editorfactorys und Dateitypen in systemeigenen [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] erfolgt mithilfe eines Skripts für die Registrierung um in der Windows-Registrierung zu schreiben, wie im folgenden veranschaulicht.

### <a name="to-register-editor-file-types-using-a-registry-script"></a>Editor-Dateitypen, die eine Registrierungsdatei mit registrieren

1.  Definieren Sie in Ihrem Registrierungsskript die Editor-Factory und die Editor-Factory GUID-Zeichenfolge ein, entsprechend der `GUID_BscEditorFactory` Abschnitt das folgende Registrierungsskript. Außerdem definieren Sie die Erweiterung und die Priorität der Editor-Erweiterung:

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

     Die Editor-Erweiterung in diesem Beispiel wird als ".rtf" identifiziert, und seine Priorität ist "50". Die GUID-Zeichenfolgen werden in Resource.h-Datei des Beispielprojekts BscEdit definiert.

2.  Registrieren Sie das VSPackage.

3.  Registrieren Sie die Editor-Factory.

     Die Editor-Factory ist registriert, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Implementierung.

    ```cpp
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