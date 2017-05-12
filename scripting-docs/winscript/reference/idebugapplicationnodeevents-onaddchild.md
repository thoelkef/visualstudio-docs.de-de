---
title: "IDebugApplicationNodeEvents::onAddChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onAddChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onAddChild"
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onAddChild
Behandelt das Ereignis, wenn ein untergeordneter Knoten zu einem Debuganwendungsknotenobjekt hinzugefügt wird.  
  
## Syntax  
  
```  
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### Parameter  
 `prddpChild`  
 \[in\] Der untergeordnete Debug\- Anwendungsknoten, der hinzugefügt wurde.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode behandelt das Ereignis, wenn ein untergeordneter Knoten zu einem Debuganwendungsknotenobjekt hinzugefügt wird.  
  
 Implementierungen der `IDebugApplicationNode`\-Schnittstelle lösen dieses Ereignis aus  
  
## Siehe auch  
 [IDebugApplicationNodeEvents\-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)   
 [IDebugApplicationNode\-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)