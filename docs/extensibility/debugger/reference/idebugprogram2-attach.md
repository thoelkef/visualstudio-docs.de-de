---
title: "IDebugProgram2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Attach"
helpviewer_keywords: 
  - "IDebugProgram2::Attach"
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fügt dem Programm an.  
  
## Syntax  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### Parameter  
 `pCallback`  
 \[in\]  Ein für die Ereignisbenachrichtigung verwendet werden soll [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)\-Objekt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  In der folgenden Tabelle sind einige mögliche Fehlercodes an.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Das angegebene Programm wurde bereits an den Debugger angefügt.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Eine Sicherheitsüberprüfung Anfügen der aufgetreten verletzung Prozedur auf.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Ein Desktop programm kann nicht an den Debugger angefügt werden.|  
  
## Hinweise  
 Ein Modul \(Debug\) DE wird nie diese Methode auf, um zu einem Programm anzufügen.  Wenn DE im Adressbereich des Programms ausgeführt wird, wird die [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)\-Methode aufgerufen.  Wenn die DE\-Ausführungen in der Sitzung den Adressbereich des Managers \(SDM\) debuggen, wird die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode aufgerufen.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)