---
title: "IDebugEventCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2"
helpviewer_keywords: 
  - "IDebugEventCallback2"
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird durch das Debugmodul \(DE\) verwendet wird, um Ereignisse Debuggen auf Debuggen von Manager der Sitzung \(SDM\) zu senden.  
  
## Syntax  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementiert diese Schnittstelle, um Ereignisse von einem Debugbuild Modul zu empfangen.  
  
## Hinweise für Aufrufer  
 Ein Debuggen Modul empfängt es sich in der Regel um diese Schnittstelle, wenn das SDM [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)oder [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)aufruft.  Ein Modul Ereignisse sendet SDM zum Debuggen mit [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)aufruft.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugEventCallback2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Sendet eine Benachrichtigung über das Debuggen von Ereignissen zum SDM.|  
  
## Hinweise  
 Obwohl [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) angeben, dass sie eine `IDebugEventCallback2`\-Schnittstelle verwenden, ist dies nicht der Fall, und der Schnittstellenzeiger ist immer ein NULL\-Wert.  Stattdessen muss das Debugmodul die `IDebugEventCallback2`\-Schnittstelle verwenden, die im Aufruf von [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)oder [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)empfangen wird.  
  
 Wenn ein Paket [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) in verwaltetem Code implementiert, wird es dringend empfohlen, dass <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> auf den verschiedenen Schnittstellen aufgerufen wird, die [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)übergeben werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)