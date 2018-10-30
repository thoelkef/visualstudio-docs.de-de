---
title: 'Idiasymbol:: Get_virtual | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSymbol::get_virtual method
ms.assetid: 97e3ad51-8ef3-4446-ab33-3cb34a21b7a0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0f71a9fdfaf5d46194670b4c615b4c0d9e1f630
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906207"
---
# <a name="idiasymbolgetvirtual"></a>IDiaSymbol::get_virtual
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag, das angibt, ob die Funktion virtuell ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_virtual (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` gibt zurück, wenn die Funktion, andernfalls virtuellen ist, `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



