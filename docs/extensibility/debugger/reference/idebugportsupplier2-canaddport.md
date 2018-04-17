---
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00b1c1303be8ccc326a58a20d132ad38db3b426d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Stellt sicher, dass ein Port Lieferant neue Ports hinzufügen kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt zurück, ob der Port hinzugefügt werden kann, `S_OK`ist, andernfalls gibt `S_FALSE` an, dass keine Ports können an diesem Port Lieferanten hinzugefügt werden.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie diese Methode vor dem Aufruf der [hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) Methode, da die zweite Methode erstellt wird, den Port sowie das Hinzufügen, die möglicherweise einen zeitaufwändigen Vorgang.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [Hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)