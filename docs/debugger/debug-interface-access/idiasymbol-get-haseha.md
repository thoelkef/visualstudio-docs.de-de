---
title: 'Idiasymbol:: Get_haseha | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEHa method
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca6cc1306fec11033b1430adbb6bd13093d48061
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926814"
---
# <a name="idiasymbolgethaseha"></a>IDiaSymbol::get_hasEHa
Ruft ein Flag, das angibt, ob die Funktion asynchrone (strukturierte) Ausnahmebehandlung enthält.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_hasEHa(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 [out] Gibt `TRUE` , wenn die Funktion asynchrone Ausnahmebehandlung; hat, andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Anmerkungen  
 Es ist möglich, asynchrone oder strukturierte Ausnahmebehandlung mit C++-Stil für die Ausnahmebehandlung zu kombinieren, aber es erfordert, dass eine bestimmte Compilerschalter/EHa, um ihn zu aktivieren.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)