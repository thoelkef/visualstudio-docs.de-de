---
title: IDebugCodeContext2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59573736ca3cd0768d3383e5621d96dffdea9746
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338901"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Diese Schnittstelle stellt die Anfangsposition der Anweisung für einen Code an. Für die meisten Laufzeit-Architekturen kann heute ein Codekontext als Adresse für die Ausführung Stream eines Programms betrachtet werden.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine implementiert diese Schnittstelle, um die Position des eine Code-Anweisung an eine Dokumentposition beziehen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Methoden für viele Schnittstellen zurückgeben dieser Schnittstelle, i. d. r. [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Darüber hinaus wird häufig mit der [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) Schnittstelle auch wie in der Lösung breakpointinformationen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden für die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ruft ab, der Dokumentenkontext, der auf den aktiven Code-Kontext entspricht.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ruft die Sprachinformationen für diesen Codekontext ab.|

## <a name="remarks"></a>Hinweise
 Der Hauptunterschied zwischen einer `IDebugCodeContext2` Schnittstelle und eine [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Schnittstelle ist, die eine `IDebugCodeContext2` ist immer Anweisung ausgerichtet. Dies bedeutet, dass ein `IDebugCodeContext2` ist immer an den Anfang einer Anweisung verweist, während ein `IDebugMemoryContext2` können eventuell Hinweise auf jedes beliebige Byte des Arbeitsspeichers in der Laufzeit-Architektur. `IDebugCodeContext2` wird von Anweisungen und nicht von der grundlegenden Speichergröße (in der Regel Byte) erhöht.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)