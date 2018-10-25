---
title: 'Idiasymbol:: Get_registerid | Microsoft-Dokumentation'
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
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1ca9b0ba4cdf9a0a95522b4eef5793b9a42d152
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859693"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ab, der Register-Kennzeichner des Standorts bei der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) nastaven NA hodnotu `LocIsEnregistered`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Register-Kennzeichner des Speicherorts zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Symbol Bezug auf ein Register, d. h. wenn des Symbols [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) nastaven NA hodnotu `LocIsRegRel`, verwenden Sie die `get_registerId` Methode, gefolgt von einem Aufruf von der [idiasymbol:: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) Methode, die der Offset aus der Registrierung abgerufen werden, wo sich das Symbol befindet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)



