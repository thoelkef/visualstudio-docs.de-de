---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721822"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Ermöglicht die Benachrichtigung eines Programmknotens über den Versuch, eine Verbindung an das zugeordnete Programm anzufügen.

## <a name="syntax"></a>Syntax

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird auf derselben Klasse implementiert, die die [IDebugProgramNode2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogramnode2.md) implementiert, um eine Benachrichtigung über einen Anfügevorgang zu erhalten und die Möglichkeit zum Abbrechen des Anfügevorgangs bereitzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie diese `QueryInterface` Schnittstelle ab, indem Sie die Methode in einem [IDebugProgramNode2-Objekt](../../../extensibility/debugger/reference/idebugprogramnode2.md) aufrufen. Die [OnAttach-Methode](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) muss vor der [Attach-Methode](../../../extensibility/debugger/reference/idebugengine2-attach.md) aufgerufen werden, um dem Programmknoten die Möglichkeit zu geben, den Anfügevorgang zu beenden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Fügt an das zugeordnete Programm an, oder [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) verschiebt den Anfügeprozess an die Attach-Methode.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ist die bevorzugte Alternative zur veralteten [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) Methode. Alle Debug-Module werden `CoCreateInstance` immer mit der Funktion geladen, d. h. sie werden außerhalb des Adressraums des zu debuggenden Programms instanziiert.

 Wenn eine vorherige `IDebugProgramNode2::Attach_V7` Implementierung der Methode `GUID` einfach die des zu debuggenden Programms festlegt, muss nur die [OnAttach-Methode](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) implementiert werden.

 Wenn eine vorherige `IDebugProgramNode2::Attach_V7` Implementierung der Methode die bereitgestellte Rückrufschnittstelle verwendet hat, muss diese Funktionalität in `IDebugProgramNodeAttach2` eine Implementierung der [Attach-Methode](../../../extensibility/debugger/reference/idebugengine2-attach.md) verschoben werden, und die Schnittstelle muss nicht implementiert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
