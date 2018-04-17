---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a83f5635dfacb638a2e76054dc5ed4e887e2a3cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Ermöglicht es einem Programm-Knoten, der beim Anfügen an das zugeordnete Programm benachrichtigt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird implementiert, auf die gleiche Klasse, implementiert die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle, um Benachrichtigungen zu einem Anfügevorgang und bieten eine Möglichkeit zum Abbrechen des Anfügevorgangs.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle durch Aufrufen der `QueryInterface` Methode in einer [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt. Die [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode muss aufgerufen werden, bevor die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode, um dem Knoten für die Anwendung beenden den Prozess anfügen kann.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Fügt an die zugeordnete Anwendung oder den Prozess anfügen, verzögert die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ist die bevorzugte Alternative zu veralteten [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) Methode. Alle Debugmodule werden immer geladen, mit der `CoCreateInstance` funktionieren, d. h. sie außerhalb des Adressraums des zu debuggenden Programms instanziiert werden.  
  
 Wenn einer früheren Implementierung der `IDebugProgramNode2::Attach_V7` Methode wurde einfach Festlegen der `GUID` des Programms, der debuggt wird, klicken Sie dann nur die [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode muss implementiert werden.  
  
 Wenn einer früheren Implementierung der `IDebugProgramNode2::Attach_V7` Methode verwendet die Rückrufschnittstelle, das bereitgestellt wurde, dann wird diese Funktion muss eine Implementierung von verschoben werden die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode und die `IDebugProgramNodeAttach2` Schnittstelle nicht implementiert werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)