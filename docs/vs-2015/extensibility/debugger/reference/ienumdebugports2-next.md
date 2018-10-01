---
title: IEnumDebugPorts2::Next | Microsoft-Dokumentation
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
- IEnumDebugPorts2::Next
helpviewer_keywords:
- IEnumDebugPorts2::Next
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11d9830666621cd8c3280fbf64cc8379c13b8de9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509249"
---
# <a name="ienumdebugports2next"></a>IEnumDebugPorts2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IEnumDebugPorts2::Next](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugports2-next).  
  
Gibt den nächsten Satz von Elementen aus der Enumeration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Next(  
   ULONG         celt,  
   IDebugPort2** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint          celt,  
   IDebugPort2[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale Größe der `rgelt` Array.  
  
 `rgelt`  
 [in, out] Array von [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Elementen gefüllt werden soll.  
  
 `pceltFetched`  
 [out] Gibt die Anzahl der im tatsächlich zurückgegebenen Elemente `rgelt`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden können; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

