---
title: Verfügbarmachen von Projektobjekten | Microsoft-Dokumentation
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044669"
---
# <a name="exposing-project-objects"></a>Verfügbarmachen von Projektobjekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Benutzerdefinierte Projekttypen können Automatisierungsobjekte bereitstellen, um den Zugriff auf das Projekt mithilfe der Automatisierungsschnittstellen zu ermöglichen. Jeder Projekttyp wird erwartet, dass den Standard bereitstellt <xref:EnvDTE.Project> Automatisierungsobjekt, das aus zugegriffen werden kann <xref:EnvDTE.Solution>, enthält eine Auflistung aller Projekte, die in der IDE geöffnet sind. Jedes Element im Projekt von verfügbar gemacht werden soll eine <xref:EnvDTE.ProjectItem> mit zugegriffene Objekt <xref:EnvDTE.Project.ProjectItems>. Zusätzlich zu diesen Objekten Automation standard-können Projekte auch projektspezifische Automatisierungsobjekte zu bieten.  
  
 Sie können benutzerdefinierte auf Stammebene Automatisierungsobjekte erstellen, die Sie zugreifen können, spät gebundene von der Stamm DTE-Objekt unter Verwendung `DTE.<customeObjectName>` oder `DTE.GetObject(“<customObjectName>”)`. Visual C++ erstellt z. B. C++ projektspezifische projektauflistung namens "VCProjects", die Sie mithilfe des DTE zugreifen können. VCProjects oder DTE. GetObject("VCProjects"). Sie können auch eine Project.Object, erstellen, der für den Projekttyp, eine Project.CodeModel, eindeutig ist, die die für die am stärksten abgeleiteten Objekt ProjectItem, die ProjectItem.Object und eine Projektmodells verfügbar macht, abgefragt werden können.  
  
 Es ist eine allgemeine Konvention für Projekte, um eine benutzerdefinierte, projektspezifische Projektsammlung verfügbar zu machen. Z. B. [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] erstellt eine bestimmte C++-projektauflistung, die Sie zugreifen können mithilfe von `DTE.VCProjects` oder `DTE.GetObject("VCProjects")`. Sie können auch erstellen eine `Project.Object`, für den Projekttyp, eindeutig ist eine `Project.CodeModel`, die abgefragt werden kann, für das Objekt am stärksten abgeleiteten eine `ProjectItem`, verfügbar macht `ProjectItem.Object`, und eine `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Um ein VSPackage-Objekt für ein Projekt beitragen.  
  
1. Fügen Sie die entsprechenden Schlüssel, der PKGDEF-Datei Ihres VSPackage hinzu.  
  
     Hier sind z. B. die PKGDEF-Einstellungen für die Sprache C++-Projekt:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2. Implementieren Sie den Code in die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> -Methode, wie im folgenden Beispiel gezeigt.  
  
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
  
     Im Code `g_wszAutomationProjects` ist der Name der Projektsammlung. Die `GetAutomationProjects` Methode erstellt ein Objekt, implementiert die `Projects` -Schnittstelle und gibt eine `IDispatch` Zeiger auf das aufrufende Objekt, wie im folgenden Codebeispiel gezeigt.  
  
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
  
     Sie sollten einen eindeutigen Namen für das Automatisierungsobjekt auswählen. Konflikte bei Befehlsnamen sind unvorhersehbar und Konflikte verursachen, ein in Konflikt stehende Objektname nach dem Zufallsprinzip ausgelöst wird, wenn es sich bei verschiedenen Projekttypen den gleichen Namen verwenden. Sie sollten den Namen Ihres Unternehmens oder der Product Name den Namen das Automatisierungsobjekt Aspekts eindeutigen einschließen.  
  
     Die benutzerdefinierte `Projects` -Objekt ist ein der Einfachheit halber-Einstiegspunkt für den verbleibenden Teil Ihrer Projektautomatisierungsmodell. Ihr Projektobjekt ist auch über die <xref:EnvDTE.Solution> Projektsammlung. Nachdem Sie die entsprechenden Einträge von Code und die Registrierung erstellt haben, die Kunden mit bereitstellen `Projects` Auflistung Objekte, die Ihre Implementierung muss verbleibende Standardobjekte für das Modell angeben. Weitere Informationen finden Sie unter [Projekt Modellierung](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
