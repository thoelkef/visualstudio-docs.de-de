---
title: IDebugExpressionContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729641"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Diese Schnittstelle stellt einen Kontext für die Ausdrucksauswertung dar.

## <a name="syntax"></a>Syntax

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um einen Kontext darzustellen, in dem ein Ausdruck ausgewertet werden kann.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) gibt diese Schnittstelle zurück. Auf diese Schnittstelle kann nur zugegriffen werden, wenn das zu debuggende Programm angehalten wurde und ein Stapelrahmen verfügbar ist.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugExpressionContext2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Ruft den Namen des Auswertungskontexts ab.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analysiert einen textbasierten Ausdruck zur Auswertung.|

## <a name="remarks"></a>Bemerkungen
 Ein Evaluierungskontext kann als Einfühlungsspielraum für die Ausdrucksauswertung betrachtet werden.

 Wenn ein Programm angehalten wurde, ruft der Sitzungsdebug-Manager (SDM) einen Stackframe von der DE mit einem Aufruf von [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)ab. Das SDM ruft dann [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um die `IDebugExpressionContext2` Schnittstelle abzubekommen. Es folgt ein Aufruf von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zum Erstellen einer [IDebugExpression2-Schnittstelle,](../../../extensibility/debugger/reference/idebugexpression2.md) die den analysierten Ausdruck darstellt, der ausgewertet werden kann.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
