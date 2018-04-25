---
title: IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 471c9ecfb7ee1aa318e2db9c1c7de0cd56a1184f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetliverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Gibt den Offset Teil die Startadresse des Bereichs, in dem die lokalen Symbolcache gültig ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_liveRangeStartAddressOffset (   
   DWORD* offset  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `offset`  
 [out] Gibt den Zeitzonenoffset-Teil des Start-Adressbereichs an.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Ein zurückgegebene Fehlercode bedeutet, dass das Symbol keinen live Bereichsinformationen.  
  
## <a name="remarks"></a>Hinweise  
 Die Adresse formed by the Abschnitt und Offset ist der Anfang des Bereichs, in dem das Symbol gültig ist.  
  
 Verwenden Sie zum Abrufen der Abschnitt Teil der Adresse [IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)