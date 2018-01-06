---
title: 'Idiasymbol:: Get_registerid | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c944869d48c484f7ddf234f4e00a5d10e96f70ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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