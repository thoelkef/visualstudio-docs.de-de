---
title: IDebugProgramNodeAttach2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ba1dd00fc661e6b35f30998376c1970096a4d57
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774769"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

