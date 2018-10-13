---
title: Lexikalische Hierarchie der Symboltypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfb8fd751d6230dd839d073a61e80cabf5d48892
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305486"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Lexikalische Hierarchie der Symboltypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die folgende Tabelle zeigt die Symboltypen in der lexikalische Hierarchie an.  
  
## <a name="symbol-types"></a>Symboltypen  
  
|Symboltyp|Beschreibung|  
|-----------------|-----------------|  
|[Anmerkung](../../debugger/debug-interface-access/annotation.md)|Hiermit wird ein mit Anmerkungen versehenen Speicherort im Programmcode.|  
|[Block](../../debugger/debug-interface-access/block.md)|Gibt geschachtelte Bereiche in Funktionen an.|  
|`Compiland`|Gibt an, eine `compiland` zur .exe-Datei verknüpft.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Gibt an, in denen möglicherweise zusätzliche Compiland-Details werden geladen und fallen daher die Laufzeit-overhead zum Abrufen von Compiland-Daten.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Gibt zusätzliche Umgebungsvariablen für die Kompilierung von der Kompiliereinheit signifikant.|  
|[Benutzerdefiniert (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Gibt ein benutzerdefiniertes Symbol an.|  
|[Daten (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Gibt die Variablen als Parameter, lokale Variablen, globale Variablen und Klassenmember an.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Gibt den globalen Bereich der Daten an. entspricht einer vollständigen .exe oder .dll-Datei.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Gibt an, eine Funktion mit einem bestimmten Zeitpunkt auf dem Debuggen besteht darin, zu beenden.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Gibt an, eine Funktion mit einem bestimmten Zeitpunkt unter dem Debuggen begonnen werden soll.|  
|[Funktion (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Gibt eine Funktion.|  
|[Label (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Gibt einen Speicherort im Programmcode.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Gibt ein externes Symbol, das angezeigt wird, wenn Sie das ausführbare Programm zu erstellen.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Gibt an, eine `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Gibt an, eine `namespace`Bezeichner.|  
  
> [!NOTE]
>  Zusätzliche Symboleigenschaften können je nach den Symboltyp verfügbar sein. Diese Eigenschaften werden in den einzelnen Symbol-Themen aufgelistet.  
  
## <a name="see-also"></a>Siehe auch  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)



