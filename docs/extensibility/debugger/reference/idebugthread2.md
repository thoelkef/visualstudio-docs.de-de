---
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718593"
---
# <a name="idebugthread2"></a>IDebugThread2
Diese Schnittstelle stellt einen Thread dar, der in einem Programm ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um einen Ausführungsthread in einem einzigen Programm darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) auf, um diese Schnittstelle abzurufen, die den aktuell aktiven Thread darstellt.

 Diese Schnittstelle wird auch zum Erstellen einer Haltepunktanforderung verwendet (siehe [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Diese Schnittstelle wird auch zurückgegeben, wenn ein gebundener oder Fehlerhaltepunkt aufgelöst wird (siehe [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) und [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugThread2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Ruft eine Liste der Stapelrahmen für diesen Thread ab.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Ruft den Namen des Threads ab.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Legt den Namen des Threads fest.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Ruft das Programm ab, in dem ein Thread ausgeführt wird.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Legt fest, ob die nächste Anweisung auf den angegebenen Stapelrahmen und Codekontext festgelegt werden kann.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Legt die nächste Anweisung für den angegebenen Stapelrahmen und Codekontext fest.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Ruft den Systemthreadbezeichner ab.|
|[Angehalten](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Hält einen Thread an.|
|[Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Setzt einen Thread fort.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Ruft Eigenschaften ab, die einen Thread beschreiben.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Ruft den logischen Thread ab, der diesem physischen Thread zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen
 Da ein einzelner physischer Thread in mehreren `IDebugThread2` Programmen ausgeführt werden kann, kann mehr als ein Von mehr als einem Programm denselben physischen Thread darstellen.

 Wenn ein Haltepunkt oder eine Ausnahme auftritt, wird ein Ereignis durch Aufrufen von [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)gesendet. Eines der Argumente für diese `IDebugThread2` Methode ist eine Schnittstelle, die den aktuellen Thread darstellt. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) wird verwendet, um die [IDebugStackFrame2-Schnittstelle](../../../extensibility/debugger/reference/idebugstackframe2.md) für den aktuellen Stapelrahmen abzuerhalten.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
