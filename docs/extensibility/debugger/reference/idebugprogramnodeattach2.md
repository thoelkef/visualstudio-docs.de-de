---
title: IDebugProgramNodeAttach2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 255d057154b9814cb81325a737324c18de470bc8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869788"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Ermöglicht es einen Knoten Programm beim Anfügen an das zugeordnete Programm benachrichtigt werden sollen.

## <a name="syntax"></a>Syntax

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird implementiert, für die gleiche Klasse, die implementiert die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle, um einen Anfügevorgang benachrichtigt und bieten eine Möglichkeit zum Abbrechen des Anfügevorgang.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie diese Schnittstelle durch Aufrufen der `QueryInterface` -Methode in einer [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt. Die [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode muss aufgerufen werden, bevor die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode geben Sie dem Program-Knoten eine Möglichkeit, den anfügungsprozess zu beenden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Fügt an die zugeordnete Anwendung oder den anfügungsprozess, verzögert die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle ist die bevorzugte Alternative zu veralteten [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) Methode. Alle Debug-Engines werden immer geladen, mit der `CoCreateInstance` funktionieren, d. h., sie außerhalb des Adressraums des gedebuggten Programm instanziiert werden.

 Wenn von einer früheren Implementierung der `IDebugProgramNode2::Attach_V7` Methode wurde einfach Festlegen der `GUID` des gedebuggten Programm, klicken Sie dann nur der [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode implementiert werden muss.

 Wenn in einer früheren Implementierung der `IDebugProgramNode2::Attach_V7` Methode verwendet die Rückrufschnittstelle, die bereitgestellt wurden, und klicken Sie dann diese Funktionalität auf eine Implementierung der verschoben werden muss die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode und die `IDebugProgramNodeAttach2` Schnittstelle nicht implementiert werden muss.

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)