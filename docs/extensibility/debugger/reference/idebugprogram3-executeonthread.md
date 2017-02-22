---
title: "IDebugProgram3::ExecuteOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3::ExecuteOnThread"
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Führt das programm Debugger aus.  Der Thread wird zurückgegeben, um den Debugger Informationen zu geben, in denen Thread der Benutzer angezeigt wird, wenn das Programm ausgeführt wird.  
  
## Syntax  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```c#  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### Parameter  
 `pThread`  
 \[in\]  Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Es gibt drei verschiedene Möglichkeiten, dass ein Debugger die Ausführung fortgesetzt werden kann, nachdem er beendet wurde:  
  
-   Führen Sie aus: Cancel jeden vorherigen Schritt ab, und usw. bis zum nächsten Haltepunkt ausgeführt.  
  
-   Schritts: Cancel jeden alten Schritt ausgeführt und auf den neuen Schritt schließt ab.  
  
-   Fahren Sie fort: Führen Sie erneut aus, und lassen Sie einen alten Schritt aktiv.  
  
 Der Thread, der auf `ExecuteOnThread` übergeben wird, wird beim Entscheiden, die zum Abbrechen wechseln.  Wenn Sie nicht wissen, den Thread ausgeführten führen Sie Löschungen alle Schritte aus.  Bei Kenntnis des Threads, müssen Sie nur den Schritt auf dem aktiven Thread abbrechen.  
  
## Siehe auch  
 [Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)