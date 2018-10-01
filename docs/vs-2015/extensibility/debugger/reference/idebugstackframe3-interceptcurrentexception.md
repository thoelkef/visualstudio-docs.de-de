---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80bb98c22ecd220b4dbb8d817eb8bad6351e37bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516041"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugStackFrame3::InterceptCurrentException](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception).  
  
Aufgerufen vom Debugger auf dem aktuellen Stapelrahmen an, wenn die aktuelle Ausnahme abzufangen.  
  
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
 [out] Eindeutiger Wert identifiziert eine bestimmte Ausnahme.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
 Im folgenden werden die häufigsten Fehler zurückgibt.  
  
|Fehler|Beschreibung|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Die aktuelle Ausnahme kann nicht abgefangen werden.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Der aktuelle Frame für die Ausführung noch nicht nach einem Handler noch durchsucht wurde.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Diese Methode wird für diesen Frame nicht unterstützt.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Ausnahme ausgelöst wird, erhält der Debugger-Steuerelement aus der Laufzeit an wichtigen Punkten während der Prozess für die Ausnahmebehandlung. Während diese wichtigen stellen kann der Debugger dem aktuellen Stapelrahmen bitten, wenn möchte, dass der Frame die Ausnahme abzufangen. Auf diese Weise ist eine abgefangene Ausnahme im Wesentlichen einen auf dynamische Ausnahmehandler für einen Stapelrahmen, auch wenn dieser Stapelrahmen nicht über einen Ausnahmehandler (z. B. einen Try/Catch-Block im Programmcode) verfügt.  
  
 Wenn der Debugger wissen möchte, ob die Ausnahme abgefangen werden soll, ruft sie diese Methode, an dem aktuellen Stack-Frame-Objekt. Diese Methode ist verantwortlich für die Behandlung von alle Details der Ausnahme. Wenn die [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) Schnittstelle ist nicht implementiert oder `InterceptStackException` Methode gibt alle Fehler zurück, und klicken Sie dann der Debugger führt die Verarbeitung der Ausnahme Normal.  
  
> [!NOTE]
>  Ausnahmen können, also nur in verwaltetem Code abgefangen werden, wenn die zu debuggende Programm wird unter .NET Runtime ausgeführt wird. Natürlich können Drittanbieter-sprachimplementierung implementieren `InterceptStackException` in ihre eigenen Debug-Engines, die bei Bedarf wechselseitig.  
  
 Nachdem das Abfangen abgeschlossen ist, wird ein [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) signalisiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

