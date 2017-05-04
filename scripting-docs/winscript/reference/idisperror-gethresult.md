---
title: "IDispError::GetHresult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHresult
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHresult"
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHresult
Ruft den Fehlercode vom `IDispError`\-Objekt ab.  
  
## Syntax  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### Parameter  
 `phr`  
 \[out\] Gibt den Fehlercode an.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode ruft den Fehlercode vom `IDispError`\-Objekt ab.  
  
> [!NOTE]
>  Diese Methode ist nicht implementiert.  
  
## Siehe auch  
 [IDispError\-Schnittstelle](../../winscript/reference/idisperror-interface.md)