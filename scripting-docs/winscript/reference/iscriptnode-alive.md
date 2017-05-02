---
title: "IScriptNode::Alive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Alive
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Alive"
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptNode::Alive
Gibt an, ob ein Objekt noch aktiv ist.  
  
## Syntax  
  
```  
HRESULT Alive();  
```  
  
#### Parameter  
 Die Methode enthält keine Parameter.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Der Skripts\-Knoten ist weiterhin aktiv.|  
  
## Hinweise  
 Wenn das Objekt nicht aktiv ist, gibt COM \(Component Object Model\) einen Fehler aus Marshallingsproxy für Aufrufe dieser Methode zurück.  
  
## Siehe auch  
 [IScriptNode\-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)