---
title: IDebugTypeFieldBuilder2::CreateArrayOfType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 006e8d7164da54c6fbba866eb9b0dd3c5f854262
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865647"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
Erstellt ein Array des angegebenen Typs und der Größe.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateArrayOfType (  
   IDebugField*  pTypeField,  
   DWORD         rank,  
   IDebugField** pArrayOfTypeField  
);  
```  
  
```csharp  
int CreateArrayOfType (  
   IDebugField     pTypeField,  
   uint            rank,  
   out IDebugField pArrayOfTypeField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pTypeField`  
 [in] Typ der Elemente, die das Array aufnehmen wird.  
  
 `rank`  
 [in] Anzahl der Elemente im Array.  
  
 `pArrayOfTypeField`  
 [out] Gibt die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekte, die das neue Array darstellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)