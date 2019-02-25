---
title: IDebugProgramEx2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99b57aece9b835ac1f2277fdd626a9fdff7b903f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705098"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Diese Schnittstelle kann die Sitzung, die Debug-Manager (SDM) Anfügen an ein Programm und den Programm Knoten mit einem Programm verknüpft.

## <a name="syntax"></a>Syntax

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle auf dasselbe Objekt wie die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, um das SDM an ein Programm angefügt werden soll, während gleichzeitig an ermöglicht Anschlusslieferanten zum Nachverfolgen von allen Sitzungen angefügt ermöglichen die das Programm. Benutzerdefinierte Anschlusslieferanten kann diese Schnittstelle implementieren, wenn er entscheidet.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die SDM-Aufrufe [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugProgram2` Schnittstelle zum Abrufen diese Schnittstelle, um Sitzungen zu verfolgen, die Programme angefügt haben.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugProgramEx2`.

|Methode|Beschreibung|
|------------|-----------------|
|[Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Fügt ein Programm mit einer Sitzung.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ruft ab, der Programm-Knoten, die mit einem Programm verknüpft.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle ist privat zwischen den SDM und dem Programm.

## <a name="requirements"></a>Anforderungen
 Header: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)