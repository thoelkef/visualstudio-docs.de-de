---
title: IDebugProperty2::GetDerivedMostProperty | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 58713b63728678ccab55435eb05b1cbb1c8920fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929880"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Ruft den am stärksten abgeleitete Eigenschaft einer Eigenschaft ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppDerivedMost`  
 [out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das die am stärksten abgeleitete Eigenschaft darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück. Gibt `S_GETDERIVEDMOST_NO_DERIVED_MOST` Wenn keine Eigenschaft "am stärksten abgeleitete ist" abgerufen.  
  
## <a name="remarks"></a>Hinweise  
 Z. B., wenn diese Eigenschaft auf ein Objekt beschreibt, die implementiert `ClassRoot` , aber dies ist tatsächlich eine Instanziierung von `ClassDerived` abgeleitete `ClassRoot`, gibt diese Methode eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt Beschreibt die `ClassDerived` Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)