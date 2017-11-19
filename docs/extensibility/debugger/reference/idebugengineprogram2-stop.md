---
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::Stop
helpviewer_keywords: IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21dd14e1cc4d4e8c6b65b5285763a680a5f327f7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Beendet alle Threads, die an diesem Programm ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, wenn dieses Programm in einer Umgebung mit mehreren Anwendung gedebuggt wird. Wenn eine Stopping-Ereignis von einem anderen Programm empfangen wird, wird diese Methode auf dieses Programm aufgerufen. Die Implementierung dieser Methode sollte asynchron sein; nicht alle Threads sollte also erforderlich beendet werden soll, bevor diese Methode zurückgibt. Die Implementierung dieser Methode ist möglicherweise so einfach wie das Aufrufen der [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) -Methode für dieses Programm.  
  
 Keine Debug-Ereignis wird als Antwort auf diese Methode gesendet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)