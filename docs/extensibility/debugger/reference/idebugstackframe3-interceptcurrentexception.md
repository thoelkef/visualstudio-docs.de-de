---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords: IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9631f2206705ef6daf36b355aa6cb1d5be6458d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Aufgerufen vom Debugger auf den aktuellen Stapelrahmen an, wenn die aktuelle Ausnahme abzufangen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFlags`  
 [in] Gibt die verschiedenen Aktionen an. Derzeit nur die [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) Wert `IEA_INTERCEPT` wird unterstützt und muss angegeben werden.  
  
 `pqwCookie`  
 [out] Eindeutiger Wert, der eine bestimmte Ausnahme identifiziert.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
 Es folgen die häufigsten Fehler zurückgibt.  
  
|Fehler|Beschreibung|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Die aktuelle Ausnahme nicht abgefangen werden kann.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Der aktuelle Rahmen ist Ausführung noch nicht nach einem Ausnahmehandler noch durchsucht wurde.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Diese Methode wird für diesen Frame nicht unterstützt.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Ausnahme ausgelöst wird, erhält der Debugger-Steuerelement aus der Laufzeit zu wichtigen Zeitpunkten während der Prozess für die Ausnahmebehandlung. Während dieser Schlüssel Momente kann der Debugger dem aktuellen Stapelrahmen bitten, wenn der Frame möchte, die Ausnahme abzufangen. Auf diese Weise ist eine abgefangene Ausnahme im Wesentlichen einen auf dynamische Ausnahmehandler für einen Stapelrahmen entspricht, selbst wenn diesem Stapelrahmen einen Ausnahmehandler (z. B. einen Try/Catch-Block im Programmcode im) vorhanden ist.  
  
 Wenn der Debugger wissen möchte, ob die Ausnahme abgefangen werden sollen, ruft es diese Methode auf der aktuellen Stack-Frame-Objekts. Diese Methode ist verantwortlich für alle Details der Ausnahme zu behandeln. Wenn die [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) Schnittstelle ist nicht implementiert oder das `InterceptStackException` Methodenrückgabe Fehler, und der Debugger weiterhin normal Verarbeitung der Ausnahme.  
  
> [!NOTE]
>  Ausnahmen können also nur in verwaltetem Code abgefangen werden, wenn das Programm, das gerade gedebuggt wird unter .NET zur Laufzeit ausgeführt wird. Natürlich können Drittanbieter-Sprachimplementierer implementieren `InterceptStackException` in ihre eigenen Debugmodule Wenn wechselseitig.  
  
 Nachdem das Abfangen abgeschlossen ist, wird ein [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) signalisiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)