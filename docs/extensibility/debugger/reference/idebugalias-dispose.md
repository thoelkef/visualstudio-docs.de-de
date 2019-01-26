---
title: IDebugAlias::Dispose | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5dffc8e9bb5440fb1a05cd733c609af43104f72
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028412"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Markiert diesen Alias entfernt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Dispose();  
```  
  
```csharp  
int Dispose();  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Sobald diese Methode aufgerufen wird, ist der Alias nicht mehr verfügbar.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)