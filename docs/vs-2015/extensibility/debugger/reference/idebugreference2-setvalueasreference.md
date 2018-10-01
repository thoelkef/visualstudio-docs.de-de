---
title: IDebugReference2::SetValueAsReference | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 04a1534064acff7b392c6235c16f1ccf7a38f03e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520631"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugReference2::SetValueAsReference](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugreference2-setvalueasreference).  
  
Legt den Wert eines Verweises von einem anderen Verweis. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp#  
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
 [in] Ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt aus, das den Eigenschaftswert festzulegen.  
  
 `dwTimeout`  
 [in] Maximale Zeit in Millisekunden, die vor der Rückgabe dieser Methode gewartet. Verwendung `INFINITE` für Warten ohne Timeout.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

