---
title: "IDebugApplicationNodeEvents::onAttach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onAttach
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onAttach"
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onAttach
Behandelt ein Ereignis, dass das Debuganwendungsknotenobjekt zu einem übergeordneten Knoten angefügt wurde.  
  
## Syntax  
  
```  
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### Parameter  
 `prddpParent`  
 \[in\] Der Debug\- Anwendungsknoten, der das übergeordnete Element dieses Knotens ist.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode behandelt ein Ereignis, dass das Debuganwendungsknotenobjekt zu einem übergeordneten Knoten angefügt wurde.  
  
 Implementierungen der Schnittstelle `IDebugApplicationNode` lösen dieses Ereignis aus.  
  
## Siehe auch  
 [IDebugApplicationNodeEvents\-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)   
 [IDebugApplicationNode\-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)