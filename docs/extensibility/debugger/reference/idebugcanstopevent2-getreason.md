---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b5d4c50b407406ea9a5d878decf859b8ab70863d
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

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
