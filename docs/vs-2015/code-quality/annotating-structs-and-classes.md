---
title: Kommentieren von Strukturen und Klassen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 6db2202971facb0419db68c04835c8d5c848f528
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271583"
---
# <a name="annotating-structs-and-classes"></a>Hinzufügen einer Anmerkung zu Strukturen und Klassen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Struktur-und Klassenmember mit Anmerkungen versehen, die wie invarianten funktionieren – Sie werden als true an jedem Funktions-oder Funktions Eintrag bzw. in einem Funktionswert, der die einschließende Struktur als Parameter oder Ergebniswert einschließt, angenommen.  
  
## <a name="struct-and-class-annotations"></a>Struktur- und Klassen-Anmerkungen  
  
- `_Field_range_(low, high)`  
  
     Das Feld befindet sich im Bereich (einschließlich) von `low` bis `high`.  Äquivalent zu `_Satisfies_(_Curr_ >= low && _Curr_ <= high)`, die auf das mit Anmerkungen versehene Objekt angewendet werden, indem die entsprechenden Pre-oder Post-Bedingungen verwendet werden.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Ein Feld mit einer beschreibbaren Größe in Elementen (oder Bytes), wie in `size`angegeben.  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)``_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Ein Feld mit einer beschreibbaren Größe in Elementen (oder Bytes), wie durch `size`angegeben, und die `count` dieser Elemente (Bytes), die lesbar sind.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Ein Feld, das sowohl lesbare als auch beschreibbare Größe in Elementen (oder Bytes) aufweist, wie durch `size`angegeben.  
  
- `_Struct_size_bytes_(size)`  
  
     Ein Feld, das sowohl lesbare als auch beschreibbare Größe in Elementen (oder Bytes) aufweist, wie durch `size`angegeben.  
  
     Gilt für die Struktur-oder Klassen Deklaration.  Gibt an, dass ein gültiges Objekt dieses Typs möglicherweise größer als der deklarierte Typ und die Anzahl der Bytes ist, die durch `size`angegeben werden.  Beispiel:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     Die Puffergröße eines Parameter `pM` vom Typ `MyStruct *` wird dann wie folgt angenommen:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Sal-Anmerkungen zum Reduzieren vonC++ C/Code-Fehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 Grundlegendes zu [SAL](../code-quality/understanding-sal.md)   
 Hinzufügen von [Anmerkungen zu Funktionsparametern und Rückgabe Werten](../code-quality/annotating-function-parameters-and-return-values.md)   
 Hinzufügen einer [Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 Hinzufügen einer [Anmerkung zum Sperr Verhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung angewendet](../code-quality/specifying-when-and-where-an-annotation-applies.md) wird   
 [Intrinsische Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
