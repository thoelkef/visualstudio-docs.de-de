---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a57d2dc3274a1373f5cfa3641c4702b0a1429c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929600"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Um zu bestimmen, warum ein Auto-attach fehlgeschlagenen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszUrl`  
 [in] Derzeit nicht verwendet. sollte immer auf einen null-Wert festgelegt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Im folgenden finden andere typische Rückgabecodes:  
  
|Code|Beschreibung|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Kann nicht ermitteln, warum der Remoteserver zum Starten des Debuggings fehlgeschlagen ist.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Kann nicht auf Remoteserver, möglicherweise aufgrund unzureichender Berechtigungen debuggen, oder weil das DEBUG-Verb nicht aktiviert ist.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Der Webserver wurde gesperrt und blockiert das DEBUG-Verb, ist erforderlich, um Debuggen zu aktivieren.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)