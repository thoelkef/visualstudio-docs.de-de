---
title: IEnumDebugModules2::Skip | Microsoft-Dokumentation
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
- IEnumDebugModules2::Skip
helpviewer_keywords:
- IEnumDebugModules2::Skip
ms.assetid: 61dc42f4-8544-45bb-8da0-fb22cccec7da
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a14b7dcd0038fb358326f3f1d35c203987a0c8ae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515393"
---
# <a name="ienumdebugmodules2skip"></a>IEnumDebugModules2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IEnumDebugModules2::Skip](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugmodules2-skip).  
  
Überspringt die angegebene Anzahl von Elementen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der zu überspringenden Elemente.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn `celt` größer als die Anzahl der verbleibenden Elemente ist; andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn `celt` gibt einen Wert größer als die Anzahl der verbleibenden Elemente am Ende die Enumeration festgelegt ist und `S_FALSE` zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

