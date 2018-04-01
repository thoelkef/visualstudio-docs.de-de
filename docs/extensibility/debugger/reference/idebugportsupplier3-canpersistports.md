---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7cb364ca40c42a3f392a5944169b7dd97075ab9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
 `S_OK`Wenn Ports beibehalten werden können, oder `S_FALSE` , um anzugeben, dass die Ports nicht dauerhaft gespeichert werden können.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Lieferant Port Ports beibehalten werden kann, sollte er dies tun, wenn es zerstört wird und Laden sie dann erneut, wenn es noch einmal instanziiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)