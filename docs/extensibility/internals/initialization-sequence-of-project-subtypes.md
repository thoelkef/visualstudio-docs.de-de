---
title: "Initialisierungssequenz Projekt Untertypen | Microsoft Docs"
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
  - "Projekt-Untertypen, Initialisierungssequenz"
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Initialisierungssequenz Projekt Untertypen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Umgebung erstellt ein Projekt, indem sie die Implementierung des <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>factory Projekt aufruft.  Beim Erstellen eines Projekts untertyps beginnt, wenn die Umgebung bestimmt, ob die Liste des Projekttyps GUID für die Erweiterung einer Projektdatei nicht leer ist.  Die Projektdatei Namespaceerweiterung und der Projekt\-GUID geben an, ob das Projekt ein, oder  [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)][!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projekttyp ist.  Zum Beispiel identifizieren die .vbproj\-Erweiterung C81 C\-45F6\-A57F\-5ABD9991F28F} und {F184B08F\- ein [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekt.  
  
## Die Initialisierung der Umgebung aus Projekt\-Untertypen  
 Die folgenden Schritte sind, die die Initialisierung für ein Projektsystem Sequenz von mehreren Projekt untertypen aggregierte.  
  
1.  Die Umgebung wird das Basis\- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>des Projekts und während das Projekt die Projektdatei analysiert es ermittelt, dass die gesamte Liste des Projekttyps GUID nicht `null`ist.  Das Projekt wird ein Projekt, das direkt erstellen.  
  
2.  Das Projekt wird `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> Dienst auf, um einen untertyp Projekt mithilfe der Implementierung der Umgebung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>\-Methode zu erstellen.  Innerhalb dieser Methode werden die Umgebung rekursiven Funktionsaufrufe Implementierungen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` und <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>\-Methode, um zunächst die Liste des Projekttyps GUID durchläuft, beginnend mit der äußersten Projekt untertyp.  
  
     Die folgenden Details der Initialisierung Bereitstellungsschritte.  
  
    1.  Die Implementierung der Umgebung der Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> methodenaufruf\- `HrCreateInnerProj```mit der folgenden Funktionsdeklaration aufgeführt wird:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         Wenn diese Funktion zum ersten Mal d. h. für den äußeren Projekt untertyp aufgerufen wird, werden die Parameter `pOuter` und `pOwner` übergeben, während `null` und die Funktion den äußersten Projekt untertyp `IUnknown` zu `pOuter`festlegt.  
  
    2.  Als Nächstes die Umgebung aufrufs\- `HrCreateInnerProj`\-Funktion mit dem zweiten Projekttyp\-GUID in der Liste.  Dieses GUID entspricht dem zweiten inneren Projekt untertyp hin, der dem Basis\- Projekt in der Sequenz Aggregations.  
  
    3.  `pOuter` verweist nun auf `IUnknown` des äußeren untertyps Projekt, und `HrCreateInnerProj` Aufrufe, die die Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> von einem Aufruf der Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>erfolgreich war.  In <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>\-Methode übergeben Sie steuernde `IUnknown` des äußersten Projekt untertyps, `pOuter`.  Das Besitze Projekt \(innerer Projekt untertyp hier Projektobjekt ganzes sein muss\) erstellen.  In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>\-Methodenimplementierung übergeben Sie einen Zeiger auf `IUnknown` des inneren Projekts, die aggregiert wird.  Diese beiden Methoden erstellen das Aggregations Objekt und die Implementierung COM\-Aggregations regeln, zu folgen, um sicherzustellen, dass ein Projekt untertyp einen Verweiszähler hochhalten nicht mit sich selbst beendet wird.  
  
    4.  `HrCreateInnerProj` ruft die Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>an.  In dieser Methode übernimmt das Projekt untertyp ihre Initialisierung.  Sie können Projektmappen von Ereignissen im <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>z. B. registrieren.  
  
    5.  `HrCreateInnerProj` wird rekursiv aufgerufen, bis die letzte GUID \(das niedrige Projekt\) in der Liste erreicht ist.  Für jeden dieser Aufrufe werden die Schritte, c, d und wiederholt.  `pOuter` zeigt auf den äußersten Projekt untertyp Aggregationsebene für jede `IUnknown` .  
  
 Im folgenden Beispiel sind der programmgesteuerten Vorgang in einer ungefähren Darstellung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>\-Methode, da sie von der Umgebung implementiert wird.  Der Code ist nur ein Beispiel. Er ist nicht vorgesehen kompiliert, und alle Fehlerüberprüfung wurde aus Gründen der Übersichtlichkeit entfernt.  
  
## Beispiel  
  
### Code  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Projekt\-Untertypen](../../extensibility/internals/project-subtypes.md)