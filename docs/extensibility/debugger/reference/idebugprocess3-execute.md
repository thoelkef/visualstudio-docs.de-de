---
title: IDebugProcess3::Execute | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 95dc4728c3c51dc8e206393ccb2a8f27f470a51b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Wird fortgesetzt, das Ausführen dieses Prozesses vom Zustand "beendet". Alle vorherigen Ausführungsstatus (z. B. einem Schritt) deaktiviert ist, und der Prozess gestartet wird, erneut ausführen.  
  
> [!NOTE]
>  Diese Methode sollte verwendet werden, anstelle von [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Objekt, das Ausführen des Threads darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Benutzer die Ausführung von Status "beendet" in einem anderen Prozess Thread startet, wird diese Methode auf diesem Prozess aufgerufen. Diese Methode wird auch aufgerufen, wenn der Benutzer wählt die **starten** Befehl die **Debuggen** Menü in der IDE. Die Implementierung dieser Methode ist möglicherweise so einfach wie das Aufrufen der [fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md) Methode für den aktuellen Thread im Prozess.  
  
> [!WARNING]
>  Keine Stopping-Ereignis oder ein sofort (synchron) Ereignis senden [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) während der Bearbeitung dieser Aufruf; andernfalls der Debugger reagiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)