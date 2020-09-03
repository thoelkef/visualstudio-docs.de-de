---
title: IDebugEntryPointEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 531ff846f2488193ed7f3d9f200a1a4ea04df6f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730331"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Die Debug-Engine (de) sendet diese Schnittstelle an den Sitzungs-Debug-Manager (SDM), wenn das Programm im Begriff ist, die erste Anweisung des Benutzercodes auszuführen.

## <a name="syntax"></a>Syntax

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle als Teil des normalen Betriebs. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das von de erstellt und sendet dieses Ereignis Objekt, wenn das Programm, das gedebuggt wird, geladen wurde und bereit ist, die erste Anweisung des Benutzercodes auszuführen. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von der SDM bereitgestellt wird, wenn Sie an das Programm angefügt wird, das gedeppt wird.

## <a name="remarks"></a>Bemerkungen
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) wird gesendet, wenn das Programm im Begriff ist, die erste Anweisung auszuführen. Beispielsweise `IDebugEntryPoint2` wird gesendet, wenn das Programm im Begriff ist, die Funktion des Benutzers auszuführen `main` .

 Wenn das von de sendet `IDebugEntryPointEvent2` , sollte sich die aktuelle Code Position in der ersten Anweisung des Benutzercodes befinden, wie z `main` . b..

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
