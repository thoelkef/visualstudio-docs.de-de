---
title: "IEnumDebugApplicationNodes::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Clone
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Clone"
ms.assetid: 7190954d-e2da-4a84-8e37-81d4d27886a8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Clone
Erstellt einen Enumerator, der den gleichen Zustand wie der aktuelle Enumerator enthält.  
  
## Syntax  
  
```  
HRESULT Clone(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### Parameter  
 `pperddp`  
 \[out\] Gibt die `IEnumDebugApplicationNodes`\-Schnittstelle des Klons des Enumerators zurück.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode erstellt einen Enumerator, der denselben Zustand wie der aktuelle Enumerator enthält.  
  
## Siehe auch  
 [IEnumDebugApplicationNodes\-Schnittstelle](../../winscript/reference/ienumdebugapplicationnodes-interface.md)