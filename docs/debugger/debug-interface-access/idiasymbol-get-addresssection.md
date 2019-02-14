---
title: 'Idiasymbol:: Get_addresssection | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adf7054b98b4f3ee821b552d4b247aae14d01b5a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969339"
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
Ruft den Teil "Abschnitt" einen Adressspeicherort ab. Verwenden, wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) nastaven NA hodnotu `LocIsStatic`.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den Teil "Abschnitt" einen Adressspeicherort zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Hinweise  
 Für statische Member in einer externen DLL befinden kann der Abschnitt, der von dieser Methode zurückgegebene 0 sein, wie diese Methode beruht auf die virtuelle Adresse des Elements. Virtuelle Adressen gültig sind nur dann, wenn die [idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) -Methode in der die [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Schnittstelle mit einem ungleich NULL-Parameter angeben der Adresse Laden der DLL aufgerufen wurde.  
  
 Um den Zeitzonenoffset-Teil einer Adresse zu erhalten, rufen die [idiasymbol:: Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|Dia2.h|  
|Version:|DIA-SDK V7. 0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)