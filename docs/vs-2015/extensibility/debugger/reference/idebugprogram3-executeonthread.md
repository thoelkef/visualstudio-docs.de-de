---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfc64f8ae928b4bb0057a16b8a74c6ddbff588c0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958410"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Führt das Debugger-Programm. Der Thread wird zurückgegeben, den Debuggerinformationen geben, in welchem, die Thread dem Benutzer angezeigt wird, wenn das Programm ausgeführt, wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es gibt drei Möglichkeiten, ein Debugger die Ausführung nach dem Beenden fortgesetzt werden kann:  
  
- Führen Sie aus: Kündigen Sie alle vorherigen Schritt aus, und führen Sie bis zum nächsten Haltepunkt und so weiter.  
  
- Schritt: Brechen Sie alle alten Schritt und ausgeführt, bis der neue Schritt abgeschlossen ist.  
  
- Fahren Sie fort: Führen Sie erneut aus, und lassen Sie alle alten Schritt aktiv.  
  
  Der Thread, die an `ExecuteOnThread` ist nützlich, bei der Entscheidung, wird der entsprechende Schritt abgebrochen. Bricht Sie alle Schritte ab, wenn Sie nicht wissen, dass den Thread ausgeführt wird ausgeführt. Mit Kenntnis des Threads müssen Sie nur den Schritt für den aktiven Thread abzubrechen.  
  
## <a name="see-also"></a>Siehe auch  
 [Führen Sie](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
