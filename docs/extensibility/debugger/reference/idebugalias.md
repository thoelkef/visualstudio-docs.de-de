---
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2ceb87277460f65e52c35f02e7fbbd01da1101a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736511"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt einen numerischen Alias für eine Variable dar. Ein Alias ist einfach ein anderer Name für eine Variable.

## <a name="syntax"></a>Syntax

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Ausdrucksevaluator (EE) implementiert diese Schnittstelle, um numerische Aliase für Variablen zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) erstellt einen Alias für ein bestimmtes Objekt. Um nach Aliasnamen zu suchen, verwenden Sie [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) oder [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgenden Methoden sind `IDebugAlias` in der Schnittstelle definiert.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Getobject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Ruft das Objekt ab, auf das sich dieser Alias bezieht.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Ruft den Aliasnamen ab.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Ruft eine `ICorDebugValue` Schnittstelle ab, die Zugriff auf Informationen zu verwaltetem Code zu diesem Objekt bietet (nur verwalteter Code).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Markiert diesen Alias als nicht mehr verwendet.|

## <a name="remarks"></a>Bemerkungen
 Ein Alias ist eine Dezimalzahl in Zeichenfolgenform, gefolgt von dem Zeichen , z. B. 1001.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
