---
title: IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3a7bf8786f2ca066248ada3f1a0473b85681315
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986994"
---
# <a name="idiasymbolgetliverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Gibt den Zeitzonenoffset-Teil der Startadresse des Bereichs, in dem die lokalen Symbolcache gültig ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_liveRangeStartAddressOffset (   
   DWORD* offset  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `offset`  
 [out] Gibt den Zeitzonenoffset-Teil des Adressbereichs ab.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Ein Fehlercode bedeutet, dass das Symbol nicht live Bereichsinformationen verfügt.  
  
## <a name="remarks"></a>Hinweise  
 Die gebildet, indem Sie den Abschnitt und den Offset-Adresse ist der Anfang des Bereichs, in dem das Symbol gültig ist.  
  
 Verwenden Sie zum Abrufen des Teils "Abschnitt" die Adresse [IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)