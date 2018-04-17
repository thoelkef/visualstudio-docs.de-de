---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4ee07f9118565177e513647d28ebcb11a23de3a6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Diese Methode bestimmt, ob der Port Lieferant Ports beibehalten werden kann (indem sie auf den Datenträger geschrieben wird) zwischen den Aufrufen des Debuggers.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 `S_OK` Wenn Ports beibehalten werden können, oder `S_FALSE` , um anzugeben, dass die Ports nicht dauerhaft gespeichert werden können.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Lieferant Port Ports beibehalten werden kann, sollte er dies tun, wenn es zerstört wird und Laden sie dann erneut, wenn es noch einmal instanziiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)