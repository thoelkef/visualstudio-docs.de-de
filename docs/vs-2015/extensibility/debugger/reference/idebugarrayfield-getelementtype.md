---
title: IDebugArrayField::GetElementType | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ae24c2449d9bd26895647fc8f7b026291c4288
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142979"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Typ des Elements im Array ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppType`  
 [out] Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das den Typ des Elements beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) Objekt wird davon ausgegangen, dass alle Elemente des Arrays den gleichen Typ sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
