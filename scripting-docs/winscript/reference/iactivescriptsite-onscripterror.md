---
title: "IActiveScriptSite::OnScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptError"
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptError
Informiert den Host, dass ein Ausführungsfehler aufgetreten ist, während das Modul das Skript ausgeführt hat.  
  
## Syntax  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### Parameter  
 `pase`  
 \[in\] Die Adresse der [IActiveScriptError](../../winscript/reference/iactivescripterror.md)\-Schnittstelle des Fehlerobjekts.  Ein Host kann diese Schnittstelle verwenden, um Informationen über abzurufen den Ausführungsfehler.  
  
## Rückgabewert  
 Gibt `S_OK` zurück, wenn der Fehler ordnungsgemäß behandelt wurde, oder ein OLE definierte Fehlercode andernfalls.  
  
## Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)