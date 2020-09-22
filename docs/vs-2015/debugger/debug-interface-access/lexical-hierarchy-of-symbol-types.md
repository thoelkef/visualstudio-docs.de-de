---
title: Lexikalische Hierarchie von Symbol Typen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e70b83046c41b13cb51324eb63e81b26a118a81f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841136"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Lexikalische Hierarchie der Symboltypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In der folgenden Tabelle werden die Symboltypen in der lexikalischen Hierarchie angezeigt.  
  
## <a name="symbol-types"></a>Symbol Typen  
  
|Symboltyp|BESCHREIBUNG|  
|-----------------|-----------------|  
|[Anmerkung](../../debugger/debug-interface-access/annotation.md)|Gibt eine mit Anmerkungen versehene Position im Programmcode an.|  
|[Blockieren](../../debugger/debug-interface-access/block.md)|Gibt die in Funktionen unter fallenen Bereiche an.|  
|`Compiland`|Gibt einen `compiland` an, der mit der exe-Datei verknüpft ist.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Gibt Kompilierungen und Daten an, für die möglicherweise zusätzliche compilerdetails geladen werden müssen, sodass der abzurufende Lauf Zeitaufwand entsteht.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Gibt alle zusätzlichen Umgebungsvariablen an, die für die Kompilierung des Kompilierens wichtig sind.|  
|[Benutzerdefiniert (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Gibt ein benutzerdefiniertes Symbol an.|  
|[Daten (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Gibt Variablen wie Parameter, lokale Variablen, globale Variablen und Klassenmember an.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Gibt den globalen Gültigkeitsbereich der Daten an. entspricht einer vollständigen exe-oder DLL-Datei.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Gibt eine Funktion an, die über einen definierten Punkt verfügt, an dem das Debuggen beendet werden soll.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Gibt eine Funktion an, die über einen definierten Punkt verfügt, an dem der Debugvorgang beginnen soll.|  
|[Funktion (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Gibt eine Funktion an.|  
|[Label (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Gibt einen Speicherort im Programmcode an.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Gibt ein externes Symbol an, das angezeigt wird, wenn das ausführbare Programm aufgebaut wird.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Gibt ein an `thunk` .|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Gibt einen- `namespace` Bezeichner an.|  
  
> [!NOTE]
> Je nach Symboltyp sind möglicherweise weitere Symbol Eigenschaften verfügbar. Diese Eigenschaften sind in den einzelnen Symbolthemen aufgeführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Klassenhierarchie von Symbol Typen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Idiasymmetribol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Symbole und Symbol Tags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
