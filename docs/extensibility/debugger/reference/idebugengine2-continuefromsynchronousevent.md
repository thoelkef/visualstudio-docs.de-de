---
title: "IDebugEngine2::ContinueFromSynchronousEvent | Microsoft Docs"
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
  - "IDebugEngine2::ContinueFromSynchronousEvent"
helpviewer_keywords: 
  - "IDebugEngine2::ContinueFromSynchronousEvent"
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::ContinueFromSynchronousEvent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wird vom Debugbuild Manager der Sitzung \(SDM\), um anzugeben, dass ein synchrones Debuggen Ereignis, durch das Debugmodul bereits gesendet \(SDM\), um DE, empfangen und verarbeitet wurde.  
  
## Syntax  
  
```cpp#  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2* pEvent  
);  
```  
  
```c#  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2 pEvent  
);  
```  
  
#### Parameter  
 `pEvent`  
 \[in\]  Ein [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Objekt, das das zuvor gesendete synchrone Ereignis darstellt, in dem der Debugger nun fortgesetzt werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 DE muss sicherstellen, dass es sich um die Quelle des Ereignisses ist, das durch den `pEvent`\-Parameter dargestellt wird.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CEngine`\-Objekt implementiert, das die [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)\-Schnittstelle implementiert.  
  
```cpp#  
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)  
{  
   HRESULT hr;  
  
   // Create a pointer to a unique event interface defined for batch file  
   // breaks.    
   IAmABatchFileEvent *pBatEvent;  
   // Check for successful query for the unique batch file event  
   // interface.  
   if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,  
                                       (void **)&pBatEvent)))  
   {  
      // Release the result of the QI.  
      pBatEvent->Release();  
      // Check thread message for notification to continue.  
      if (PostThreadMessage(GetCurrentThreadId(),  
                            WM_CONTINUE_SYNC_EVENT,  
                            0,  
                            0))  
      {    
         hr = S_OK;  
      }  
      else  
      {  
         hr = HRESULT_FROM_WIN32(GetLastError());  
      }  
   }  
   else  
   {  
      hr = E_INVALIDARG;  
   }  
   return hr;  
}  
```  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)