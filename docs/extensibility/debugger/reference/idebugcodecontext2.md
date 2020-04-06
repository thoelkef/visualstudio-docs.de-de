---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734211"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Diese Schnittstelle stellt die Ausgangsposition einer Codeanweisung dar. Für die meisten Laufzeitarchitekturen heute kann ein Codekontext als Adresse im Ausführungsstream eines Programms betrachtet werden.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul implementiert diese Schnittstelle, um die Position einer Codeanweisung mit einer Dokumentposition zu verknüpfen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Methoden auf vielen Schnittstellen geben diese Schnittstelle zurück, in der Regel [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Es wird auch ausgiebig mit der [IDebugDisassemblyStream2-Schnittstelle](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) sowie in Haltepunktauflösungsinformationen verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden auf der [IDebugMemoryContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugmemorycontext2.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ruft den Dokumentkontext ab, der dem aktiven Codekontext entspricht.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ruft die Sprachinformationen für diesen Codekontext ab.|

## <a name="remarks"></a>Bemerkungen
 Der Hauptunterschied `IDebugCodeContext2` zwischen einer Schnittstelle und einer [IDebugMemoryContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugmemorycontext2.md) besteht darin, dass eine `IDebugCodeContext2` immer in Anweisung ausgerichtet ist. Dies bedeutet, dass ein `IDebugCodeContext2` immer auf den `IDebugMemoryContext2` Anfang einer Anweisung zeigt, während ein auf ein beliebiges Byte des Speichers in der Laufzeitarchitektur verweisen kann. `IDebugCodeContext2`wird durch Anweisungen und nicht durch die grundlegende Speichergröße (in der Regel Byte) erhöht.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Weiter](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
