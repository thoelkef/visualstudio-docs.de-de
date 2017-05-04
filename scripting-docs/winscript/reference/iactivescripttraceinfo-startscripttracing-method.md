---
title: "IActiveScriptTraceInfo::StartScriptTracing-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptTraceInfo::StartScriptTracing-Methode
Anfangsskriptablaufverfolgung.  
  
## Syntax  
  
```  
HRESULT StartScriptTracing(   
    [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,   
    [in] GUID guidContextID   
);  
  
```  
  
#### Parameter  
 `pSiteTraceInfo`  
 Ein Zeiger auf IActiveScriptSiteTraceInfo des Hosts.  
  
 `guidContextId`  
 Der GUID des Kontexts.  
  
## Rückgabewert  
 Die möglichen Rückgabewerte für diese Methode sind die folgenden:  
  
1.  S\_OK: Erfolg.  
  
2.  E\_POINTER: `pSiteTraceInfo` ist ein NULL\-Zeiger.  
  
3.  E\_NOTIMPL: Nicht implementiert.