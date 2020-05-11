---
title: IDebugProperty3::GetCustomViewerCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16cb623f58668362e5e308e1d66dfd6ca7c0fb8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721187"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Ruft die Anzahl der benutzerdefinierten Viewer ab, die für diese Eigenschaft verfügbar sein könnten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>Parameter
`pcelt`\
[out] Die Anzahl der benutzerdefinierten Viewer, die für diese Eigenschaft verfügbar sind.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Um Typvisualisierungen zu unterstützen, leitet diese Methode den Aufruf an die [GetCustomViewerCount-Methode](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) weiter. Wenn der Ausdrucksauswertungsor auch benutzerdefinierte Viewer für den Typ dieser Eigenschaft unterstützt, fügt diese Methode dem zurückgegebenen Wert die Anzahl der benutzerdefinierten Viewer hinzu.

Ausführliche Informationen zu den Unterschieden zwischen Typvisualisierern und benutzerdefinierten Viewern finden Sie unter [Typvisualisierung und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CProperty-Objekt** implementiert wird, das die [IDebugProperty3-Schnittstelle](../../../extensibility/debugger/reference/idebugproperty3.md) verfügbar macht.

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
