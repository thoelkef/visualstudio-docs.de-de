---
title: IDebugReference2::Compare | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ce8420c3ed2703a32e7422e9bee6b4e1815c134
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869880"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Vergleicht einen Verweis auf einen anderen. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```csharp  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCompare`  
 [in] Ein Wert aus der [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) -Enumeration, die Vergleichsoperation, z. B. größer oder gleich, kleiner als angibt.  
  
 `pReference`  
 [in] Ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt, das den Verweis auf die zu vergleichenden darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)