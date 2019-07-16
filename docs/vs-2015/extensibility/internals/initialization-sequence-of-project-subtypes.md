---
title: Initialisierungssequenz von Projektuntertypen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5594d54c188c2f561dd66229e808e48068ba41a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192656"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Initialisierungssequenz von Projektuntertypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Umgebung erstellt ein Projekt durch Aufrufen der Basis projektfactoryimplementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Die Erstellung von einem Projektuntertyp wird gestartet, wenn die Umgebung bestimmt, dass die Liste mit Projekten Typ GUID für ein Projekt die Dateierweiterung nicht leer ist. Die Dateinamenerweiterung für Projektdateien und die Projekt-GUID angeben, ob das Projekt ist eine [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Projekttyp. Z. B. die Erweiterung .vbproj {F184B08F-C81C-45F6-A57F-5ABD9991F28F} zu identifizieren, und eine [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Projekt.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Initialisierung der Umgebung von Projektuntertypen  
 Das folgende Verfahren erläutert die Initialisierungssequenz für ein Projektsystem, die von mehreren Projektuntertypen aggregiert.  
  
1. Die Umgebung ruft des Basisprojekts <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, während das Projekt die Projektdatei analysiert werden, dass der aggregierte Projekttyp GUIDs Liste nicht `null`. Das Projekt wird beendet, ihr Projekt direkt zu erstellen.  
  
2. Die projektaufrufe `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> zu einem Projektuntertyp, die mit der Umgebung-Implementierung des zu erstellenden Dienst den <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> Methode. Innerhalb dieser Methode wird die Umgebung rekursive Funktionsaufrufe an Ihre Implementierungen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` und <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> GUIDs, beginnend mit der äußeren Projektuntertyp Geben Sie Methoden, während sie die Liste der Projekttyp durchlaufen wird.  
  
    Im folgenden Abschnitt wird die Initialisierungsschritte.  
  
   1. Implementierung der Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> Methodenaufrufe "HrCreateInnerProj'' '-Methode durch die folgende Funktionsdeklaration:  
  
       ```  
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
           BOOL *pfCancelled  
       )  
       ```  
  
        Wenn diese Funktion wird aufgerufen zum ersten Mal, d. h. für den äußeren Projektuntertyp, die Parameter `pOuter` und `pOwner` als übergeben `null` und die Funktion legt fest, den äußeren Projektuntertyp `IUnknown` zu `pOuter`.  
  
   2. Als Nächstes die Umgebung ruft `HrCreateInnerProj` -Funktion mit dem zweiten Projekttyp-GUID in der Liste. Diese GUID entspricht der zweiten inneren Projektuntertyp einzelschrittausführung in Richtung Basisprojekts in der Aggregation-Sequenz.  
  
   3. Die `pOuter` verweist jetzt auf die `IUnknown` des äußersten projektuntertyps, und `HrCreateInnerProj` ruft Ihre Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> gefolgt von einem Aufruf für Ihre Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. In <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> Methode, die Sie das steuernde übergeben `IUnknown` des äußersten projektuntertyps, `pOuter`. Das Projekt im Besitz (inneren Projektuntertyp) muss hier die Projekt-Objekt zu erstellen. In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> übergeben Sie einen Zeiger auf die Implementierung der `IUnknown` des inneren Projekts, das aggregiert wird. Diese beiden Methoden erstellen, das Aggregation-Objekt, und Ihre Implementierungen müssen Sie COM-Aggregationsregeln, um sicherzustellen, dass es sich bei einem Projektuntertyp nicht am Ende ist, einen Verweiszähler auf sich selbst enthält.  
  
   4. `HrCreateInnerProj` Ruft die Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. Bei dieser Methode führt der Projektuntertyp Initialisierung. Sie können z. B. Projektmappenereignissen in registrieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
   5. `HrCreateInnerProj` wird rekursiv aufgerufen werden, bis die letzte GUID (die Basis-Projekt) in der Liste erreicht ist. Für jeden dieser Aufrufe werden die Schritte, bis d, C wiederholt. `pOuter` verweist auf den äußeren Projektuntertyp `IUnknown` für jede Ebene der Aggregation.  
  
   Im folgende Beispiel erläutert die programmgesteuerte in eine ungefähre Darstellung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> -Methode wird von der Umgebung implementiert. Der Code ist nur ein Beispiel. es nicht kompiliert werden soll, und alle fehlerüberprüfung wurde aus Gründen der Übersichtlichkeit entfernt.  
  
## <a name="example"></a>Beispiel  
  
### <a name="code"></a>Code  
  
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
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Projektuntertypen](../../extensibility/internals/project-subtypes.md)
