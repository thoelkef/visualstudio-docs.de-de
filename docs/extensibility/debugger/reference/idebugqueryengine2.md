---
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720655"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Mit dieser Schnittstelle kann der Sitzungsdebug-Manager (SDM) eine Schnittstelle abrufen, die das Debugmodul (DE) darstellt.

## <a name="syntax"></a>Syntax

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle für die Objekte, die die gängigsten DE-Schnittstellen implementieren (z. B. [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)und [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)), um den Zugriff auf die [IDebugEngine2-Schnittstelle](../../../extensibility/debugger/reference/idebugengine2.md) der DE selbst zu ermöglichen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf einer typischen DE-Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugQueryEngine2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Ruft eine benutzerdefinierte Debug-Engine(DE)-Schnittstelle ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird in der Regel in dem Objekt implementiert, das die [IDebugProgram2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogram2.md) implementiert, um kausalitätsbeordierte Strittfunktionen zu unterstützen. Das heißt, wenn der Debugger aus einer Funktion heraustritt, ist die nächste auszuführende Funktion möglicherweise nicht die vorherige Funktion auf dem Stapel, sondern eine Funktion in einem anderen Thread insgesamt. Eine Definition von "Kausalität" finden Sie im [Visual Studio Debugger Glossary](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
