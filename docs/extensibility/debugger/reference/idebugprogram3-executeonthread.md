---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b75ee8c7b53e751f322ba41bc3f93e2542e192ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Führt das Programm Debugger. Der Thread wird zurückgegeben, um den Debuggerinformationen zu gewähren, in welchem, die Thread die Benutzer angezeigt wird, wenn das Programm ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es gibt drei Möglichkeiten, um ein Debugger die Ausführung nach dem Beenden fortgesetzt werden kann:  
  
-   Ausführen: Brechen Sie alle vorherigen Schritt und und so weiter bis zum nächsten Haltepunkt ausgeführt.  
  
-   Schritt: Brechen Sie alle alten Schritt und ausgeführt, bis der neue Schritt abgeschlossen ist.  
  
-   Weiterhin: Führen Sie erneut aus, und lassen Sie alle alten Schritt active.  
  
 Das an der Thread `ExecuteOnThread` ist nützlich, wenn Sie entscheiden, die Schritt auf "Abbrechen". Wenn Sie nicht wissen, dass der Thread ausgeführt ausführen bricht alle Schritte ab. Mit dem Wissen des Threads müssen Sie nur den Schritt auf dem aktiven Thread "Abbrechen".  
  
## <a name="see-also"></a>Siehe auch  
 [Führen Sie](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)