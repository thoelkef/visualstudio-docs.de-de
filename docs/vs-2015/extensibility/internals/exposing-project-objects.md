---
title: Verfügbar machen von Projekt Objekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f40c523c058bf215cc4574b3aa4a2e038c833beb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196645"
---
# <a name="exposing-project-objects"></a>Verfügbarmachen von Projektobjekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Benutzerdefinierte Projekttypen können Automatisierungs Objekte bereitstellen, um den Zugriff auf das Projekt mithilfe von Automatisierungs Schnittstellen zuzulassen. Jeder Projekttyp soll das standardmäßige <xref:EnvDTE.Project> Automatisierungs Objekt bereitstellen, auf das von zugegriffen wird <xref:EnvDTE.Solution> , das eine Auflistung aller Projekte enthält, die in der IDE geöffnet sind. Es wird erwartet, dass jedes Element im Projekt durch ein-Objekt verfügbar gemacht wird, auf das <xref:EnvDTE.ProjectItem> mit zugegriffen wird <xref:EnvDTE.Project.ProjectItems> . Zusätzlich zu diesen Standard Automatisierungs Objekten können Projekte auch projektspezifische Automatisierungs Objekte anbieten.  
  
 Sie können benutzerdefinierte Automatisierungs Objekte auf Stamm Ebene erstellen, auf die Sie mithilfe von oder über das Stamm-DTE-Objekt mit der spät Bindung zugreifen können `DTE.<customeObjectName>` `DTE.GetObject(“<customObjectName>”)` . Visual C++ erstellt beispielsweise eine C++-projektspezifische Projekt Auflistung mit dem Namen "vcprojects", auf die Sie mit DTE zugreifen können. Vcprojects oder DTE. GetObject ("vcprojects"). Sie können auch ein Project. Object-Objekt erstellen, das für den Projekttyp eindeutig ist, ein Project. CodeModel-Objekt, das für das am meisten abgeleitete Objekt abgefragt werden kann. dabei handelt es sich um ein ProjectItem-Objekt, das ProjectItem. Object und ProjectItem. FileCodeModel verfügbar macht.  
  
 Es ist eine gängige Konvention für-Projekte, eine benutzerdefinierte projektspezifische Projekt Auflistung verfügbar zu machen. Erstellt beispielsweise [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] eine C++ spezifische Projekt Auflistung, auf die Sie dann mithilfe von `DTE.VCProjects` oder zugreifen können `DTE.GetObject("VCProjects")` . Sie können auch ein- `Project.Object` Objekt erstellen, das für den Projekttyp eindeutig ist, ein `Project.CodeModel` -Objekt, das für das am meisten abgeleitete Objekt, ein-Objekt, das verfügbar macht, `ProjectItem` `ProjectItem.Object` und ein-Objekt abgefragt werden kann `ProjectItem.FileCodeModel` .  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>So tragen Sie ein VSPackage-spezifisches Objekt für ein Projekt an  
  
1. Fügen Sie der pkgdef-Datei des VSPackage die entsprechenden Schlüssel hinzu.  
  
     Hier sind z. b. die pkgdef-Einstellungen für das Sprachprojekt C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2. Implementieren Sie den Code in der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode, wie im folgenden Beispiel gezeigt.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     Im Code `g_wszAutomationProjects` ist der Name der Projekt Auflistung. Die `GetAutomationProjects` -Methode erstellt ein Objekt, das die `Projects` -Schnittstelle implementiert und einen `IDispatch` Zeiger auf das aufrufende Objekt zurückgibt, wie im folgenden Codebeispiel gezeigt.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     Wählen Sie einen eindeutigen Namen für das Automatisierungs Objekt aus. Namenskonflikte sind unvorhersehbar, und Konflikte bewirken, dass ein in Konflikt stehender Objektname willkürlich ausgelöst wird, wenn mehrere Projekttypen denselben Namen verwenden. Sie sollten Ihren Firmennamen oder einen eindeutigen Aspekt des Produkt namens in den Namen des Automatisierungs Objekts einschließen.  
  
     Das benutzerdefinierte `Projects` Sammlungsobjekt ist ein praktischer Einstiegspunkt für den verbleibenden Teil Ihres Projekt Automatisierungs Modells. Auf das Projekt Objekt kann auch über die Projekt Auflistung zugegriffen werden <xref:EnvDTE.Solution> . Nachdem Sie den entsprechenden Code und die Registrierungseinträge erstellt haben, die Consumern Auflistungs Objekte bereitstellen `Projects` , muss die Implementierung verbleibende Standardobjekte für das Projekt Modell bereitstellen. Weitere Informationen finden Sie unter [Projekt Modellierung](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
