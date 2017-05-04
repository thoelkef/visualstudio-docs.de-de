---
title: "IRemoteDebugApplication::EnumGlobalExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.EnumGlobalExpressionContexts
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::EnumGlobalExpressionContexts"
ms.assetid: 61598a34-f409-42a2-810d-a9e92e2f4861
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::EnumGlobalExpressionContexts
Listet die globalen Ausdruckskontexte für alle Sprachen aufgeführt, die in dieser Anwendung ausgeführt werden.  
  
## Syntax  
  
```  
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### Parameter  
 `ppedec`  
 \[out\] Enumerator, der die globalen Ausdruckskontexte für alle Sprachen aufgeführt werden, die in dieser Anwendung ausgeführt werden.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode listet die globalen Ausdruckskontexte für alle Sprachen aufgeführt, die in dieser Anwendung ausgeführt werden.  
  
## Siehe auch  
 [IRemoteDebugApplication\-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)