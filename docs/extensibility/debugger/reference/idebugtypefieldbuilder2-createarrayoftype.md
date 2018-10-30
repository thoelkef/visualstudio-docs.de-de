---
title: IDebugTypeFieldBuilder2::CreateArrayOfType | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 3171fedfe263aa4e2624e4425d3bc6929dd3c2fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950445"
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