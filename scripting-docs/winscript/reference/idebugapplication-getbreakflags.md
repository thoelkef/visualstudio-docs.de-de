---
title: "IDebugApplication::GetBreakFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.GetBreakFlags
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::GetBreakFlags"
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::GetBreakFlags
Gibt die aktuellen Unterbrechungsflags für die Anwendung zurück.  
  
## Syntax  
  
```  
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### Parameter  
 `pabf`  
 \[out\] Die aktuellen Unterbrechungsflags für die Anwendung.  
  
 `pprdatSteppingThread`  
 \[out\] Der momentan ausgeführten Thread.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt die aktuellen Unterbrechungsflags für die Anwendung zurück.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [APPBREAKFLAGS\-Enumeration](../../winscript/reference/appbreakflags-enumeration.md)