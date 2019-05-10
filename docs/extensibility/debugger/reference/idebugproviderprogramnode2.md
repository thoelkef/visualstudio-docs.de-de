---
title: IDebugProviderProgramNode2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f9e0756c3cb9e92d0899020383d536b83892046
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458761"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Diese Schnittstelle marshallt Programm sammlungsbezogene Schnittstellen über Prozessgrenzen hinweg.

## <a name="syntax"></a>Syntax

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle für das gleiche Objekt, das implementiert [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Marshalling Schnittstellen über Prozessgrenzen hinweg zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugProgramNode2` Schnittstelle, um diese Schnittstelle zu erhalten. Wenn diese Schnittstelle kann nicht abgerufen werden, unterstützt die DE kein Marshalling von Schnittstellen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ruft eine angegebene Schnittstelle über Prozessgrenzen hinweg.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle wird implementiert, wenn die DE aus der zu debuggende Programm wird in einem separaten Prozessbereich ausgeführt wird: z. B. wenn die DE in den Prozessbereich der Visual Studio anstelle von den Prozessbereich der gedebuggten Programm ausgeführt wird.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)