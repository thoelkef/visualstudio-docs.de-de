---
title: FuncDebugEnd | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
- FuncDebugEnd symbol
- debugging [DIA SDK], end point
ms.assetid: 68f84fff-7cd3-4636-b929-7063a45009f8
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1033d79bc0639afe95bd72ccd9d679885fced169
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515794"
---
# <a name="funcdebugend"></a>FuncDebugEnd
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [FuncDebugEnd](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/funcdebugend).  
  
Wenn eine Funktion mit einer definierten Zeitpunkt verfügt werden dem Debuggen zu beenden, Debuggen Ausgangspunkt wird durch ein Symbol mit identifiziert eine `SymTagFuncDebugEnd` Tag.  
  
## <a name="properties"></a>Eigenschaften  
 Die folgende Tabelle zeigt die Eigenschaften, die für diesen Symboltyp gültig sind.  
  
|Eigenschaft|Datentyp|Beschreibung|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Zeitzonenoffset-Teil des Speicherorts; Weitere Informationen finden Sie unter den [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Abschnitt daran des Speicherorts. Weitere Informationen finden Sie unter den [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Wenn die Funktion eine benutzerdefinierte Aufrufkonvention (nur in DIA-SDK Version 8.0 oder höher) verwendet.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Wenn die Funktion eine weit zurück (nur in DIA-SDK Version 8.0 oder höher) führt.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Wenn die Funktion eine Rückgabe von Interrupt (nur in DIA-SDK Version 8.0 oder höher) enthält.|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` Wenn die Funktion statisch (nur in DIA-SDK Version 8.0 oder höher) ist.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die einschließende Funktion.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Die ID des lexikalischen übergeordneten Symbols.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Endpunkte haben statischen Speicherort; Weitere Informationen finden Sie unter [Orte für Symboldateien](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Wenn die Funktion angegeben wurde, mit der [Noinline](http://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) Attribut (nur in DIA-SDK Version 8.0 oder höher).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Wenn die Funktion angegeben wurde, mit der [Noreturn](http://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) Attribut (nur in DIA-SDK Version 8.0 oder höher).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Wenn die Funktion nie (nur in DIA-SDK Version 8.0 oder höher) aufgerufen wird.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset des Symbols im Speicher; Weitere Informationen finden Sie unter den [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Wenn die Funktion Debuginformationen für optimierten Code (nur in DIA-SDK Version 8.0 oder höher).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relative Position des Endes dieser Funktion innerhalb der Moduls.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagFuncDebugEnd` (eines der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Werte).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Die Position dieser Funktion im Image ausführbaren Datei.|  
  
## <a name="see-also"></a>Siehe auch  
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)



