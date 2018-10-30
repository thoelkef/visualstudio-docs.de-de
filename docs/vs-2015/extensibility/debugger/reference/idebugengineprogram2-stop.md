---
title: IDebugEngineProgram2::Stop | Microsoft-Dokumentation
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
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b833dcab12fe4533e781154b90b8aceab7588c62
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916633"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beendet alle Threads, die in diesem Programm ausgeführt wird.  
  
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
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, wenn dieses Programm in einer Umgebung mit mehreren Anwendung gedebuggt wird. Wenn eine Beenden-Ereignis in ein anderes Programm empfangen wird, wird diese Methode für dieses Programm aufgerufen. Die Implementierung dieser Methode sollten asynchron sein; nicht alle Threads sollte, also erforderlich, um vor dem Beenden dieser Methode beendet werden. Die Implementierung dieser Methode ist möglicherweise so einfach wie das Aufrufen der [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) Methode für dieses Programm.  
  
 Kein Debugereignis wird als Reaktion auf diese Methode gesendet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)

