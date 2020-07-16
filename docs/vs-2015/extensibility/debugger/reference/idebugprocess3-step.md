---
title: 'IDebugProcess3:: Step | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5069a40f4e3ea4b1fba74c8133a18b46f2b3f2d2
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386224"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bewirkt, dass der Prozess eine Anweisung oder eine Anweisung schrittweise durch nimmt.  
  
> [!NOTE]
> Diese Methode sollte anstelle von [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 in Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den abgestuften Thread darstellt.  
  
 `sk`  
 in Einer der [stepkind](../../../extensibility/debugger/reference/stepkind.md) -Werte.  
  
 `step`  
 in Einer der [stepunit](../../../extensibility/debugger/reference/stepunit.md) -Werte.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird der Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Thread Synchronisierung oder Kommunikation zwischen Threads vorhanden ist, sollten andere Threads im Prozess ausgeführt werden, wenn ein bestimmter Thread schrittweise ausgeführt wird.  
  
 **Warnung** Senden Sie während der Behandlung dieses Aufrufes kein anhalteereignis oder ein sofortiges (synchrones [) Ereignis.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls reagiert der Debugger möglicherweise nicht mehr.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Stepkind](../../../extensibility/debugger/reference/stepkind.md)   
 [Stepunit](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
