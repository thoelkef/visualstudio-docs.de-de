---
title: "IDebugApplication::RemoveStackFrameSniffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.RemoveStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::RemoveStackFrameSniffer"
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::RemoveStackFrameSniffer
Entfernt einen Stapelrahmenenumeratoranbieter aus der Anwendung.  
  
## Syntax  
  
```  
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### Parameter  
 `dwCookie`  
 \[in\] Das Cookie, das durch die `AddStackFrameSniffer`\-Methode zurückgegeben wird, als der Stapelrahmenenumeratoranbieter hinzugefügt wurde.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Die `RemoveStackFrameSniffer`\-Methode entfernt einen Stapelrahmenenumeratoranbieter aus der Anwendung.  
  
## Siehe auch  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugStackFrameSniffer\-Schnittstelle](../../winscript/reference/idebugstackframesniffer-interface.md)