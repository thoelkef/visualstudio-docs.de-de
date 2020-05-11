---
title: Initialisierungssequenz von Projektuntertypen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707632"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Initialisierungssequenz von Projektuntertypen
Die Umgebung erstellt ein Projekt, indem sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>die Implementierung der Basisprojektfactory von aufruft. Die Erstellung eines Projektuntertyps beginnt, wenn die Umgebung feststellt, dass die GUID-Liste des Projekttyps für die Erweiterung einer Projektdatei nicht leer ist. Die Projektdateierweiterung und die Projekt-GUID [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] geben an, ob es sich bei dem Projekt um einen oder einen Projekttyp handelt. Die Erweiterung .vbproj und die Erweiterung "F184B08F-C81C-45F6-A57F-5ABD9991F28F" kennzeichnen z. B. ein [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekt.

## <a name="environments-initialization-of-project-subtypes"></a>Die Initialisierung von Projektuntertypen durch die Umgebung
 Im folgenden Verfahren wird die Initialisierungssequenz für ein Projektsystem beschrieben, das von mehreren Projektuntertypen aggregiert wird.

1. Die Umgebung ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>des Basisprojekts auf, und während das Projekt seine Projektdatei analysiert, `null`stellt sie fest, dass die Liste der aggregierten Projekttyp-GUIDs nicht ist. Das Projekt stellt die direkte Erstellung des Projekts ein.

2. Das Projekt `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> fordert den Dienst auf, einen Projektuntertyp <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> zu erstellen, der die Implementierung der Methode in der Umgebung verwendet. Innerhalb dieser Methode führt die Umgebung rekursive Funktionsaufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> für Ihre Implementierungen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>aus, während sie die Liste der Projekttyp-GUIDs fortführt, beginnend mit dem untersten Projektsubtyp.

     Im Folgenden werden die Initialisierungsschritte erläutert.

    1. Die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> Methode in `HrCreateInnerProj` der Umgebung ruft die Methode mit der folgenden Funktionsdeklaration auf:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Wenn diese Funktion zum ersten Mal aufgerufen wird, d. h. `pOuter` für `pOwner` den äußersten Projektuntertyp, werden die Parameter als übergeben `null` und die Funktion legt den äußersten Projektuntertyp `IUnknown` auf `pOuter`fest.

    2. Als Nächstes `HrCreateInnerProj` ruft die Umgebung die Funktion mit der zweiten Projekttyp-GUID in der Liste auf. Diese GUID entspricht dem zweiten inneren Projektuntertyp, der in der Aggregationssequenz in Richtung des Basisprojekts eintritt.

    3. Der `pOuter` zeigt nun `IUnknown` auf den Untertyp des `HrCreateInnerProj` äußersten Projekts <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> und ruft Ihre Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>auf, gefolgt von einem Aufruf an ihre Implementierung von . In <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> der Methode übergeben `IUnknown` Sie die Steuerung des `pOuter`äußersten Projektsubtyps . Das eigene Projekt (innerer Projektuntertyp) muss hier sein aggregiertes Projektobjekt erstellen. In <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> der Methodenimplementierung übergeben Sie einen `IUnknown` Zeiger auf das innere Projekt, das aggregiert wird. Diese beiden Methoden erstellen das Aggregationsobjekt, und Ihre Implementierungen müssen COM-Aggregationsregeln befolgen, um sicherzustellen, dass ein Projektuntertyp am Ende keine Verweisanzahl für sich selbst enthält.

    4. `HrCreateInnerProj`ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>Implementierung von auf Bei dieser Methode führt der Projektuntertyp seine Initialisierungsarbeit durch. Sie können z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>Lösungsereignisse in registrieren.

    5. `HrCreateInnerProj`wird rekursiv aufgerufen, bis die letzte GUID (das Basisprojekt) in der Liste erreicht ist. Für jeden dieser Aufrufe werden die Schritte c bis d wiederholt. `pOuter`zeigt auf den äußersten `IUnknown` Projektsubtyp für jede Aggregationsebene.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der programmgesteuerte <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> Prozess in einer ungefähren Darstellung der Methode, wie sie von der Umgebung implementiert wird, erläutert. Der Code ist nur ein Beispiel; Es ist nicht für die Kompilierung vorgesehen, und alle Fehlerüberprüfungen wurden aus Gründen der Übersichtlichkeit entfernt.

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

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)
