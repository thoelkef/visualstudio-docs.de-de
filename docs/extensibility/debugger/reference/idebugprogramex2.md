---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722330"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Mit dieser Schnittstelle kann der Session-Debug-Manager (SDM) an ein Programm angefügt werden und den Programmknoten einem Programm zugeordnet werden.

## <a name="syntax"></a>Syntax

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle auf demselben Objekt wie die [IDebugProgram2-Schnittstelle,](../../../extensibility/debugger/reference/idebugprogram2.md) um das SDM an ein Programm anfügen zu lassen und gleichzeitig dem Portlieferanten zu ermöglichen, alle an das Programm angehängten Sitzungen zu verfolgen. Der benutzerdefinierte Portlieferant kann diese Schnittstelle implementieren, wenn er dies auswählt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Das SDM ruft [QueryInterface](/cpp/atl/queryinterface) auf einer `IDebugProgram2` Schnittstelle auf, um diese Schnittstelle zum Nachverfolgen von Sitzungen zu erhalten, die an Programme angeschlossen sind.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProgramEx2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Fügt ein Programm an eine Sitzung an.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ruft den Programmknoten ab, der einem Programm zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ist privat zwischen dem SDM und dem Programm.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
