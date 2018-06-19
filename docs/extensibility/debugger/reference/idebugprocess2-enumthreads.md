---
title: IDebugProcess2::EnumThreads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 786a3b4b5988b66e1fccc624154eeef67285ec84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116694"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Ruft eine Liste aller Threads im Prozess ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) -Objekt, das eine Liste aller Threads in alle Programme im Prozess enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode zählt die Threads in jedem Programm ausgeführt wird und Sie dann in eine Prozessansicht der Threads. Ein einzelner Thread möglicherweise in mehreren Programmen ausgeführt; Diese Methode listet dieser Thread nur einmal aus.  
  
 Diese Methode wird eine Liste von Prozessthreads ohne Duplikate. Zum Auflisten von Threads in einem bestimmten Programm ausgeführt wird, verwenden Sie andernfalls die [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)