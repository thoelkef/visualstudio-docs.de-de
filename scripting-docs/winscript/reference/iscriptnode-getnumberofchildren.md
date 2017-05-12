---
title: "IScriptNode::GetNumberOfChildren | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetNumberOfChildren
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetNumberOfChildren"
ms.assetid: 3451c7e9-cb50-482e-9038-6e7d7ce1ecdf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptNode::GetNumberOfChildren
Gibt die Anzahl der untergeordneten Knoten des `IScriptNode`\-Objekts zurück.  
  
## Syntax  
  
```  
HRESULT GetNumberOfChildren(  
   ULONG              *pcsn  
);  
```  
  
#### Parameter  
 `pcsn`  
 \[out\] Die Anzahl der untergeordneten Knoten, die das `IScriptNode`\-Objekt verfügt.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptNode\-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)