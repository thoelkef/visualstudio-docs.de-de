---
title: "IActiveScriptSiteTraceInfo::SendScriptTraceInfo-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptSiteTraceInfo::SendScriptTraceInfo-Methode
Sendet Ablaufverfolgungsinformationen, die den Ereignistyp, Kontext und die Skriptanweisung umfasst.  
  
## Syntax  
  
```  
HRESULT SendScriptTraceInfo(   
    [in] SCRIPTTRACEINFO stiEventType,   
    [in] GUID guidContextID,   
    [in] DWORD dwScriptContextCookie,   
    [in] LONG lScriptStatementStart,   
    [in] LONG lScriptStatementEnd,   
    [in] DWORD64 dwReserved   
);   
```  
  
#### Parameter  
 `stiEventType`  
 Der Ereignistyp.  
  
 `guidContextId`  
 Der GUID des Kontexts.  
  
 `dwScriptContextCookie`  
 Das Cookie des Kontexts.  
  
 `lScriptStatementStart`  
 Der Speicherort von Anfang der Skriptanweisung.  
  
 `lScriptStatementEnd`  
 Der Speicherort des Stapelrahmens der Skriptanweisung.  
  
 `dwReserved`  
 Reserviert.