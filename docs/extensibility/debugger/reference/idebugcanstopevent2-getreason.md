---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
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
ms.openlocfilehash: 4c0eaefee714467084898182b338ceda63ebdc0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101988"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Ruft den Grund, warum die Debugging-Modul (DE) beenden möchte.  
  
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
 [out] Gibt einen Wert aus der [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) -Enumeration, der den Grund für dieses Ereignis beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird in der Regel aufgerufen, bevor die [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) Methode, sodass der Aufrufer nicht 0 (null) übergeben ermitteln, ob kann (`TRUE`), die `IDebugCanStopEvent2::CanStop` Methode.  
  
 Der Grund für Beendigung kann entweder `CANSTOP_ENTRYPOINT`, was bedeutet, dass die DE hat einen Einstiegspunkt erreicht oder `CANSTOP_STEPIN`, was bedeutet, dass die DE in eine Funktion in Einzelschritten hat.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)