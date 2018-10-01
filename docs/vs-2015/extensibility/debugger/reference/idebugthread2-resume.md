---
title: IDebugThread2::Resume | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a3591ff3363a267b65c41093b18ff8d3ed154d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516344"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugThread2::Resume](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugthread2-resume).  
  
Setzt die Ausführung eines Threads.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwSuspendCount`  
 [out] Gibt den Unterbrechungszähler nach der Wiederaufnahme des Vorgangs zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jeder Aufruf von verringert diese Methode den Unterbrechungszähler bis zu diesem Zeitpunkt 0 erreicht, wird tatsächlich Ausführung fortgesetzt. Diese Unterbrechungszähler wird angezeigt, der **Threads** Debug-Fenster.  
  
 Bei jedem Aufruf dieser Methode, muss ein vorherigen Aufruf der [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) Methode. Der Unterbrechungszähler bestimmt, wie oft die `IDebugThread2::Suspend` bisher Methode aufgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)

