---
title: "Verf&#252;gbarmachen von Projektobjekten | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Project-Objekte verfügbar machen"
  - "Erweiterbarkeit von Project-Objekte"
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Verf&#252;gbarmachen von Projektobjekten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Benutzerdefinierte Typen können Automatisierungsobjekte bereitstellen, um Zugriff auf das Projekt über Automatisierungsschnittstellen ermöglichen. Von jedem Projekttyp wird erwartet, dass den Standard bereitstellt <xref:EnvDTE.Project> Automatisierungsobjekt, das aus zugegriffen werden kann <xref:EnvDTE.Solution>, enthält eine Auflistung aller Projekte, die in der IDE geöffnet sind. Jedes Element im Projekt zur Verfügung gestellt werden soll ein <xref:EnvDTE.ProjectItem> Objekt mit den Zugriff auf <xref:Project.ProjectItems>. Zusätzlich zu diesen Automatisierungsobjekten standard können Projekte projektspezifische Automatisierungsobjekte zu bieten.  
  
 Sie können benutzerdefinierte auf Stammebene Automatisierungsobjekte erstellen, die Sie zugreifen können, spät gebundene in das Stammverzeichnis DTE mit `DTE.<customeObjectName>` oder `DTE.GetObject(“<customObjectName>”)`. Visual C\+\+ erstellt z. B. C\+\+ projektspezifische Projektsammlung namens "VCProjects", die Sie mit DTE zugreifen können. VCProjects oder DTE. GetObject\("VCProjects"\). Sie können auch eine Project.Object erstellen, die eindeutig für den Projekttyp, eine Project.CodeModel ist nach dem am meisten abgeleiteten Objekt, ein ProjectItem die ProjectItem.Object und eine Projektmodells verfügbar macht, abgefragt werden können.  
  
 Es ist eine allgemeine Konvention für Projekte, um eine benutzerdefinierte, projektspezifische Projektsammlung verfügbar zu machen. Z. B. [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] erstellt eine C\+\+\-projektspezifische\-Auflistung, die Sie dann zugreifen können, mithilfe von `DTE.VCProjects` oder `DTE.GetObject("VCProjects")`. Können Sie auch erstellen eine `Project.Object`, eindeutige für den Projekttyp, eine `Project.CodeModel`, die nach dem am meisten abgeleiteten Objekt abgefragt werden kann ein `ProjectItem`, verfügbar macht `ProjectItem.Object`, und ein `ProjectItem.FileCodeModel`.  
  
### Ein VSPackage\-Objekt für ein Projekt beitragen  
  
1.  Fügen Sie die entsprechenden Schlüssel der PKGDEF\-Datei der Ihr VSPackage.  
  
     Hier sind z. B. die PKGDEF\-Einstellungen für die Sprache C\+\+\-Projekt:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation] "VCProjects"="" [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents] "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementieren Sie den Code in die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode, wie im folgenden Beispiel.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject( /* [in]  */ LPCOLESTR       pszPropName, /* [out] */ IDispatch **    ppIDispatch) { ExpectedPtrRet(pszPropName); ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (m_fZombie) return E_UNEXPECTED; if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0) { return GetAutomationProjects(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } return E_INVALIDARG; }   
    ```  
  
     Im Code `g_wszAutomationProjects` ist der Name der Projektsammlung. Die `GetAutomationProjects` \-Methode erstellt ein Objekt, das implementiert die `Projects` \-Schnittstelle und gibt ein `IDispatch` Zeiger auf das aufrufende Objekt, wie im folgenden Codebeispiel gezeigt.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch) { ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (!m_srpAutomationProjects) { HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects); IfFailRet(hr); ExpectedExprRet(m_srpAutomationProjects != NULL); } return m_srpAutomationProjects.CopyTo(ppIDispatch); }  
    ```  
  
     Sie sollten einen eindeutigen Namen für das Automatisierungsobjekt auswählen. Namenskonflikte unvorhersehbar und Konflikte verursachen einen in Konflikt stehenden Objektnamen, um nach dem Zufallsprinzip ausgelöst werden, wenn mehrere Projekttypen den gleichen Namen verwenden. Sie sollten den Namen Ihres Unternehmens oder einem eindeutigen Aspekt des Produkts namens im Namen des Automatisierungsobjekts einschließen.  
  
     Die benutzerdefinierte `Projects` Auflistungsobjekt ist eine benutzerfreundliche Einstiegspunkt für den verbleibenden Teil der Projektautomatisierungsmodell. Das Projektobjekt ist auch die <xref:EnvDTE.Solution> Projektsammlung. Nachdem Sie die entsprechenden Code und die Registrierung Einträge erstellt haben, die Consumer bereitstellen `Projects` Auflistung Objekte, die Ihre Implementierung bereitstellen muss, verbleibende Standardobjekte für das Modell. Weitere Informationen finden Sie unter [Projekt\-Modellierung](../../extensibility/internals/project-modeling.md).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>