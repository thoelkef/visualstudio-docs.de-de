---
title: FuncDebugStart | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- FuncDebugStart symbol
- debugging [DIA SDK], start point
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89d240980746a0a6a606bd43ff67f86e454bfdc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="funcdebugstart"></a>FuncDebugStart
Eine Funktion besitzt einen definierten Punkt auf welche Debuggen begonnen werden soll, Punkt angegeben ist, durch ein Symbol mit einem `SymTagFuncDebugStart` Tag.  
  
## <a name="properties"></a>Eigenschaften  
 Die folgende Tabelle zeigt die Eigenschaften, die für diesen Symboltyp gültig sind.  
  
|Eigenschaft|Datentyp|Beschreibung|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Zeitzonenoffset-Teil des Speicherorts; Einzelheiten finden Sie in der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Abschnitt Teil Speicherort. Einzelheiten finden Sie in der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`Wenn die Funktion eine benutzerdefinierte Aufrufkonvention (nur in DIA-SDK 8.0 oder höher) verwendet.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`Wenn die Funktion eine weit zurück (nur in DIA-SDK 8.0 oder höher) führt.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`Wenn die Funktion eine Rückgabe von Interrupt (nur in DIA-SDK 8.0 oder höher) enthält.|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`Wenn die Funktion als statische (nur in DIA-SDK 8.0 oder höher) markiert ist.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die einschließende Funktion.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Die ID des übergeordneten lexikalischen Symbols.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Startpunkte haben statische Speicherorte; Weitere Informationen finden Sie unter [Orte für Symboldateien](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`Wenn die Funktion angegeben wurde, mit der [Noinline](/cpp/cpp/noinline) Attribut (nur in DIA-SDK 8.0 oder höher).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`Wenn die Funktion angegeben wurde, mit der [Noreturn](/cpp/cpp/noreturn) Attribut (nur in DIA-SDK 8.0 oder höher).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`Wenn die Funktion nie (nur in DIA-SDK 8.0 oder höher) aufgerufen wird.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset des Symbols im Arbeitsspeicher; Einzelheiten finden Sie in der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`Wenn der Code Debuginformationen für optimierten Code (nur in DIA-SDK 8.0 oder höher) hat.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relative Position in die Block-Funktion.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagFuncDebugStart` (eines der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Werte).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Die Position der Funktion in der ausführbaren Datei.|  
  
## <a name="see-also"></a>Siehe auch  
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)