---
title: Speicherorte für | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 021911c01a7cd98e157f6c216ae28feffcaf7096
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="symbol-locations"></a>Symbolspeicherorte
Die meisten Symbole haben eine definierte Position innerhalb der Bilddatei. Speicherort des Symbols wird angegeben, mit einem Wert aus der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) Enumeration. Das Symbol unterstützen möglicherweise weitere Eigenschaften abhängig von ihrem Speicherort.  
  
 Die folgende Tabelle zeigt die am häufigsten Typen und deren zusätzlichen Eigenschaften verwendeten.  
  
|Speicherorttyp|Zusätzliche Eigenschaften|  
|-------------------|---------------------------|  
|`LocIsNull`|Keine|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [Idiasymbol:: Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (wenn es sich um eine relative virtuelle Adressen sind aktiviert sind)<br /><br /> [Idiasymbol:: Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (wenn die Abbildbasis zu ungleich NULL festgelegt wurde)|  
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|  
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Idiasymbol:: Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [Idiasymbol:: Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Idiasymbol:: Get_bitposition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [Idiasymbol:: Get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [Idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Idiasymbol:: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [Idiasymbol:: Get_registerid](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [Idiasymbol:: Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [Idiasymbol:: Get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [Idiasymbol:: Get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [Idiasymbol:: Get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [Idiasymbol:: Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)