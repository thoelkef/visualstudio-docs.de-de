---
title: 'Idiasymmetribol:: get_addressSection | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 85e6ffac13f25e79f51af13ac134cf538e6af5af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840859"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Abschnitts Teil eines Adress Speicher Orts ab. Verwenden Sie, wenn die [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) auf festgelegt ist `LocIsStatic` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt den Abschnitts Teil eines Adress Speicher Orts zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Für statische Member, die sich in einer externen DLL befinden, kann der von dieser Methode zurückgegebene Abschnitt 0 sein, da diese Methode darauf basiert, dass die virtuelle Adresse des Members erhalten wird. Virtuelle Adressen sind nur gültig, wenn die [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) -Methode in der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Schnittstelle mit einem Parameter ungleich NULL aufgerufen wurde, der die Lade Adresse der DLL angibt.  
  
 Um den Offset Teil einer Adresse abzurufen, nennen Sie die [idiasymmetribol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) -Methode.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|BESCHREIBUNG|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|Dia SDK v 7.0|  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)
