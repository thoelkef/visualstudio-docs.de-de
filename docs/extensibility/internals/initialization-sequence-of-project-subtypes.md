---
title: Initialisierungssequenz Projekt Untertypen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe7e7a574d04ec9a49252e32e0fbb8b5685778aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131607"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Initialisierungssequenz Projekt Untertypen
Die Umgebung erstellt ein Projekt durch Aufrufen der Basis projektfactoryimplementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Die zur Erstellung eines Untertyps Projekt beginnt, wenn die Umgebung bestimmt, dass das Projekt GUID Typliste für ein Projekt die Dateierweiterung nicht leer ist. Die Projekt-Dateierweiterung und der Projekt-GUID angeben, ob das Projekt ist eine [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projekttyp. Z. B. die vbproj-Erweiterung und {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identifiziert eine [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekt.

## <a name="environments-initialization-of-project-subtypes"></a>Initialisierung von der Umgebung Projekt Untertypen
 Das folgende Verfahren erläutert die Initialisierungssequenz für ein Projektsystem wird durch mehrere Projekt Untertypen aggregiert.

1.  Ruft die Umgebung die Basisprojekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, während das Projekt auf die Projektdatei analysiert werden, dass die aggregate Projekttyp GUIDs Liste nicht `null`. Das Projekt reagiert nicht mehr, die ihr Projekt direkt erstellen.

2.  Ruft die Projekt `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> zu Projektuntertyp mit der Umgebung Implementierung des zu erstellenden Dienst den <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> Methode. Innerhalb dieser Methode stellt die Umgebung rekursive Funktionsaufrufe Ihre Implementierungen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> Methoden, während es die Liste des Projekts durchläuft geben GUIDs, beginnend mit dem äußersten Projektuntertyp.

     Im folgenden sind die Schritte zum Initialisieren.

    1.  Implementierung der Umgebung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> Methodenaufrufe der `HrCreateInnerProj` Methode mit der folgenden Deklaration:

         <CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Wenn dieser Funktion wird zum ersten Mal, also für den Projektuntertyp äußersten Parameter `pOuter` und `pOwner` als übergeben `null` und setzt die Funktion den Untertyp des äußersten Projekts `IUnknown` auf `pOuter`.

    2.  Als Nächstes ruft die Umgebung `HrCreateInnerProj` -Funktion mit dem zweiten Projekttyp GUID in der Liste. Diese GUID entspricht der zweite innere Projektuntertyp ausführen in Einzelschritten gegen die Basis-Projekt in der Sequenz Aggregation.

    3.  Die `pOuter` jetzt verweist auf die `IUnknown` des Untertyps äußersten Projekt und `HrCreateInnerProj` ruft Ihre Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> gefolgt von einem Aufruf Ihrer Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. In <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> Methode steuernde übergebenen `IUnknown` des Untertyps äußersten Projekt `pOuter`. Das zugehörige Projekt (innere Projektuntertyp) muss hier die aggregierten Projektobjekt zu erstellen. In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> methodenimplementierung, die Sie übergeben einen Zeiger auf die `IUnknown` des inneren Projekts, das aggregiert wird. Diese beiden Methoden erstellen des Aggregationsentwurfs-Objekts, und Ihre Implementierungen von COM Aggregationsregeln, um sicherzustellen, dass ein Projektuntertyp nicht annehmen enthalten einen Verweiszähler auf sich selbst entsprechen müssen.

    4.  `HrCreateInnerProj` Ruft die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. Bei dieser Methode funktioniert der Untertyp des Projekts die Initialisierung. Sie können z. B. registrieren Lösung Ereignisse in <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5.  `HrCreateInnerProj` ist rekursiv aufgerufen werden, bis die letzte GUID (die Basis-Projekt) in der Liste erreicht ist. Für jede von diesen aufrufen werden die Schritte, bis d, C wiederholt. `pOuter` verweist auf den äußersten Projektuntertyp `IUnknown` für jede Ebene der Aggregation.

## <a name="example"></a>Beispiel

Das folgende Beispiel erläutert das programmgesteuerte in eine ungefähre Darstellung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> -Methode wird von der Umgebung implementiert. Der Code ist nur ein Beispiel. Es ist nicht vorgesehen, kompiliert werden, und alle fehlerüberprüfung aus Gründen der Übersichtlichkeit entfernt wurde.

```cpp
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

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)