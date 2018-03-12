---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7c5fe4c0ab03e6f0683fff3d43658fde5bc90bf0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Benachrichtigt die Debugging-Modul (DE) ob an der aktuellen Codeposition beenden oder Fortsetzen der Ausführung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [in] Ungleich 0 (`TRUE`) Wenn DE an der aktuellen Position des Codes; beendet werden soll, andernfalls 0 (null) (`FALSE`).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ruft der Empfänger der dieses Ereignis in der Regel die [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) -Methode, um die Ursache zu ermitteln, die DE beenden möchte, und ruft dann die `IDebugCanStopEvent2::CanStop` -Methode durch die entsprechende Antwort.  
  
 Wenn die DE beendet wird, sendet er ein Ereignis, das den Grund für Beendigung beschreibt. In der Regel werden zwei Ereignisse, die eine Benutzer- oder Signal-Unterbrechung dargestellte gesendet, werden die [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) -Schnittstelle, und ein Haltepunktereignis dargestellte der [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)