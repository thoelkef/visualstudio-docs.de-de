---
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720684"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Diese Schnittstelle marshallt programmbezogene Schnittstellen über Prozessgrenzen hinweg.

## <a name="syntax"></a>Syntax

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) implementiert, um Marshallingschnittstellen über Prozessgrenzen hinweg zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf einer `IDebugProgramNode2` Schnittstelle auf, um diese Schnittstelle zu erhalten. Wenn diese Schnittstelle nicht abgerufen werden kann, unterstützt die DE das Marshalling von Schnittstellen nicht.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ruft eine angegebene Schnittstelle über Prozessgrenzen hinweg ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird implementiert, wenn die DE in einem separaten Prozessbereich vom zu debuggenden Programm ausgeführt wird, z. B. wenn die DE im Visual Studio-Prozessbereich anstelle des Prozessraums des zu debuggenden Programms ausgeführt wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
