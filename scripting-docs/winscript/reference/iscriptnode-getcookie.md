---
title: "IScriptNode::GetCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetCookie
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetCookie"
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IScriptNode::GetCookie
Gibt einen anwendungsdefinierten Wert zurück, der verwendet wird, um ein Skriptlet mit dem Hostobjekt zuzuordnen.  
  
## Syntax  
  
```  
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### Parameter  
 `pdwCookie`  
 \[out\] Gibt für ein `IScriptEntry`\-Objekt den anwendungsdefinierten Cookiewert zurück.  
  
 Ein `IScriptNode`\-Objekt, das eine Webseite darstellt, gibt 0 zurück.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptNode\-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)