---
title: 'Idiasymbol:: Get_addresssection | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: af030d63c79901a41ea2704000de5b4d62e70e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
Ruft den Abschnitt Teil einer Adressspeicherort ab. Verwenden in folgenden Fällen die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) festgelegt ist, um `LocIsStatic`.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den Abschnitt Teil einer Adresse zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Hinweise  
 Bei statischen Elementen in einer externen DLL befindet sich möglicherweise im Abschnitt, der von dieser Methode zurückgegebene 0, wie diese Methode stützt sich auf die virtuelle Adresse des Elements abrufen. Virtuelle Adressen sind gültige nur, wenn die [idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) Methode in der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Schnittstelle mit Angabe der Adresse Laden der DLL Parameter ungleich NULL aufgerufen wurde.  
  
 Rufen Sie zum Abrufen der Zeitzonenoffset-Teils der Adresse der [idiasymbol:: Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK Version 7.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)