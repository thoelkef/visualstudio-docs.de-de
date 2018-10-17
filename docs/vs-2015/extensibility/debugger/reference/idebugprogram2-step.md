---
title: IDebugProgram2::Step | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24946452e4ca1f595b076d61d165876c072e4537
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209676"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Führt einen Schritt aus.  
  
> [!NOTE]
>  Diese Methode ist veraltet. Verwenden der [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md) Methode stattdessen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread wird abgestuften darstellt.  
  
 `sk`  
 [in] Ein Wert aus der [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) -Enumeration, der den Typ des Schritts angibt.  
  
 `step`  
 [in] Ein Wert aus der [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) Enumeration, die die Einheit des Schritts (beispielsweise von einer Anweisung oder der Anweisung) angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Für den Fall, dass alle Threadsynchronisierung oder die Kommunikation zwischen Threads vorhanden ist, sollten andere Threads im Programm ausführen, wird ein Prozedurschritt ein bestimmter Thread ausgeführt.  
  
> [!WARNING]
>  Senden Sie eine Beenden-Ereignis oder ein sofort (synchron) Ereignis [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) bei der Verarbeitung dieser Aufruf ist; andernfalls der Debugger wird, reagiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

