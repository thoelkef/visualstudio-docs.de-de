---
title: 'IDebugEngineProgram2:: stoppt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb74cb2940a91bbc64fa4a06f28d07a828357fc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431484"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beendet alle Threads, die in diesem Programm ausgeführt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird aufgerufen, wenn dieses Programm in einer Umgebung mit mehreren Programmen deentschlgt wird. Wenn ein anhalteereignis von einem anderen Programm empfangen wird, wird diese Methode für dieses Programm aufgerufen. Die Implementierung dieser Methode muss asynchron sein. Das heißt, dass nicht alle Threads beendet werden müssen, bevor diese Methode zurückgegeben wird. Die Implementierung dieser Methode kann so einfach wie das Aufrufen der [causetbreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) -Methode für dieses Programm sein.  
  
 Ein Debug-Ereignis wird nicht als Antwort auf diese Methode gesendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
