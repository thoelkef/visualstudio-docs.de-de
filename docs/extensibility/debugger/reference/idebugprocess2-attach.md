---
title: "IDebugProcess2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Attach"
helpviewer_keywords: 
  - "IDebugProcess2::Attach"
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fügt den Debug\- Manager der Sitzung \(SDM\) auf den Vorgang an.  
  
## Syntax  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### Parameter  
 `pCallback`  
 \[in\]  Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)\-Objekt, das für die Ereignisbenachrichtigung verwendet wird.  
  
 `rgguidSpecificEngines`  
 \[in\]  Ein Array von GUIDs für den Debug\- Testprogrammen zu verwendenden Module, die in den Prozess ausgeführt werden.  Dieser Parameter kann ein NULL\-Wert sein.  Weitere Informationen finden Sie in den Hinweisen.  
  
 `celtSpecificEngines`  
 \[in\]  Die Anzahl der Module im Array `rgguidSpecificEngines` Debuggen und die Größe des `rghrEngineAttach` Arrays.  
  
 `rghrEngineAttach`  
 \[in, out\]  Ein Array HRESULT\-Codes durch die Debugmodule zurückgegeben.  Die Größe dieses Arrays wird im `celtSpecificEngines`\-Parameter angegeben.  Jeder Code ist in der Regel entweder `S_OK` oder `S_ATTACH_DEFERRED`.  Der zweite gibt an, dass nur DE keinen Programmen verbunden ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  In der folgenden Tabelle werden weitere mögliche Werte an.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Der angegebene Vorgang wurde bereits an den Debugger angefügt.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Eine Sicherheitsüberprüfung Anfügen der aufgetreten verletzung Prozedur auf.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Ein Desktop Prozess kann nicht an den Debugger angefügt werden.|  
  
## Hinweise  
 Das Anfügen an einen Prozess fügt das SDM auf Alle Programme, die in diesem Prozess ausgeführt werden, der durch die Debugmodule \(DE\) gedebuggt werden kann `rgguidSpecificEngines` im bereitgestellten Array.  Legen Sie den `rgguidSpecificEngines`\-Parameter zu einem NULL\-Wert oder Einschließen `GUID_NULL` im Array fest, um auf Alle Programme im Prozess anhängen.  
  
 Alle Debuggen der Ereignisse, die im Prozess gesendet werden in den angegebenen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)\-Objekt auftreten.  Dieses `IDebugEventCallback2`\-Objekt wird bereitgestellt, wenn das SDM diese Methode aufgerufen wird.  
  
## Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)