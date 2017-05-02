---
title: "IBindEventHandler::BindHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IBindEventHandler.BindHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IBindEventHandler::BindHandler"
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IBindEventHandler::BindHandler
Umschließt ein Ereignis zu einem Objekt.  
  
## Syntax  
  
```  
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### Parameter  
 `pstrEvent`  
 \[in\] Gibt das Ereignis an, um zu behandeln.  
  
 `pdisp`  
 \[in\] Gibt das Objekt an, das Ereignis zu behandeln.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Mit dieser Methode wird ein Ereignis zu einem Objekt.  
  
## Siehe auch  
 [IBindEventHandler\-Schnittstelle](../../winscript/reference/ibindeventhandler-interface.md)