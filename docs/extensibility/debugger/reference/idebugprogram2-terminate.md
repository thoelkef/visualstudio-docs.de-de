---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Terminate
helpviewer_keywords: IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fea9b99fc597a75e93392b14fe40a1be87072602
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Wird das Programm beendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn möglich, wird das Programm beendet und aus dem Prozess entladen werden; Andernfalls führt der Debugging-Modul (DE) alle erforderlichen Cleanup.  
  
 Diese Methode oder die [terminieren](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) Methode wird von der IDE, in der Regel als Reaktion auf den Benutzer Anhalten aller Debuggen aufgerufen. Die Implementierung dieser Methode sollte idealerweise die Anwendung innerhalb des Prozesses beendet. Wenn dies nicht möglich ist, sollten die DE verhindern, dass das Programm keine weiteren in diesem Prozess ausgeführt (und führen Sie alle erforderlichen cleanupmaßnahmen). Wenn die `IDebugProcess2::Terminate` Methode von der IDE aufgerufen wurde, wird der gesamte Prozess beendet, zu irgendeinem Zeitpunkt nach der `IDebugProgram2::Terminate` -Methode aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Beenden](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)