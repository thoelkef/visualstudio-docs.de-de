---
title: IEnumDebugFields::Clone | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9c3243c7e5f2cb0378772987917455c3a6d0a8c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928463"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
Diese Methode gibt eine Kopie der aktuellen Enumeration als separates Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Clone(  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine Kopie dieser Enumeration als ein separates Objekt zurück.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Kopie der Enumeration hat den gleichen Zustand wie die ursprüngliche, zu dem Zeitpunkt, die diese Methode aufgerufen wird. Allerdings wird der Kopiervorgangs des und den ursprünglichen Zustand sind getrennt und einzeln geändert werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)