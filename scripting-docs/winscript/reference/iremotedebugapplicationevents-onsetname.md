---
title: "IRemoteDebugApplicationEvents::OnSetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnSetName
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnSetName"
ms.assetid: 524dcff3-fb48-4d8f-8989-73eb539454fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnSetName
Behandelt ein Menge Nameereignis.  
  
## Syntax  
  
```  
HRESULT OnSetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### Parameter  
 `pstrName`  
 \[in\] Der neue Name.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode behandelt eines festgelegten Nameereignis.  
  
## Siehe auch  
 [IRemoteDebugApplicationEvents\-Schnittstelle](../../winscript/reference/iremotedebugapplicationevents-interface.md)