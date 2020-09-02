---
title: Symbol Speicherorte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1f9ea0c6f2eede11100a4956ef4c63b20c6fa9a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193563"
---
# <a name="symbol-locations"></a>Symbolspeicherorte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die meisten Symbole haben einen definierten Speicherort innerhalb der Bilddatei. Der Speicherort eines Symbols wird mit einem Wert aus der [LocationType](../../debugger/debug-interface-access/locationtype.md) -enumerationsenumeration angegeben. Abhängig von ihrem Speicherort unterstützt das Symbol möglicherweise zusätzliche Eigenschaften.  
  
 In der folgenden Tabelle werden die am häufigsten verwendeten Speicherort Typen und die zugehörigen zusätzlichen Eigenschaften angezeigt.  
  
|Ortstyp|Zusätzliche Eigenschaften|  
|-------------------|---------------------------|  
|`LocIsNull`|Keine|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [Idiasymmetribol:: get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (wenn relative virtuelle Adressen aktiviert sind)<br /><br /> [Idiasymmetribol:: get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (wenn die Bildbasis auf einen Wert ungleich NULL festgelegt wurde)|  
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|  
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idiasymmetribol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [Idiasymmetribol:: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Idiasymmetribol:: get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [Idiasymmetribol:: get_Length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [Idiasymmetribol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Idiasymmetribol:: get_Offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [Idiasymmetribol:: get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [Idiasymmetribol:: get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [Idiasymmetribol:: get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [Idiasymmetribol:: get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [Idiasymmetribol:: get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [Idiasymmetribol:: get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
