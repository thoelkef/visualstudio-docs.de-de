---
title: Hinzufügen einer Anmerkung zu Strukturen und Klassen
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: e37d1ad27fab77e5aff1064ecc83e67ee7cc739d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935055"
---
# <a name="annotating-structs-and-classes"></a>Hinzufügen einer Anmerkung zu Strukturen und Klassen
Sie können Struktur- und Elemente mit Anmerkungen versehen, verwenden von Anmerkungen, die wie invarianten fungiert – sie werden als "true" bei einem beliebigen Funktionsaufruf oder eine Funktion Einstiegs-/ausstiegsspunkt, die die einschließende Struktur als Parameter oder einen Ergebniswert umfasst.

## <a name="struct-and-class-annotations"></a>Struktur- und Klassen-Anmerkungen

-   `_Field_range_(low, high)`

     Das Feld befindet sich im Bereich (inklusiv) von `low` zu `high`.  Äquivalent zu `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` auf das mit Anmerkungen versehene Objekt angewendet werden, mithilfe der entsprechenden Pre oder Post-Bedingungen.

-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Ein Feld mit einem schreibbare Größe in Elemente (oder Bytes) als gemäß `size`.

-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Ein Feld mit einem schreibbare Größe in Elemente (oder Bytes) als gemäß `size`, und die `count` dieser Elemente (Bytes), die gelesen werden.

-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Ein Feld mit lesbare und schreibbare Größe in Elemente (oder Bytes) als gemäß `size`.

-   `_Field_z_`

     Ein Feld, eine Null-terminierte Zeichenfolge enthält.

-   `_Struct_size_bytes_(size)`

     Gilt für die Struktur oder Klasse Deklaration.  Gibt an, dass ein gültiges Objekt dieses Typs möglicherweise größer als der deklarierte Typ, mit der Anzahl von Bytes, die angegeben wird `size`.  Zum Beispiel:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Die Puffergröße in Bytes für einen Parameter `pM` des Typs `MyStruct *` wird, werden ausgeführt:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="see-also"></a>Siehe auch

- [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Einführung in SAL](../code-quality/understanding-sal.md)
- [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)
- [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)
- [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)
- [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)
- [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)