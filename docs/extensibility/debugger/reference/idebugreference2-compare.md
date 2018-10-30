---
title: IDebugReference2::Compare | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: b00eb4e64e9dcccf4519f5e799f238ad01773b8a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860486"
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