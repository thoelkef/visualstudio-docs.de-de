---
title: "IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::DiagnoseWebDebuggingError"
helpviewer_keywords: 
  - "IDebugCoreServer3::DiagnoseWebDebuggingError"
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3::DiagnoseWebDebuggingError
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Versucht, selbstklebendes zu bestimmen, warum ein Fehler aufgetreten.  
  
## Syntax  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```c#  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### Parameter  
 `pszUrl`  
 \[in\]  Derzeit nicht verwendet. muss immer auf einen NULL\-Wert festgelegt werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Im Folgenden werden andere typische Rückgabecodes:  
  
|Code|Beschreibung|  
|----------|------------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Kann warum den Remoteserver, der nicht ermitteln konnte, das Debuggen begonnen wird.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Kann nicht auf Remoteserver, möglicherweise aufgrund fehlender Berechtigungen debuggen, da das DEBUG\-Verb nicht aktiviert ist.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Der Webserver ist gesperrt und das DEBUG\-Verb blockiert, das erforderlich ist, um das Debuggen zu aktivieren.|  
  
## Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)