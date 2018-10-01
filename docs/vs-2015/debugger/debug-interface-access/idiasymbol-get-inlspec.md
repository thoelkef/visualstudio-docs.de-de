---
title: 'Idiasymbol:: Get_inlspec | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc76fb517c6cc75c6117d8dc7cd95bd377b34f87
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520516"
---
# <a name="idiasymbolgetinlspec"></a>IDiaSymbol::get_InlSpec
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasymbol:: Get_inlspec](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-inlspec).  
  
Diese Funktion ruft ein Flag, der angibt, ob die Funktion als Inline gekennzeichnet war (mit einer der der [Inline __inline, \__forceinline](../../misc/inline-inline-forceinline.md) Attribute).  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_inlSpec(  
   BOOL *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` , wenn die Funktion als Inline gekennzeichnet wurde, andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [inline, __inline, \__forceinline](../../misc/inline-inline-forceinline.md)



