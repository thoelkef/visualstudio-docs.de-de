---
title: IDebugProperty2::GetDerivedMostProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4e9efd498485340b49dbd385a6a94fa6cf7fcedd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Ruft die am stärksten abgeleitete-Eigenschaft einer Eigenschaft ab.  
  
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
 Im Erfolgsfall gibt `S_OK`; andernfalls wird Fehlercode zurückgegeben. Gibt `S_GETDERIVEDMOST_NO_DERIVED_MOST` Wenn keine am stärksten abgeleitete Eigenschaft ist abgerufen.  
  
## <a name="remarks"></a>Hinweise  
 Angenommen, wenn diese Eigenschaft ein Objekt beschreibt, die implementiert `ClassRoot` , aber diese ist tatsächlich eine Instanziierung von `ClassDerived` , stammt aus `ClassRoot`, gibt diese Methode ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt Beschreibt die `ClassDerived` Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)