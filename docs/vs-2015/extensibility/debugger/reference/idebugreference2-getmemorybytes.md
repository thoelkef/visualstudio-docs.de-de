---
title: IDebugReference2::GetMemoryBytes | Microsoft-Dokumentation
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
- IDebugReference2::GetMemoryBytes
helpviewer_keywords:
- IDebugReference2::GetMemoryBytes
ms.assetid: 2006cb2b-1dfa-4a2d-8e3e-db2ce0302e0d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 508d627066f34c0561160e334240f5e91e464606
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851204"
---
# <a name="idebugreference2getmemorybytes"></a>IDebugReference2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft ab, die Arbeitsspeicher-Bytes, die physisch auf den Wert eines Verweises enthalten. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppMemoryBytes`  
 [out] Gibt eine [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) -Objekt, das verwendet werden kann, um den Arbeitsspeicher abzurufen, die den Wert des Verweises enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)

