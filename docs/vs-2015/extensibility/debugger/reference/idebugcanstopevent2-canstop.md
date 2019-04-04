---
title: IDebugCanStopEvent2::CanStop | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8167013489b3b37e254100f7547cd61d54529b95
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960088"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Benachrichtigt der Debug-Engine (DE), ob an der aktuellen Codeposition zu beenden oder Fortsetzen der Ausführung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fCanStop`  
 [in] Ungleich 0 (`TRUE`), wenn die DE werden, an der aktuellen Position des Codes beendet soll; andernfalls NULL (`FALSE`).  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ruft der Empfänger der dieses Ereignis in der Regel die [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) Methode, um die Ursache zu ermitteln, die DE beenden möchte, und ruft dann die `IDebugCanStopEvent2::CanStop` Methode mit der entsprechenden Antwort.  
  
 Wenn die DE beendet wird, sendet er ein Ereignis, das den Grund für Beenden beschreibt. In der Regel werden zwei Ereignisse, die einen Benutzer oder ein Signal Umbruch, der durch dargestellt wird gesendet, werden die [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) -Schnittstelle, und ein Haltepunktereignis, dargestellt durch die [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
