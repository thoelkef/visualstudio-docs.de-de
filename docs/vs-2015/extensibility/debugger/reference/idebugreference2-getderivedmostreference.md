---
title: IDebugReference2::GetDerivedMostReference | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6baff17ba485b45a239d2acb0af2b765844fa35c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914007"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den am stärksten abgeleitete-Verweis, der einen Verweis ab. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Z. B., wenn diese Eigenschaft auf ein Objekt beschreibt, die implementiert `ClassRoot` , aber dies ist tatsächlich eine Instanziierung von `ClassDerived` abgeleitete `ClassRoot`, gibt diese Methode eine [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt Ein Verweis auf die `ClassDerived` Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

