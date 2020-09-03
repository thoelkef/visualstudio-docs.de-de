---
title: Symbole und Symbol Tags | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 625752125d3c68e9f03afd41cd549995fbc3272e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193539"
---
# <a name="symbols-and-symbol-tags"></a>Symbole und Symboltags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debuginformationen über ein kompiliertes Programm werden in der Programm Datenbankdatei (. pdb) als Symbole gespeichert, auf die mithilfe der Debug Interface Access (Dia) SDK-APIs zugegriffen werden kann. Alle Symbole verfügen über eine [idiasymmetribol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) -Eigenschaft und eine [idiasymmetribol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) -Eigenschaft. Die- `symTag` Eigenschaft gibt die Art des Symbols an, wie durch die Enumeration der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) definiert. Die- `symIndexId` Eigenschaft ist ein `DWORD` Wert, der den eindeutigen Bezeichner für jede Instanz eines Symbols enthält.  
  
 Symbole verfügen auch über Eigenschaften, mit denen zusätzliche Informationen über das Symbol sowie Verweise auf andere Symbole angegeben werden können. Dies ist meistens ein [idiasymmetribol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) oder [idiasymmetribol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Wenn Sie eine Eigenschaft Abfragen, die einen Verweis enthält, wird der Verweis als [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurückgegeben. Solche Eigenschaften werden immer mit einer anderen Eigenschaft mit demselben Namen gekoppelt, aber mit "ID" versehen, z. b. [idiasymmetribol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) und [idiasymmetribol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Die Tabellen in [Symbol Positionen](../../debugger/debug-interface-access/symbol-locations.md), [lexikalische Hierarchie von Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)und [Klassenhierarchie von Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) gliedern die Eigenschaften für die verschiedenen Arten von Symbolen. Diese Eigenschaften können relevante Informationen zu-oder-verweisen auf andere Symbole aufweisen. Da `*Id` es sich bei den Eigenschaften einfach um numerische ordinalbezeichner der zugehörigen Eigenschaften handelt, werden Sie in weiteren Diskussionen ausgelassen. Sie werden nur bei Bedarf für die Parameter Klärung bezeichnet.  
  
 Wenn Sie versuchen, auf die-Eigenschaft zuzugreifen, wenn kein Fehler auftritt und der Symbol Eigenschaft ein Wert zugewiesen wurde, gibt die "Get"-Methode der Eigenschaft zurück `S_OK` . Der Rückgabewert `S_FALSE` gibt an, dass die Eigenschaft für das aktuelle Symbol nicht gültig ist.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)  
 Beschreibt die unterschiedlichen Arten von Standorten, die ein Symbol aufweisen kann.  
  
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Beschreibt die Symboltypen, die lexikalische Hierarchien bilden, wie z. b. Dateien, Module und Funktionen.  
  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Beschreibt die Symboltypen, die unterschiedlichen Sprachelementen, z. b. Klassen, Arrays und Funktions Rückgabe Typen, entsprechen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
