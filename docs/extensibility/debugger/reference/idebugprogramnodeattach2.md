---
title: "IDebugProgramNodeAttach2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2-Schnittstelle"
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ermöglicht es einem von einem Versuch Knoten Programm benachrichtigt zu werden, wenn der zugeordneten Programm anzufügen.  
  
## Syntax  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von derselben Klasse implementiert, die die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)\-Schnittstelle, um eine Benachrichtigung des Anfügevorgangs empfangen implementiert und eine Möglichkeit zu geben, den Anfügevorgang abzubrechen.  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die `QueryInterface`\-Methode in einem [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)\-Objekts aufruft.  Die [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)\-Methode muss aufgerufen werden, bevor die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode, um dem Knoten Programm eine Möglichkeit zu geben, den Anfügen an Prozess beenden.  
  
## Methoden in die Vtable\-Reihenfolge  
 Diese Schnittstelle implementiert die folgende Weise:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Fügt dem entsprechenden Programm oder verzögert Anfügen an den Prozess zur [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode.|  
  
## Hinweise  
 Diese Schnittstelle ist die bevorzugte Alternative zur veralteten [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)\-Methode.  Alle von Modulen werden immer mit der `CoCreateInstance`\-Funktion geladen, d.h., werden sie außerhalb des Adressraums des Programms instanziiert, das gedebuggt wird.  
  
 Wenn eine vorherige Implementierung der `IDebugProgramNode2::Attach_V7`\-Methode einfach `GUID` des Programms, das gedebuggt festgelegt wurde, dann nur die [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)\-Methode müssen implementiert werden.  
  
 Wenn eine vorherige Implementierung der `IDebugProgramNode2::Attach_V7`\-Methode die Rückrufschnittstelle, die bereitgestellt wurde, dass Funktionen auf eine Implementierung der [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode und der `IDebugProgramNodeAttach2`\-Schnittstelle verschoben werden muss, muss nicht implementiert werden.  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)