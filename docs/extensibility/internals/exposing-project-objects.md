---
title: "Verfügbarmachen von Projektobjekten | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f29ca84669f563da5733c8c07b219d498ccf6ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="exposing-project-objects"></a>Verfügbarmachen von Projektobjekten
Benutzerdefinierte Projekttypen können Automatisierungsobjekte bereitstellen, um den Zugriff auf das Projekt mithilfe der Automatisierungsschnittstellen zu ermöglichen. Jeder Projekttyp wird erwartet, dass den Standard bereitstellt <xref:EnvDTE.Project> Automatisierungsobjekt, das aus erfolgt <xref:EnvDTE.Solution>, enthält eine Auflistung aller Projekte, die in der IDE geöffnet sind. Jedes Element im Projekt zur Verfügung gestellt werden soll eine <xref:EnvDTE.ProjectItem> mit zugegriffene Objekt `Project.ProjectItems`. Zusätzlich zu diesen standard-Automatisierungsobjekte können Projekte projektspezifische Automatisierungsobjekte zu bieten.  
  
 Sie können benutzerdefinierte auf Stammebene Automatisierungsobjekte erstellen, die Sie zugreifen können spät gebundene von der Stamm DTE-Objekts unter Verwendung `DTE.<customeObjectName>` oder `DTE.GetObject("<customObjectName>")`. Visual C++ erstellt z. B. C++ projektspezifische projektauflistung mit dem Namen "VCProjects", die Sie mithilfe von DTE zugreifen können. VCProjects oder DTE. GetObject("VCProjects"). Sie können auch eine Project.Object erstellen, die für den Projekttyp, der eine Project.CodeModel eindeutig ist, der für die am meisten abgeleiteten Objekt ein ProjectItem abgefragt werden können die ProjectItem.Object und eine Projektmodells verfügbar macht.  
  
 Es ist eine allgemeine Konvention für Projekte, um eine benutzerdefinierte, projektspezifische projektauflistung verfügbar zu machen. Beispielsweise [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] erstellt eine bestimmte C++-projektauflistung, die Sie dann mit erreichen können `DTE.VCProjects` oder `DTE.GetObject("VCProjects")`. Können Sie auch erstellen eine `Project.Object`, für den Projekttyp, eindeutig ist eine `Project.CodeModel`, die abgefragt werden kann, für die meisten ableitungen-Objekt, eine `ProjectItem`, welche macht `ProjectItem.Object`, und ein `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Ein VSPackage-Objekt für ein Projekt beitragen.  
  
1.  Fügen Sie die erforderlichen Schlüssel auf die PKGDEF-Datei Ihres VSPackage hinzu.  
  
     Hier sind z. B. die PKGDEF-Einstellungen für die Sprache C++-Projekt:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementieren Sie den Code in die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode, wie im folgenden Beispiel gezeigt.  
  
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
  
     Im Code `g_wszAutomationProjects` ist der Name der projektauflistung. Die `GetAutomationProjects` Methode erstellt ein Objekt, implementiert die `Projects` -Schnittstelle und gibt ein `IDispatch` Zeiger auf das aufrufende Objekt, wie im folgenden Codebeispiel gezeigt.  
  
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
  
     Sie sollten einen eindeutigen Namen für das Automatisierungsobjekt auswählen. Namenskonflikte sind unvorhersehbar und Konflikte verursachen einen in Konflikt stehende Objektnamen, um nach dem Zufallsprinzip ausgelöst werden, wenn mehrere Projekttypen den gleichen Namen verwenden. Sie sollten den Namen Ihres Unternehmens oder eindeutigen Aspekte des Produkts namens den Namen der Automatisierungsobjekt einbinden.  
  
     Die benutzerdefinierte `Projects` -Sammlungsobjekt ist eine Vereinfachung Einstiegspunkt für den verbleibenden Teil der Projekt-Automatisierungsmodell. Ihr Projektobjekt ist auch über die <xref:EnvDTE.Solution> projektauflistung. Nachdem Sie die entsprechenden Code und der Registrierung Einträge erstellt haben, die Consumern mit bereitstellen `Projects` Auflistung Objekten, die Ihre Implementierung muss verbleibende Standardobjekte für das Modell bereitstellen. Weitere Informationen finden Sie unter [Projekt modellieren](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>