---
title: "IEnumDebugCodeContexts::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Clone"
ms.assetid: eaad6af9-4a0a-49c9-8f73-bccaa42b235c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Clone
Erstellt einen Enumerator, der den gleichen Zustand wie der aktuelle Enumerator enthält.  
  
## Syntax  
  
```  
HRESULT Clone(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### Parameter  
 `ppescc`  
 \[out\] Gibt die `IEnumDebugCodeContexts`\-Schnittstelle des Klons des Enumerators zurück.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode erstellt einen Enumerator, der denselben Zustand wie der aktuelle Enumerator enthält.  
  
## Siehe auch  
 [IEnumDebugCodeContexts\-Schnittstelle](../../winscript/reference/ienumdebugcodecontexts-interface.md)