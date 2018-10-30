---
title: IDebugCanStopEvent2::GetReason | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d32f8be53d88b8268fdbbc82e6d774bffe3d7c3a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898413"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Ruft ab, der Grund, warum die Debug-Engine (DE) beenden möchte.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcr`  
 [out] Gibt einen Wert aus der [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) -Enumeration, die den Grund für dieses Ereignis beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird in der Regel aufgerufen, bevor die [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) Methode, sodass der Aufrufer entscheiden kann, ob ungleich NULL übergeben werden soll (`TRUE`) auf die `IDebugCanStopEvent2::CanStop` Methode.  
  
 Der Grund für beenden kann es sich entweder `CANSTOP_ENTRYPOINT`, was bedeutet, dass die DE ein Einstiegspunkts erreicht hat oder `CANSTOP_STEPIN`, was bedeutet, dass die DE in eine Funktion, abgestuft wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)