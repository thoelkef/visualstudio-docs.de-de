---
title: 'Idiasymbol:: Get_registerid | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f6a4583206666f90adb90cbebebf9417e66fc78
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480848"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Ruft ab, die Register-Kennzeichner des Speicherorts bei der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) festgelegt ist, um `LocIsEnregistered`.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Register-Kennzeichner des Speicherorts zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Symbol relativ zum eines Registers, d. h. wenn des Symbols [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) auf festgelegt ist `LocIsRegRel`, verwenden Sie die `get_registerId` Methode gefolgt von einem Aufruf der [idiasymbol:: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) Methode, die der Offset aus dem Register abgerufen, in dem das Symbol befindet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)