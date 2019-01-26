---
title: IDebugProcess2::GetPort | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetPort
helpviewer_keywords:
- IDebugProcess2::GetPort
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b41e434de676a60427b9c7267719cd2a61088d31
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934486"
---
# <a name="idebugprocess2getport"></a>IDebugProcess2::GetPort
Ruft ab, der Port, den der Prozess ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetPort(   
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppPort`  
 [out] Gibt eine [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Objekt, das den Port darstellt, auf dem der Prozess gestartet wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)