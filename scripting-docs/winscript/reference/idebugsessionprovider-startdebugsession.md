---
title: "IDebugSessionProvider::StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProvider.StartDebugSession
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugSessionProvider::StartDebugSession"
ms.assetid: 47697dfb-d4e1-492c-a14f-753e28195a76
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSessionProvider::StartDebugSession
Initiiert eine Debugsitzung mit der angegebenen Anwendung.  
  
## Syntax  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
);  
```  
  
#### Parameter  
 `pda`  
 \[in\] Gibt die Debugsitzung Anwendung.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode initiiert eine Debugsitzung mit der angegebenen Anwendung.  Der Debugger sollte `IRemoteDebugApplication::ConnectDebugger` aufrufen, bevor er von diesem Aufruf zurückgibt.  
  
## Siehe auch  
 [IDebugSessionProvider\-Schnittstelle](../../winscript/reference/idebugsessionprovider-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)