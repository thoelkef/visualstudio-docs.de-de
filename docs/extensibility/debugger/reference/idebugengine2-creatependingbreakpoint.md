---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72719a2dc6d424487c0fdd6b5850ff7f1d1e29aa
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703382"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Erstellt einen ausstehenden Haltepunkt in der Debug-Engine (DE).

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

#### <a name="parameters"></a>Parameter
`pBPRequest`

 [in] Ein [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Objekt, das zum Erstellen den ausstehenden Haltepunkt beschreibt.

`ppPendingBP`

 [out] Gibt eine [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Objekt, das den ausstehenden Haltepunkt darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. In der Regel gibt `E_FAIL` Wenn die `pBPRequest` Parameter entspricht einer beliebigen Sprache, die von der DE zurück, wenn unterstützt nicht die `pBPRequest` -Parameter ist ungültig oder unvollständig.

## <a name="remarks"></a>Hinweise
Ein ausstehender Haltepunkt ist im Wesentlichen eine Sammlung aller Informationen erforderlich, um einen Haltepunkt in Code zu binden. Der ausstehenden Haltepunkt von dieser Methode zurückgegebene nicht an den Code bis gebunden ist die [binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) Methode wird aufgerufen.

Für jeden ausstehenden Haltepunkt Ruft die Benutzersätze sitzungsbasierter Debug-Manager (SDM) diese Methode in jeder angefügten DE. Es ist Aufgabe der DE, um sicherzustellen, dass der Haltepunkt für Programme, die unter diesem DE gültig ist.

Wenn der Benutzer einen Haltepunkt in einer Zeile des Codes festlegt, kann die DE den Haltepunkt in die nächste Zeile im Dokument binden, der dieser Code entspricht. Dadurch kann der Benutzer zum Festlegen eines Haltepunkts in der ersten Zeile einer mehrzeiligen Anweisung, aber binden es in der letzten Zeile (wobei der gesamte Code in den Debuginformationen zugeordnet ist).

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CProgram` Objekt. Die DE Implementierung der `IDebugEngine2::CreatePendingBreakpoint` könnte dann alle Aufrufe an diese Implementierung der Methode in jedem Programm weiterleiten.

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

## <a name="see-also"></a>Siehe auch
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
