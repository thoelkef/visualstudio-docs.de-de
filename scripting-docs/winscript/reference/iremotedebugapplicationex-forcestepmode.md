---
title: "IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:ForceStepMode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:ForceStepMode"
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:ForceStepMode
Erzwingt den Debugger in einschrittigen Modus.  
  
## Syntax  
  
```  
HRESULT ForceStepMode(  
   IRemoteDebugApplicationThread*  pStepThread  
);  
```  
  
#### Parameter  
 `pStepThread`  
 \[in\] Debuggen Thread zum Prozess Bildschirm, um zu durchlaufen.  Wenn NULL, das PDM seinen Tretenthread gelöscht wird.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IRemoteDebugApplicationEx Interface](http://msdn.microsoft.com/de-de/2f65fa67-06b7-4053-8945-22383ab66343)