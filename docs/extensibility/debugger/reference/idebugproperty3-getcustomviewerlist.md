---
title: IDebugProperty3::GetCustomViewerList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 212f8d251232d35ee7d9cc46074a21239eea29f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721158"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Ruft eine Liste der benutzerdefinierten Viewer ab, die dieser Eigenschaft zugeordnet sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCustomViewerList(
    ULONG                celtSkip,
    ULONG                celtRequested,
    DEBUG_CUSTOM_VIEWER* rgViewers,
    ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
    uint                  celtSkip,
    uint                  celtRequested,
    DEBUG_CUSTOM_VIEWER[] rgViewers,
    out uint              pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celtSkip`\
[in] Die Anzahl der Zuüberspringenden Zuschauer.

`celtRequested`\
[in] Die Anzahl der abzurufenden Viewer (gibt `rgViewers` auch die Größe des Arrays an).

`rgViewers`\
[in, out] Array von [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen auszufüllen.

`pceltFetched`\
[out] Die tatsächliche Anzahl der zurückgegebenen Zuschauer.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Um Typvisualisierungen zu unterstützen, leitet diese Methode den Aufruf an die [GetCustomViewerList-Methode](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) weiter. Wenn der Ausdrucksauswertungsor auch benutzerdefinierte Viewer für den Typ dieser Eigenschaft unterstützt, kann diese Methode die entsprechenden benutzerdefinierten Viewer an die Liste anhängen.

Weitere Informationen zu den Unterschieden zwischen Typvisualisierern und benutzerdefinierten Viewern finden Sie unter [Typvisualisierung und benutzerdefinierter Viewer.](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CProperty-Objekt** implementiert wird, das die [IDebugProperty3-Schnittstelle](../../../extensibility/debugger/reference/idebugproperty3.md) verfügbar macht.

```cpp
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)
{
    if (NULL == prgViewers)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
