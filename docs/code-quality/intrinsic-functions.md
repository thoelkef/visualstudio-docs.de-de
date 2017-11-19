---
title: Systeminterne Funktionen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be65ae9177591b015cd8b29b3dbdc262b66a30ab
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="intrinsic-functions"></a>Systeminterne Funktionen
Ein Ausdruck in SAL kann ein C/C++-Ausdruck sein, vorausgesetzt, dass es sich um einen Ausdruck handelt, die keine nachteiligen Auswirkungen haben – z. B. ++,--, und Funktionsaufrufe, die alle haben Nebenwirkungen in diesem Kontext.  SAL bietet allerdings einige funktionsähnliche-Objekte und einige reservierte Symbole, die in SAL-Ausdrücken verwendet werden können. Diese werden als bezeichnet *systeminterne Funktionen*.  
  
## <a name="general-purpose"></a>Allgemeine Verwendung  
 Die folgenden intrinsische funktionsanmerkungen bieten allgemeine Hilfsprogramm auf SAL-Anmerkungen.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_Curr_`|Ein Synonym für das Objekt, das derzeit kommentiert wird.  Wenn die `_At_` Anmerkung wird verwendet, `_Curr_` ist identisch mit dem ersten Parameter `_At_`.  Andernfalls ist er den Parameter oder der gesamte Funktionsrückgabe-Wert, den die Anmerkung lexikalisch zugeordnet ist.|  
|`_Inexpressible_(expr)`|Eine Situation, in dem die Größe eines Puffers zu komplex ist für darstellen, indem Sie mithilfe eines Ausdrucks Anmerkung, ausdrückt – z. B. wenn er berechnet wird, durch das Scannen von ein Eingabedataset, und klicken Sie dann gezählt ausgewählte Elemente.|  
|`_Nullterm_length_(param)`|`param`ist die Anzahl der Elemente im Puffer bis zur, aber nicht einschließlich ein null-Abschlusszeichen. Es kann auf alle Puffer des Typs von nicht-aggregierbare, nicht als "void" angewendet werden.|  
|`_Old_(expr)`|Bei der Auswertung in Vorbedingung, `_Old_` gibt den Eingabewert `expr`.  Wenn sie in der nachbedingung ausgewertet wird, wird der Wert `expr` wie in Vorbedingung ausgewertet worden wären.|  
|`_Param_(n)`|Die `n`-ten Parameter für eine Funktion, beginnend mit 1 bis `n`, und `n` eine literale ganzzahlige Konstante ist. Wenn der Parameter benannt wird, ist diese Anmerkung für den Zugriff auf den Parameter anhand des Namens identisch. **Hinweis:** `n` bezieht sich möglicherweise auf die Positionsparameter, die durch eine Ellipse definiert, oder verwendet werden können in Funktionsprototypen, in dem Namen nicht verwendet werden.  |  
|`return`|Die C/C++-reserviertes Schlüsselwort `return` können in einem SAL-Ausdruck verwendet werden, um den Rückgabewert einer Funktion anzugeben.  Der Wert ist nur im Post-Status verfügbar. Es ist ein Syntaxfehler zu dessen Verwendung in den Zustand vor.|  
  
## <a name="string-specific"></a>Spezifisches für Zeichenfolgen  
 Die folgende integrierte funktionsanmerkungen ermöglichen Manipulation von Zeichenfolgen. Alle vier dieser Funktionen dienen den gleichen Zweck: um die Anzahl der Elemente des Typs zurückzugeben, die gefunden wird, bevor ein null-Abschlusszeichen. Die Unterschiede werden die Arten von Daten in den Elementen, die auf die verwiesen werden. Beachten Sie, die, wenn Sie die Länge der eine Null-terminierte angeben möchten, der als Puffer, besteht nicht aus Zeichen, verwenden Sie die `_Nullterm_length_(param)` Anmerkung aus dem vorherigen Abschnitt.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_String_length_(param)`|`param`ist die Anzahl von Elementen in der Zeichenfolge bis zum, aber nicht einschließlich ein null-Abschlusszeichen. Diese Anmerkung ist für Zeichenfolge-Zeichentypen reserviert.|  
|`strlen(param)`|`param`ist die Anzahl von Elementen in der Zeichenfolge bis zum, aber nicht einschließlich ein null-Abschlusszeichen. Diese Anmerkung ist reserviert für auf Zeichen arrays und der C-Laufzeitfunktion ähnelt [strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
|`wcslen(param)`|`param`die Anzahl der Elemente in der Zeichenfolge bis zu (aber nicht einschließlich) ist ein null-Abschlusszeichen. Diese Anmerkung ist reserviert für Verwendung in Breitzeichen arrays und der C-Laufzeitfunktion ähnelt [wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)