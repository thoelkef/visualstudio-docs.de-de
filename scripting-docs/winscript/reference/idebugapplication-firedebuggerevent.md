---
title: "IDebugApplication::FireDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FireDebuggerEvent
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FireDebuggerEvent"
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FireDebuggerEvent
Löst ein generisches Ereignis zur `IApplicationDebugger`\-Schnittstelle des Debuggers aus.  
  
## Syntax  
  
```  
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### Parameter  
 `riid`  
 \[in\] Ein GUID für das Objekt.  
  
 `punk`  
 \[in\] Ein Ereignisobjekt übergeben Sie an den Debugger.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode wird derzeit nicht implementiert.|  
  
## Hinweise  
 Die Semantik des GUID und `IUnknown` sind vollständig Anwendung\/der definierte Debugger.  
  
 Mit dieser Methode können benutzerdefinierte Erweiterungen des Debuggermodells zu; sie wird derzeit implementiert.  
  
 Diese Methode wird `IApplicationDebugger::onDebuggerEvent` aufgerufen werden.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)