---
title: Klassenhierarchie von Symbol Typen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c42ea4bb2d5c2ad91538bec8b31774a5a41aa4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745455"
---
# <a name="class-hierarchy-of-symbol-types"></a>Klassenhierarchie der Symboltypen
In der folgenden Tabelle werden die Symboltypen in der Klassenhierarchie beschrieben.

## <a name="symbol-types"></a>Symbol Typen

|Symboltyp|Beschreibung|
|-----------------|-----------------|
|[UDT](../../debugger/debug-interface-access/udt.md)|Symbol, das zum Darstellen der einzelnen Klassen, Strukturen und Union verwendet wird.|
|[Enum (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Symbol für Enumerationstypen.|
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Symbol für Zeiger Typen.|
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Symbol für Array Typen.|
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Symbol für Basis Typen|
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Symbol, das Namen für andere Typen einführt.|
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Das Symbol, das für jede Basisklasse eines benutzerdefinierten Typs (User-Defined Type, UDT) verwendet wird.|
|[Friend (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Symbol für Friend-Klassen und Friend-Funktionen.|
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Symbol für jede eindeutige Funktions Signatur.|
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Symbol für jeden Parameter einer Funktion.|
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Das Symbol für die Größe der virtuellen Tabelle.|
|[VTable](../../debugger/debug-interface-access/vtable.md)|Symbol für eine virtuelle Tabelle.|
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Symbol für Hersteller definierten Typ.|
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Symbol für einen Typ, der in den Metadaten definiert ist.|
|[Dimension](../../debugger/debug-interface-access/dimension.md)|Symbol für Array Dimensionen.|

> [!NOTE]
> Jedes Symbol kann über Eigenschaften verfügen, die Informationen über das Symbol enthalten, sowie Verweise auf andere Symbole. Diese Eigenschaften sind in den einzelnen Symbolthemen aufgeführt.

## <a name="see-also"></a>Siehe auch
- [CV_access_e-Enumeration](../../debugger/debug-interface-access/cv-access-e.md)
- [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)