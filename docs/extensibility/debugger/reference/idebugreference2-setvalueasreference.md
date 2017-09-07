---
title: IDebugReference2::SetValueAsReference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
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
ms.openlocfilehash: e295ad3fd09a8b5dbaa17cdd6f10f3cb8a9ff1b9
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Legt den Wert eines Verweises aus eines anderen Verweises. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rgpArgs`  
 [in] Ein Array von [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekte verwendet, um zu bestimmen, wie der Verweiswert festgelegt.  
  
 `dwArgCount`  
 [in] Die Anzahl der Verweise im Array.  
  
 `pValue`  
 [in] Ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt aus, das den Wert der Eigenschaft festgelegt.  
  
 `dwTimeout`  
 [in] Maximale Zeit in Millisekunden, bis vor der Rückgabe dieser Methode. Verwendung `INFINITE` zum unendlichen Warten angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
