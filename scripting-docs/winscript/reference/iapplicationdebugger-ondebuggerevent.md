---
title: "IApplicationDebugger::onDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onDebuggerEvent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onDebuggerEvent"
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onDebuggerEvent
Behandelt ein benutzerdefiniertes Anwendungsereignis.  
  
## Syntax  
  
```  
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### Parameter  
 `riid`  
 \[in\] Der Schnittstellenbezeichner für das Objekt.  
  
 `punk`  
 \[in\] Das Ereignisobjekt, das die durch `riid` definierte Schnittstelle implementiert.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode wird derzeit nicht implementiert.|  
  
## Hinweise  
 Die Semantik `IUnknown` ist vollständig Anwendung\/der definierte Debugger.  
  
 Mit dieser Methode können benutzerdefinierte Erweiterungen des Debuggermodells zu; sie wird derzeit implementiert.  
  
 Diese Methode wird aufgerufen, wenn `IDebugApplication::FireDebuggerEvent` aufgerufen wird.  
  
## Siehe auch  
 [IApplicationDebugger\-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)