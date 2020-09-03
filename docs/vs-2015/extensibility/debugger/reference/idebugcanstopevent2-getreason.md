---
title: 'IDebugCanStopEvent2:: geverrat | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 707488abed004adaa75c84f16358bdd8a979eb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191153"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Grund ab, warum die Debug-Engine (de) beendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 vorgenommen Gibt einen Wert aus der [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) -Enumeration zurück, die den Grund für dieses Ereignis beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird in der Regel vor der [canstoppt](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) -Methode aufgerufen, sodass der Aufrufer bestimmen kann, ob nicht NULL ( `TRUE` ) an die-Methode übergeben werden soll `IDebugCanStopEvent2::CanStop` .  
  
 Der Grund für das anhalten kann sein. das bedeutet, dass `CANSTOP_ENTRYPOINT` die de einen Einstiegspunkt erreicht hat, oder `CANSTOP_STEPIN` , was bedeutet, dass die de in eine Funktion eingetreten ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
