---
title: IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01bd3d099bc714aa20a9066c414b4222d3894f5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetliverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Gibt den Teil "Abschnitt" die Startadresse des Bereichs, in dem die lokalen Symbolcache gültig ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `section`  
 [out] Gibt den Abschnitt Teil der ab-Adressbereich an.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Ein zurückgegebene Fehlercode bedeutet, dass das Symbol keinen live Bereichsinformationen.  
  
## <a name="remarks"></a>Hinweise  
 Die Adresse formed by the Abschnitt und Offset ist der Anfang des Bereichs, in dem das Symbol gültig ist.  
  
 Verwenden Sie zum Abrufen der Zeitzonenoffset-Teils der Adresse [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)