---
title: IDebugProcess3::Continue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f666f35a71f65b839073e7d360bc357627fb7c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Wird fortgesetzt, das Ausführen dieses Prozesses vom Zustand "beendet". Alle vorherigen Ausführungsstatus (z. B. einem Schritt) wird beibehalten, und der Prozess gestartet wird, erneut ausführen.  
  
> [!NOTE]
>  Diese Methode sollte verwendet werden, anstelle von [Fortfahren](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Objekt, das den Thread fortgesetzt werden darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, auf diesem Prozess unabhängig davon, wie viele Prozesse gedebuggt werden oder welcher Prozess das Stopping-Ereignis generiert. Die Implementierung muss den vorherigen Ausführungsstatus (z. B. einem Schritt) beibehalten und Ausführung wird fortgesetzt, als wäre er nie beendet wurde, vor dem Abschluss der vorherigen Ausführung. Das heißt, wenn ein Thread in dieser Prozess wurde einen Schritt-Over-Vorgang ausführen und wurde beendet, weil ein anderer Prozess beendet, und klicken Sie dann `Continue` aufgerufen wurde, den angegebenen Thread muss der ursprünglichen Schritt mit Failover-Vorgang abgeschlossen.  
  
 **Warnung** keine Stopping-Ereignis oder ein sofort (synchron) Ereignis senden [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) während der Bearbeitung dieser Aufruf; andernfalls der Debugger reagiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)