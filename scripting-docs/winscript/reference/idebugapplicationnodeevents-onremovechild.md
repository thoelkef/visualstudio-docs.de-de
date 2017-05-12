---
title: "IDebugApplicationNodeEvents::onRemoveChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onRemoveChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onRemoveChild"
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onRemoveChild
Behandelt das Ereignis, wenn ein untergeordneter Knoten von einem Debuganwendungsknotenobjekt entfernt wird.  
  
## Syntax  
  
```  
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### Parameter  
 `prddpChild`  
 \[in\] Der untergeordnete Anwendungsknoten, der entfernt wurde.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode behandelt das Ereignis, wenn ein untergeordneter Knoten von einem Debuganwendungsknotenobjekt entfernt wird.  
  
 Implementierungen der Schnittstelle `IDebugApplicationNode` lösen dieses Ereignis aus.  
  
## Siehe auch  
 [IDebugApplicationNodeEvents\-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)   
 [IDebugApplicationNode\-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)