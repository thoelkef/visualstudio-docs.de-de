---
title: 'Idiasymbol:: Get_hascastoperator | Microsoft-Dokumentation'
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
- IDiaSymbol::get_hasCastOperator method
ms.assetid: a21114a6-56a3-4e8a-a65f-58ec2a0a8908
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 977d95aa5f7d720efc672360b97239a5d8fe6261
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520873"
---
# <a name="idiasymbolgethascastoperator"></a>IDiaSymbol::get_hasCastOperator
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasymbol:: Get_hascastoperator](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-hascastoperator).  
  
Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp alle Umwandlungsoperatoren definiert hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_hasCastOperator (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt eine `TRUE` , wenn der benutzerdefinierte Datentyp alle Umwandlungsoperatoren definiert wurde, andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK V7. 0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



