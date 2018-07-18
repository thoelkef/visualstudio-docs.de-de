---
title: IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4240a3ba82f3787c1e2e2da9f14c1cee5a8d177e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121104"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Diese Methode ruft ein Objekt, das Enumeration, der die Liste der persistenten Ports ermöglicht ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `PortNames`  
 [in] Ein [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) -Struktur, eine Liste der Anschlussnamen enthält zu suchen und zwischen der beibehaltenen Ports zurückzugeben. Nur die persistente Ports mit diesen Namen werden zurückgegeben.  
  
 `ppEnum`  
 [out] Ein Objekt, implementiert die [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Persistente Ports werden geladen, wenn ein Lieferant Port instanziiert und gespeichert, wenn der Lieferant Port zerstört wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)