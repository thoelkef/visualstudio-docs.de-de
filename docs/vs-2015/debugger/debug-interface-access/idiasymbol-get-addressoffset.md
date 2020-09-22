---
title: 'Idiasymmetribol:: get_addressOffset | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dfa54e09baa3cec238eb892599a8e1bd5910e17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840888"
---
# <a name="idiasymbolget_addressoffset"></a>IDiaSymbol::get_addressOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Offset Teil eines Adress Speicher Orts ab. Verwenden Sie, wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) auf festgelegt ist `LocIsStatic` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt den Offset Teil eines Adress Speicher Orts zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei statischen Membern, die sich in einer externen DLL befinden, kann der Offset, der von dieser Methode zurückgegeben wird, 0 sein, da diese Methode das Abrufen der virtuellen Adresse des Members erfordert. Virtuelle Adressen sind nur gültig, wenn die [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) -Methode in der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Schnittstelle mit einem Parameter ungleich NULL aufgerufen wurde, der die Lade Adresse der DLL angibt.  
  
 Um den Abschnitts Teil einer Adresse abzurufen, nennen Sie die [idiasymmetribol:: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) -Methode.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|BESCHREIBUNG|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|Dia SDK v 7.0|  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [Idiasymmetribol:: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
