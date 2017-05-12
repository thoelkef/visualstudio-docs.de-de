---
title: "IDispError::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetNext"
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetNext
Ruft das folgende `IDispError`\-Objekt ab.  
  
## Syntax  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### Parameter  
 `ppde`  
 \[out\] Gibt folgendes `IDispError`\-Objekt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode ruft das folgende `IDispError`\-Objekt ab.  Wenn dies das letzte `IDispError`\-Objekt NULL ist, gibt diese Methode ungültig.  
  
> [!NOTE]
>  Diese Methode ist nicht implementiert.  
  
## Siehe auch  
 [IDispError\-Schnittstelle](../../winscript/reference/idisperror-interface.md)