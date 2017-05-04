---
title: "IDebugApplicationNode::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.EnumChildren
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::EnumChildren"
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::EnumChildren
Listet die untergeordneten Knoten des Anwendungsknotens auf.  
  
## Syntax  
  
```  
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### Parameter  
 `pperddp`  
 \[out\] Die Enumeration der untergeordneten Knoten des Knotens.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode listet die untergeordneten Knoten des Anwendungsknotens auf.  
  
## Siehe auch  
 [IDebugApplicationNode\-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)