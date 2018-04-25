---
title: 'Idiasymbol:: Get_addressoffset | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d00838fc3f76221293241656743bbf5a2a7f4d26
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetaddressoffset"></a>IDiaSymbol::get_addressOffset
Ruft den Zeitzonenoffset-Teil eines Speicherorts Adresse ab. Verwenden in folgenden Fällen die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) festgelegt ist, um `LocIsStatic`.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den Zeitzonenoffset-Teil eines Speicherorts Adresse zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Hinweise  
 Bei statischen Elementen in einer externen DLL befindet sich möglicherweise von dieser Methode zurückgegebene Offset 0, wie diese Methode stützt sich auf die virtuelle Adresse des Elements abrufen. Virtuelle Adressen sind gültige nur, wenn die [idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) Methode in der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Schnittstelle mit Angabe der Adresse Laden der DLL Parameter ungleich NULL aufgerufen wurde.  
  
 Um den Abschnitt Teil einer Adresse zu erhalten, rufen die [idiasymbol:: Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK Version 7.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [Idiasymbol:: Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)