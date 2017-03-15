---
title: "Hinzuf&#252;gen einer Anmerkung zu Strukturen und Klassen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Field_size_bytes_part_"
  - "_Field_size_bytes_full_opt_"
  - "_Field_size_bytes_"
  - "_Field_size_opt_"
  - "_Field_size_part_"
  - "_Field_size_bytes_part_opt_"
  - "_Field_range_"
  - "_Field_size_part_opt_"
  - "_Field_size_"
  - "_Field_size_bytes_opt_"
  - "_Struct_size_bytes_"
  - "_Field_size_bytes_full_"
  - "_Field_size_full_"
  - "_Field_size_full_opt_"
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Hinzuf&#252;gen einer Anmerkung zu Strukturen und Klassen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Struktur- und Elemente mit Anmerkungen, die Invarianten fungieren versehen – sie werden als bei einem beliebigen Funktionsaufruf oder/Beendigung, bei der die einschließende Struktur als Parameter oder einen Ergebniswert, true sein.  
  
## <a name="struct-and-class-annotations"></a>Struktur- und Klassen-Anmerkungen  
  
-   `_Field_range_(low, high)`  
  
     Das Feld wird im Bereich (inklusiv) von `low` zu `high`.  Gleichbedeutend mit `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` auf das Objekt mit Anmerkungen mit den entsprechenden Pre oder Post-Bedingungen angewendet.  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Ein Feld, das eine schreibbare Größe in Elementen (oder Bytes) als durch angegeben hat `size`.  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Ein Feld, das eine schreibbare Größe in Elementen (oder Bytes) als durch angegeben hat `size`, und die `count` dieser Elemente (Bytes), die gelesen werden.  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Ein Feld mit lesbare und schreibbare Größe in Elemente (oder Bytes) als angegebenen `size`.  
  
-   `_Struct_size_bytes_(size)`  
  
     Ein Feld mit lesbare und schreibbare Größe in Elemente (oder Bytes) als angegebenen `size`.  
  
     Gilt für die Deklaration Struktur oder Klasse.  Gibt an, dass ein gültiges Objekt dieses Typs möglicherweise größer als die deklarierte Typ mit der angegebenen Anzahl von Bytes wird durch `size`.  Zum Beispiel:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     Die Puffergröße in Bytes eines Parameters `pM` vom Typ `MyStruct *` wird dann ausgeführt werden:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)