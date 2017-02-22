---
title: "IDebugCanStopEvent2::GetReason | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::GetReason"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::GetReason"
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Grund ab, weshalb das Debugmodul \(DE\) beendet werden soll.  
  
## Syntax  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```c#  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### Parameter  
 `pcr`  
 \[out\]  Gibt einen Wert aus der [CANSTOP\_REASON](../../../extensibility/debugger/reference/canstop-reason.md)\-Enumeration zurück, der den Grund für dieses Ereignis beschreibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird in der Regel vor der [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)\-Methode aufgerufen, damit der Aufrufer bestimmen, ob Wert ungleich 0 \(`TRUE`\) zur `IDebugCanStopEvent2::CanStop`\-Methode führt.  
  
 Der Grund für das Beenden `CANSTOP_ENTRYPOINT`kann jedes sein, das heißt dass DE einen Einstiegspunkt erreicht ist oder `CANSTOP_STEPIN`, das heißt die DE in eine Funktion aufgetreten ist.  
  
## Siehe auch  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP\_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)