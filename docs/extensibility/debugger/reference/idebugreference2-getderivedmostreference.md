---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 9c52e0deb9303790a10091bf645646546aef546d
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

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
