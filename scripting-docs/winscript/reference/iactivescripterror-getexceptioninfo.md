---
title: "IActiveScriptError::GetExceptionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetExceptionInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetExceptionInfo"
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetExceptionInfo
Ruft Informationen über einen Fehler ab, der aufgetreten ist, während das Skriptmodul ein Skript ausführen.  
  
## Syntax  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### Parameter  
 `pexcepinfo`  
 \[out\] Adresse einer `EXCEPINFO`\-Struktur, die Fehlerinformationen abruft.  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder `E_FAIL`, wenn ein Fehler aufgetreten ist.  
  
## Siehe auch  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)