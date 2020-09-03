---
title: Kompilieren | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiland symbol
- compilands, compiland symbol
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 579ac6a70b379364870425e78cee41ac0840a214
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163999"
---
# <a name="compiland"></a>Compiland
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es gibt ein `SymTagCompiland` Symbol für jede Kompilierungen, die mit der exe-Datei verknüpft ist. Compiland-Informationen werden zwischen Symbolen mit einem- `SymTagCompiland` Tag aufgeteilt, das abgerufen werden kann, ohne dass zusätzliche Kompilierungen und Symbole geladen werden, sowie von Symbolen mit einem- `SymTagCompilandDetails` Tag, die möglicherweise zusätzliche Symbole laden müssen.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die für diesen Symboltyp gültig sind.  
  
|Eigenschaft|Datentyp|Beschreibung|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` , wenn Bearbeiten und fortfahren bei der Kompilierung aktiviert wurde.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Das Symbol für die exe-Datei.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des übergeordneten lexikalischen Symbols.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|Der Name der Bibliothek oder Objektdatei, aus der das Objekt geladen wurde.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Der Dateiname der Objektdatei der Kompilierungen.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|Der Name der Quelldatei.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompiland` (einen der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswerte) zurück.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Compilanddetails](../../debugger/debug-interface-access/compilanddetails.md)   
 [Compilandenv](../../debugger/debug-interface-access/compilandenv.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
