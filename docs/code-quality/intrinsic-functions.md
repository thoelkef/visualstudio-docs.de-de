---
title: "Systeminterne Funktionen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_String_length_"
  - "_Param_"
  - "_Curr_"
  - "_Old_"
  - "_Nullterm_length_"
  - "_Inexpressible_"
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Systeminterne Funktionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein Ausdruck im SAL kann ein Ausdruck \/C \+\+ sein, vorausgesetzt, dass ein Ausdruck ist, der nicht die Seite Effekt – z. B. C\+\+ verfügt, \-und alle Funktionsaufrufe haben Nebeneffekte in diesen Kontext.  Allerdings stellt SAL einige ähnliche Funktion Objekte und einige reservierte Symbole, die in den SALZausdrücken verwendet werden können.  Diese wird als *systeminterne Funktionen*.  
  
## Allgemeine Verwendung  
 Die folgenden instrinsic Funktionsanmerkungen stellen allgemeines Hilfsprogramm für SAL bereit.  
  
|Anmerkung|**Beschreibung**|  
|---------------|----------------------|  
|`_Curr_`|Ein Synonym für das Objekt, das derzeit hinzugefügt wird.  Wenn die `_At_` Anmerkung verwendet wird, ist `_Curr_` das gleiche wie der erste Parameter in `_At_`.  Andernfalls ist der Parameter oder die gesamte Funktion\/der Rückgabewert, mit dem die Anmerkung lexikalisch zugeordnet ist.|  
|`_Inexpressible_(expr)`|Drückt eine Situation aus, in der die Größe eines Puffers zu komplex ist, anzuzeigen, indem eine Anmerkung Ausdruck\-für Beispiel verwendet, wenn sie abgeleitet wird, indem ein Eingabedataset scannt und dann ausgewählte Member wird.|  
|`_Nullterm_length_(param)`|`param` entspricht der Anzahl der Elemente im Puffer bis einschließlich eines NULL\-Abschlusszeichens jedoch nicht.  Sie ist auf jedem Puffer des NichtAggregats, Nichtvoid\-Typ angewendet werden.|  
|`_Old_(expr)`|Wenn es in der Vorbedingung ausgewertet wird, gibt `_Old_` den Eingabewert `expr` zurück.  Wenn es in der Nachbedingung ausgewertet wird, gibt sie den Wert `expr` zurück, da in der Vorbedingung ausgewertet worden wäre.|  
|`_Param_(n)`|`n` der Parameter für eine Funktion, durch 1 zu von `n` und `n` ist eine literale Ganzzahlkonstante.  Wenn der Parameter genannt wird, gilt diese Anmerkung zu auf den Parameter nach zugreifen identisch. **Note:**  `n` verweist möglicherweise die Positionsparameter, die von Ellipsen definiert sind, oder wird den Funktionsprototypen verwendet werden, in denen Namen nicht verwendet werden.|  
|`return`|Das C\/C\+\+ reservierten Schlüsselwort `return` kann in einem SALZausdruck verwendet werden, um den Rückgabewert einer Funktion anzugeben.  Der Wert ist im Nachbedingung nur verfügbar; Sie entspricht einem Syntaxfehler, um es im Zustand vor zu verwenden.|  
  
## Spezifisches für Zeichenfolgen  
 Die folgenden Anmerkungen der systeminternen Funktion aktivieren Manipulation von Zeichenfolgen.  Alle vier dieser Funktionen dienen den gleichen Zweck erfüllen: zu der Anzahl von Elementen des Typs zurückgeben, der vor einem NULL\-Zeichen gefunden wird.  Die Unterschiede sind die Arten von Daten in den Elementen, die verwiesen wird.  Beachten Sie, dass, wenn Sie die Länge eines auf NULL endende Puffers angeben möchten, der nicht von Zeichen zusammengesetzt ist, die `_Nullterm_length_(param)` Anmerkung im vorherigen Abschnitt verwendet werden.  
  
|Anmerkung|**Beschreibung**|  
|---------------|----------------------|  
|`_String_length_(param)`|`param` entspricht der Anzahl der Elemente in der Zeichenfolge bis einschließlich eines NULL\-Abschlusszeichens jedoch nicht.  Die Anmerkung ist für Zeichenfolge\-vonZeichentypen reserviert.|  
|`strlen(param)`|`param` entspricht der Anzahl der Elemente in der Zeichenfolge bis einschließlich eines NULL\-Abschlusszeichens jedoch nicht.  Die Anmerkung ist für die Verwendung auf Zeichenarrays reserviert und der C\-Ablauffunktion [strlen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l) ähnelt.|  
|`wcslen(param)`|`param` entspricht der Anzahl der Elemente in der Zeichenfolge bis \(jedoch ohne\) einem NULL\-Zeichen.  Die Anmerkung ist für die Verwendung auf Breitzeichenarrays reserviert und der C\-Ablauffunktion [wcslen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l) ähnelt.|  
  
## Siehe auch  
 [Verwenden von SAL\-Anmerkungen zum Reduzieren von C\/C\+\+\-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)