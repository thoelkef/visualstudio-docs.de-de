---
title: Bezeichnung (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- locations, in program code
- Label symbol
ms.assetid: 8cef7620-5bc8-4500-8bd0-e9e638bccb24
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f7d1721f8f48b8bcaaaba4c32a5ad323941d59c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682724"
---
# <a name="label-debug-interface-access-sdk"></a>Label (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Speicherort im Programmcode wird durch ein `SymTagLabel` Symbol gekennzeichnet.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die für diesen Symboltyp gültig sind.  
  
|Eigenschaft|Datentyp|BESCHREIBUNG|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Offset Teil des Standorts; Weitere Informationen finden Sie unter der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Teil des Standorts; Weitere Informationen finden Sie unter der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` , wenn die Bezeichnung eine benutzerdefinierte Aufruf Konvention verwendet.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` , wenn die Bezeichnung eine lange Rückgabe ausführt.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` , wenn die Bezeichnung eine Rückgabe von Interrupt enthält.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für das einschließende compilerblock, den Block oder die Funktion.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des übergeordneten lexikalischen Symbols.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Bezeichnungen verfügen über statische Speicherorte. Weitere Informationen finden Sie unter der-Enumeration für [Symbol Orte](../../debugger/debug-interface-access/symbol-locations.md) .|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Der Name der Bezeichnung.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` , wenn die Bezeichnung mit dem [noinline](https://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) -Attribut angegeben wurde.|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` , wenn die Bezeichnung mit dem [noreturn](https://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) -Attribut angegeben wurde.|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` , wenn die Bezeichnung nie aufgerufen wird.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset des Symbols im Speicher; Weitere Informationen finden Sie unter der [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` .|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` , wenn der Code über Debuginformationen für optimierten Code verfügt.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relative Position dieser Bezeichnung in Ihrem Modul.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagFuncDebugLabel` (einen der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswerte) zurück.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Die Position dieser Bezeichnung innerhalb des ausführbaren Bilds.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lexikalische Hierarchie von Symbol Typen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType-Enumeration](../../debugger/debug-interface-access/locationtype.md)   
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)
