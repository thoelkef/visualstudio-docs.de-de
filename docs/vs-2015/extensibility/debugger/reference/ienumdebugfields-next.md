---
title: IEnumDebugFields::Next | Microsoft-Dokumentation
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
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 10406175a7254be0548678827afd41a4625e70c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516223"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IEnumDebugFields::Next](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugfields-next).  
  
Diese Methode gibt den nächsten Satz von Elementen aus der Enumeration.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Next(  
   ULONG         celt,  
   IDebugField** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint          celt,  
   IDebugField[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale Größe der `rgelt` Array.  
  
 `rgelt`  
 [in, out] Array von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Elementen gefüllt werden soll.  
  
 `pceltFetched`  
 [out] Gibt die Anzahl der im tatsächlich zurückgegebenen Elemente `rgelt`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden können; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

