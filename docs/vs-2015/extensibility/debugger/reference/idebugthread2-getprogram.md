---
title: IDebugThread2::GetProgram | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::GetProgram
helpviewer_keywords:
- IDebugThread2::GetProgram
ms.assetid: 8c9c5ea1-2031-472e-bc8f-30e22e754566
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a78f831f5df6506b0aa607a6378f8e37caa8e5ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946182"
---
# <a name="idebugthread2getprogram"></a>IDebugThread2::GetProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft ab, das Programm, in dem ein Thread ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetProgram (   
   IDebugProgram2** ppProgram  
);  
```  
  
```csharp  
int GetProgram (   
   out IDebugProgram2 ppProgram  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppProgram`  
 [out] Gibt eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das Programm darstellt, in diesem Thread ausgeführt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
