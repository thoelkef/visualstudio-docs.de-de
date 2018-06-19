---
title: IEnumDebugModules2::Clone | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugModules2::Clone
helpviewer_keywords:
- IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7a42eeb056ba141f2cedb551f43ea4dacb0a9032
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123500"
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
Gibt eine Kopie der aktuellen Enumeration als separates Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Clone(  
   IEnumDebugModules2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine Kopie dieser Enumeration als separates Objekt zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Kopie der Enumeration enthält denselben Status an wie die ursprüngliche, zu dem Zeitpunkt, die diese Methode aufgerufen wird. Allerdings wird der Kopie und den ursprünglichen Zustand getrennt sind und können einzeln geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)