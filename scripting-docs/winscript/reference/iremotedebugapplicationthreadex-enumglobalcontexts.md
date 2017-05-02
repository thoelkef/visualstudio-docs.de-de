---
title: "IRemoteDebugApplicationThreadEx:EnumGlobalContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThreadEx:EnumGlobalContexts
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThreadEx:EnumGlobalContexts"
ms.assetid: a6c0bc3f-4afc-41e1-b734-06e252c5b171
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IRemoteDebugApplicationThreadEx:EnumGlobalContexts
Listet die globalen Ausdruckskontexte für alle Sprachen aufgeführt, die in diesen Thread ausgeführt werden.  
  
## Syntax  
  
```  
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\] Enumerator, der die globalen Ausdruckskontexte für alle Sprachen aufgeführt werden, die in diesen Thread ausgeführt werden.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise