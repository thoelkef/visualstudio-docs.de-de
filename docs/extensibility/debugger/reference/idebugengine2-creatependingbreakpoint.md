---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731121"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Erstellt einen ausstehenden Haltepunkt im Debugmodul (DE).

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Parameter
`pBPRequest`\
[in] Ein [IDebugBreakpointRequest2-Objekt,](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) das den zu erstellenden ausstehenden Haltepunkt beschreibt.

`ppPendingBP`\
[out] Gibt ein [IDebugPendingBreakpoint2-Objekt](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) zurück, das den ausstehenden Haltepunkt darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Wird `E_FAIL` in `pBPRequest` der Regel zurückgegeben, wenn der Parameter `pBPRequest` nicht mit einer Sprache übereinstimmt, die von der DE unterstützt wird, wenn der Parameter ungültig oder unvollständig ist.

## <a name="remarks"></a>Bemerkungen
Ein ausstehender Haltepunkt ist im Wesentlichen eine Sammlung aller Informationen, die zum Binden eines Haltepunkts an Code erforderlich sind. Der ausstehende Haltepunkt, der von dieser Methode zurückgegeben wird, ist erst an den Code gebunden, wenn die [Bind-Methode](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) aufgerufen wird.

Für jeden ausstehenden Haltepunkt, den der Benutzer festlegt, ruft der Sitzungsdebug-Manager (SDM) diese Methode in jeder angefügten DE auf. Es ist an der DE zu überprüfen, ob der Haltepunkt für Programme gültig ist, die in dieser DE ausgeführt werden.

Wenn der Benutzer einen Haltepunkt für eine Codezeile festlegt, kann der DE den Haltepunkt an die nächste Zeile im Dokument binden, die diesem Code entspricht. Dies ermöglicht es dem Benutzer, einen Haltepunkt in der ersten Zeile einer mehrzeiligen Anweisung festzulegen, ihn jedoch in der letzten Zeile zu binden (wobei der gesamte Code in den Debuginformationen zugeordnet ist).

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CProgram` Methode für ein einfaches Objekt implementiert wird. Die De-Implementierung der `IDebugEngine2::CreatePendingBreakpoint` könnte dann alle Aufrufe an diese Implementierung der Methode in jedem Programm weiterleiten.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
