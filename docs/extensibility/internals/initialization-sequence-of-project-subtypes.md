---
title: Initialisierungs Sequenz von Projekt Untertypen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 678f704c73a39cdf2130d36fcfb1a74925dd89d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726878"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Initialisierungssequenz von Projektuntertypen
Die Umgebung erstellt ein Projekt durch Aufrufen der Basisprojekt-Factory-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Die Erstellung eines Projekt unter Typs beginnt, wenn die Umgebung feststellt, dass die Projekttyp-GUID-Liste für die Erweiterung einer Projektdatei nicht leer ist. Die Projektdatei Erweiterung und die Projekt-GUID geben an, ob das Projekt ein [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projekttyp ist. Beispielsweise identifizieren die VBPROJ-Erweiterung und {F184B08F-C81C-45F6-A57F-5ABD9991F28F} ein [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekt.

## <a name="environments-initialization-of-project-subtypes"></a>Initialisierung von Projekt Untertypen in der Umgebung
 Im folgenden Verfahren wird die Initialisierungs Sequenz für ein Projekt System erläutert, das von mehreren Projekt Untertypen aggregiert wird.

1. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> des Basis Projekts auf, und während das Projekt die Projektdatei analysiert, wird ermittelt, dass die GUIDs-Liste für den Aggregat Projekttyp nicht `null` ist. Das Projekt wird nicht mehr direkt mit dem Projekt erstellt.

2. Das Projekt ruft `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> Dienst auf, um einen Projekt Untertyp mithilfe der Implementierung der-<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>-Methode der Umgebung zu erstellen. Innerhalb dieser Methode führt die Umgebung rekursive Funktionsaufrufe ihrer Implementierungen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> Methoden aus, während Sie die Liste der Projekttyp-GUIDs durchläuft, beginnend mit dem äußersten Projekt Untertyp.

     Im folgenden werden die Initialisierungs Schritte ausführlich erläutert.

    1. Die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>-Methode der Umgebung Ruft die `HrCreateInnerProj`-Methode mit der folgenden Funktionsdeklaration auf:

         \<CodeContentPlaceHolder > 0 </CodeContentPlaceHolder>

         Wenn diese Funktion zum ersten Mal aufgerufen wird, d. h. für den äußersten Projekt Untertyp, werden die Parameter `pOuter` und `pOwner` als `null` und die Funktion legt den äußersten Projekt Untertyp `IUnknown` auf `pOuter` fest.

    2. Als nächstes Ruft die Umgebung `HrCreateInnerProj` Funktion mit der zweiten Projekttyp-GUID in der Liste auf. Diese GUID entspricht dem zweiten inneren Projekt Untertyp, der in Richtung des Basis Projekts in der Aggregations Sequenz geht.

    3. Der `pOuter` verweist jetzt auf die `IUnknown` des äußersten Projekt unter Typs, und `HrCreateInnerProj` Ruft die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> auf, gefolgt von einem Aufruf der Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. In <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>-Methode übergeben Sie den Steuerungs `IUnknown` des äußersten Projekt unter Typs `pOuter`. Das eigene Projekt (Inner Project SubType) muss das Aggregat Projekt Objekt hier erstellen. In der Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> Methode übergeben Sie einen Zeiger auf den `IUnknown` des inneren Projekts, das aggregiert wird. Diese beiden Methoden erstellen das Aggregations Objekt, und ihre Implementierungen müssen com-Aggregations Regeln befolgen, um sicherzustellen, dass ein Projekt Untertyp keinen Verweis Zähler auf sich selbst enthält.

    4. `HrCreateInnerProj` Ihre Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> aufruft. In dieser Methode führt der Projekt Untertyp seine Initialisierung aus. Sie können z. b. Lösungs Ereignisse in <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> registrieren.

    5. `HrCreateInnerProj` wird rekursiv aufgerufen, bis die letzte GUID (das Basisprojekt) in der Liste erreicht ist. Für jeden dieser Aufrufe werden die Schritte c bis d wiederholt. `pOuter` verweist auf den äußersten Projekt Untertyp `IUnknown` für jede Aggregations Ebene.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der programmgesteuerte Prozess in einer ungefähren Darstellung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>-Methode erläutert, wie Sie von der Umgebung implementiert wird. Der Code ist nur ein Beispiel. Sie ist nicht für die Kompilierung vorgesehen, und die Fehlerüberprüfung wurde aus Gründen der Übersichtlichkeit entfernt.

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