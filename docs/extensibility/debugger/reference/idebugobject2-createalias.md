---
title: IDebugObject2::CreateAlias | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a06a0e9addaf30c12472698648f442f3de3f6d9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004447"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Erstellt eine eindeutige ID oder den Alias für dieses Objekt aus, oder gibt einen vorhandenen Alias.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int CreateAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppAlias`  
 [out] Der Alias (oder vorhanden).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Alias ist eine Bezeichnung, die ein bestimmtes Objekt darstellt, während das Objekt im Arbeitsspeicher befindet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)