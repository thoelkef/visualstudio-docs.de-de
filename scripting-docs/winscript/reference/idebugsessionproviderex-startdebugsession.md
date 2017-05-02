---
title: "IDebugSessionProviderEx:StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProviderEx:StartDebugSession
apilocation: scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugSessionProviderEx:StartDebugSession
Initiiert eine Debugsitzung mit der angegebenen Anwendung.  
  
## Syntax  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### Parameter  
 `pda`  
 \[in\] Gibt die Debugsitzung Anwendung.  
  
 `fQuery`  
 \[in\] Gibt True eine Abfrage an.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode initiiert eine Debugsitzung mit der angegebenen Anwendung.  Der Debugger sollte `IRemoteDebugApplication::ConnectDebugger` aufrufen, bevor er von diesem Aufruf zurückgibt.  
  
## Siehe auch  
 [IDebugSessionProviderEx\-Schnittstelle](../../winscript/reference/idebugsessionproviderex-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)