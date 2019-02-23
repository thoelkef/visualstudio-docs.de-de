---
title: IDebugExpressionContext2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 559115358910fe3445ab12000d1e113167c7da82
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717987"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Diese Schnittstelle stellt einen Kontext für ausdrucksauswertung dar.

## <a name="syntax"></a>Syntax

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um einen Kontext darstellen, in dem ein Ausdruck ausgewertet werden kann.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufruf von [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) gibt zurück, die diese Schnittstelle. Diese Schnittstelle ist zugegriffen werden kann, nur, wenn das derzeit debuggte Programm angehalten wurde und ein Stapelrahmen verfügbar ist.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugExpressionContext2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Ruft den Namen des dem Auswertungskontext ab.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analysiert einen textbasierter Ausdruck für die Evaluierung.|

## <a name="remarks"></a>Hinweise
 Ein Evaluierungskontext kann als Bereich für die Durchführung der Auswertung des Ausdrucks betrachtet werden.

 Wenn ein Programm angehalten wurde, erhält der sitzungsbasierter Debug-Manager (SDM) einen Stapelrahmen aus dem DE mit einem Aufruf von [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Klicken Sie dann aufruft, das SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zum Abrufen der `IDebugExpressionContext2` Schnittstelle. Darauf folgt ein Aufruf von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zum Erstellen einer [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle, die den analysierten Ausdruck zur Auswertung bereiter darstellt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)