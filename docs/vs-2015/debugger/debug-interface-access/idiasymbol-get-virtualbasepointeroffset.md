---
title: 'Idiasymbol:: Get_virtualbasepointeroffset | Microsoft-Dokumentation'
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
- IDiaSymbol::get_virtualBasePointerOffset method
ms.assetid: a4f2649c-6702-491c-90a1-d6d669258c51
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc9833219abc29fb50fd113e86e85af33eb39c3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524885"
---
# <a name="idiasymbolgetvirtualbasepointeroffset"></a>IDiaSymbol::get_virtualBasePointerOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasymbol:: Get_virtualbasepointeroffset](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset).  
  
Ruft den Offset von der virtuellen basiszeiger ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_virtualBasePointerOffset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den Offset der virtuellen basiszeiger zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



