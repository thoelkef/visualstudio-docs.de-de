---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cfa0e6b6755ea884b6dd9b6ba0409a614e80e290
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119203"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Ruft die am stärksten abgeleitete Verweis eines Verweises ab. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppDerivedMost`  
 [out] Gibt eine [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekt, das die am stärksten abgeleitete Eigenschaft darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Angenommen, wenn diese Eigenschaft ein Objekt beschreibt, die implementiert `ClassRoot` , aber diese ist tatsächlich eine Instanziierung von `ClassDerived` , stammt aus `ClassRoot`, gibt diese Methode ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt Ein Verweis auf die `ClassDerived` Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)