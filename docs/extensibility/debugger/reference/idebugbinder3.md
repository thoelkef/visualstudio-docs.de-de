---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa85872337fdc1f7519d0de98cffe1436ef41c67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735666"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle bietet Zugriff auf Typen, Aliase und benutzerdefinierte Visualisierungsdienste.

## <a name="syntax"></a>Syntax

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul implementiert diese Schnittstelle, um Aliase, benutzerdefinierte Visualisierungsdienste und den Zugriff auf Objekttypinformationen zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Eine [IDebugBinder-Schnittstelle](../../../extensibility/debugger/reference/idebugbinder.md) ruft diese Schnittstelle mithilfe von [QueryInterface](/cpp/atl/queryinterface)ab.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die von der [IDebugBinder-Schnittstelle](../../../extensibility/debugger/reference/idebugbinder.md) bereitgestellt werden, implementiert diese Schnittstelle Folgendes:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Ruft ein Speicherobjekt ab, das den Speicher darstellt, an den dieses Objekt gebunden ist.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Ruft die diesem Objekt zugeordnete Ausnahme ab (falls vorhanden),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Ruft einen Alias mit seinem Namen ab,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Ruft ein Array aller Aliase für dieses Objekt ab,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Ruft die Anzahl der Argumenttypen ab, die diesem Objekt zugeordnet sind,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Ruft eine Liste der Argumenttypen ab, die diesem Objekt zugeordnet sind,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Ruft eine Schnittstelle zu einem Visualisierungsdienst ab,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Konvertiert entweder einen Objektspeicherort oder eine 64-Bit-Speicheradresse in einen Speicherkontext.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
