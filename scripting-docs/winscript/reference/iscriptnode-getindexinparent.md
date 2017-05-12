---
title: "IScriptNode::GetIndexInParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetIndexInParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetIndexInParent"
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IScriptNode::GetIndexInParent
Gibt den Index des Objekts in der untergeordneten Liste des übergeordneten Elements.  
  
## Syntax  
  
```  
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### Parameter  
 `pisn`  
 \[out\] Gibt den Index eines Objekts in der untergeordneten Liste des übergeordneten Elements.  
  
 Wenn diese Methode `IScriptNode` durch ein Objekt aufgerufen wird, das eine Webseite darstellt, gibt 0 dieses Parameters.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptNode\-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)