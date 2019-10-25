---
title: Symbole und Symbol Tags | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738532"
---
# <a name="symbols-and-symbol-tags"></a>Symbole und Symboltags
Debuginformationen über ein kompiliertes Programm werden in der Programm Datenbankdatei (. pdb) als Symbole gespeichert, auf die mithilfe der Debug Interface Access (Dia) SDK-APIs zugegriffen werden kann. Alle Symbole haben eine [idiasymmetribol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) -und eine [idiasymmetribol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) -Eigenschaft. Die `symTag`-Eigenschaft gibt die Art des Symbols an, wie durch die Enumeration der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) definiert. Die `symIndexId`-Eigenschaft ist ein `DWORD` Wert, der den eindeutigen Bezeichner für jede Instanz eines Symbols enthält.

 Symbole verfügen auch über Eigenschaften, die zusätzliche Informationen über das Symbol sowie Verweise auf andere Symbole angeben können. Dies ist meistens ein [idiasymmetribol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) oder [idiasymmetribol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Wenn Sie eine Eigenschaft Abfragen, die einen Verweis enthält, wird der Verweis als [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurückgegeben. Solche Eigenschaften werden immer mit einer anderen Eigenschaft mit demselben Namen gekoppelt, aber mit "ID" versehen, z. b. [idiasymmetribol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) und [idiasymmetribol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Die Tabellen in [Symbol Positionen](../../debugger/debug-interface-access/symbol-locations.md), [lexikalische Hierarchie von Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)und [Klassenhierarchie von Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) gliedern die Eigenschaften für die verschiedenen Arten von Symbolen. Diese Eigenschaften können relevante Informationen zu-oder-verweisen auf andere Symbole aufweisen. Da es sich bei den `*Id` Eigenschaften einfach um numerische ordinalbezeichner der zugehörigen Eigenschaften handelt, werden Sie in weiteren Diskussionen ausgelassen. Sie werden nur bei Bedarf für die Parameter Klärung bezeichnet.

 Wenn Sie versuchen, auf die-Eigenschaft zuzugreifen, wenn kein Fehler auftritt und der Symbol Eigenschaft ein Wert zugewiesen wurde, gibt die "Get"-Methode der Eigenschaft `S_OK` zurück. Der Rückgabewert `S_FALSE` gibt an, dass die Eigenschaft für das aktuelle Symbol nicht gültig ist.

## <a name="in-this-section"></a>In diesem Abschnitt

[Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)

Beschreibt die unterschiedlichen Arten von Standorten, die ein Symbol aufweisen kann.

[Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Beschreibt die Symboltypen, die lexikalische Hierarchien bilden, wie z. b. Dateien, Module und Funktionen.

[Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Beschreibt die Symboltypen, die unterschiedlichen Sprachelementen, z. b. Klassen, Arrays und Funktions Rückgabe Typen, entsprechen.

## <a name="see-also"></a>Siehe auch

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)