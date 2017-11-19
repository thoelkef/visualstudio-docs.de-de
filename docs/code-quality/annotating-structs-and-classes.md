---
title: "Hinzufügen einer Anmerkung zu Strukturen und Klassen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 651108f2c917fb81857e3466384a9bfebada4a4b
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="annotating-structs-and-classes"></a>Hinzufügen einer Anmerkung zu Strukturen und Klassen
Sie können mit einer Anmerkung versehen Struktur- und Elemente mithilfe von Anmerkungen, die als invarianten agieren – sie werden als "true" bei einem beliebigen Funktionsaufruf oder/Beendigung, die die einschließende Struktur als einen Parameter oder einen Ergebniswert umfasst.  
  
## <a name="struct-and-class-annotations"></a>Struktur- und Klassen-Anmerkungen  
  
-   `_Field_range_(low, high)`  
  
     Das Feld wird im Bereich (inklusiv) von `low` auf `high`.  Entspricht `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` mit der entsprechenden Pre oder Post-Bedingungen für das Objekt mit Anmerkungen übernommen.  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Ein Feld, eine schreibbare Größe in Elemente (oder Bytes) als gemäß enthält `size`.  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Ein Feld, eine schreibbare Größe in Elemente (oder Bytes) als gemäß enthält `size`, und die `count` dieser Elemente (Bytes), die lesbar sind.  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Ein Feld mit lesbare und schreibbare Größe in Elemente (oder Bytes) als gemäß `size`.  
  
-   `_Struct_size_bytes_(size)`  
  
     Ein Feld mit lesbare und schreibbare Größe in Elemente (oder Bytes) als gemäß `size`.  
  
     Gilt für die Deklaration von Struct "oder"-Klasse.  Gibt an, dass ein gültiges Objekt dieses Typs möglicherweise größer als der deklarierte Typ mit der angegebenen Anzahl von Bytes wird durch `size`.  Zum Beispiel:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        ...  
    };  
  
    ```  
  
     Die Puffergröße in Bytes eines Parameters `pM` des Typs `MyStruct *` wird dann ausgeführt werden:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)