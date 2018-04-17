---
title: IDebugProgram2::CauseBreak | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 81fb04db3342bb8ce7d5e314c9a912b873ffb627
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Fordert an, dass das Programm zu die Ausführung der nächsten beenden Zeitpunkt eins seiner Threads Versuche ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) Ereignis gesendet wird, wenn das Programm weiter versucht, um Code auszuführen, nachdem diese Methode aufgerufen wird.  
  
 Diese Methode ist asynchron, darin, dass die Methode sofort zurückgegeben, ohne zu warten, unbedingt zum Beenden des Programms.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)