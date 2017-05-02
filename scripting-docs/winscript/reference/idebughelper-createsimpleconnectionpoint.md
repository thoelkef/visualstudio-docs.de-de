---
title: "IDebugHelper::CreateSimpleConnectionPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreateSimpleConnectionPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreateSimpleConnectionPoint"
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreateSimpleConnectionPoint
Gibt eine Ereignisschnittstelle zurück, die ein angegebenes Objekt `IDispatch` umschließt.  
  
## Syntax  
  
```  
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp   
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### Parameter  
 `pdisp`  
 \[in\] Das `IDispatch`\-Objekt an den Umbruch.  
  
 `ppscp`  
 \[out\] Die Ereignisschnittstelle, die `pdisp` umschließt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Gibt eine Ereignisschnittstelle zurück, die angegebene `IDispatch` umschließt \(finden Sie [ISimpleConnectionPoint\-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)\).  
  
## Siehe auch  
 [IDebugHelper\-Schnittstelle](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint\-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)