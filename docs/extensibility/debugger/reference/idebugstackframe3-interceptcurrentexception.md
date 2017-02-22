---
title: "IDebugStackFrame3::InterceptCurrentException | Microsoft Docs"
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
  - "IDebugStackFrame3::InterceptCurrentException"
helpviewer_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wird vom Debugger im aktuellen Stapelrahmen, wenn sie die aktuelle Ausnahme abfangen sollen.  
  
## Syntax  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```c#  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### Parameter  
 `dwFlags`  
 \[in\]  Gibt verschiedene Aktionen an.  Derzeit wird nur der Wert [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) unterstützt wird `IEA_INTERCEPT` und muss angegeben werden.  
  
 `pqwCookie`  
 \[out\]  Eindeutiger Wert, der einer bestimmten Ausnahme angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
 Nachfolgend sind der häufigste Fehlers beendet wird.  
  
|Fehler|Beschreibung|  
|------------|------------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Die aktuelle Ausnahme nicht abgefangen werden.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Die aktuellen Skinframes Ausführung noch einen Handler für nicht gefunden wurde.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Diese Methode wird nicht für die dieser Frame unterstützt.|  
  
## Hinweise  
 Wenn eine Ausnahme ausgelöst wird, der Debugger gewinn die Steuerung von der Laufzeit Punkt während des Ausnahmebehandlungsprozesses.  Während dieser Schlüssel momente kann der Debugger den aktuellen Stapelrahmen anfordern, wenn der Frame die Ausnahme abfangen möchten.  Auf diese Weise ist eine abgefangene Ausnahme im Grunde ein direkter Ausnahmehandler für einen Stapelrahmen, auch wenn dieser Stapelrahmen keinen Ausnahmehandler hat \(z. B. einen try\/catch\-Block im Programmcode\).  
  
 Wenn der Debugger wissen möchte, wenn die Ausnahme abgefangen wird, ruft diese Methode für den aktuellen Stapelrahmen Objekt an.  Diese Methode dient zum Behandeln aller Details der Ausnahme.  Wenn die [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)\-Schnittstelle nicht implementiert wird oder die `InterceptStackException`\-Methode jeden Fehler zurückgibt, führt der Debugger die Ausnahme verarbeitet gewöhnlich auf Weiter.  
  
> [!NOTE]
>  Ausnahmen können nur in verwaltetem Code abgefangen werden, d. h. wenn das Programm, das gedebuggt wird, unter der .NET\-Laufzeit ausgeführt wird.  Natürlich können von Drittanbietern Sprachen in ihren eigenen Implementierungen `InterceptStackException` Debuggen die Option Module implementieren, wenn sie so auswählen.  
  
 Nachdem das Abfangen abgeschlossen ist, wird [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) signalisiert.  
  
## Siehe auch  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)