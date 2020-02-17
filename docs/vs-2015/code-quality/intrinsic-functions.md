---
title: Intrinsische Funktionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: a0a6cd31cbc8cf73cfa2c7e9ee7c096fa56799b9
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277959"
---
# <a name="intrinsic-functions"></a>Systeminterne Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Ausdruck in SAL kann ein C/C++ Ausdruck sein, vorausgesetzt, dass es sich um einen Ausdruck handelt, der keine Nebeneffekte hat – z. b. + +,--, und Funktionsaufrufe haben alle Nebeneffekte in diesem Kontext.  SAL bietet jedoch einige Funktions ähnliche Objekte und einige reservierte Symbole, die in SAL-Ausdrücken verwendet werden können. Diese werden als *intrinsische Funktionen*bezeichnet.  
  
## <a name="general-purpose"></a>Universell  
 Die folgenden Anmerkungen in der instraninsic-Funktion bieten Allgemeines Hilfsprogramm für SAL.  
  
|Anmerkung|BESCHREIBUNG|  
|----------------|-----------------|  
|`_Curr_`|Ein Synonym für das Objekt, das gerade mit Anmerkungen versehen wird.  Wenn die `_At_` Anmerkung verwendet wird, ist `_Curr_` identisch mit dem ersten Parameter für `_At_`.  Andernfalls ist es der-Parameter oder die gesamte Funktion/der gesamte Rückgabewert, mit der die Anmerkung lexikalisch verknüpft ist.|  
|`_Inexpressible_(expr)`|Drückt eine Situation aus, bei der die Größe eines Puffers zu komplex ist, indem ein Anmerkung-Ausdruck verwendet wird, z. –. wenn er durch Scannen eines Eingabe Datasets und anschließendes zählen ausgewählter Elemente berechnet wird.|  
|`_Nullterm_length_(param)`|`param` ist die Anzahl der Elemente im Puffer bis einschließlich eines NULL-Terminator. Sie kann auf einen beliebigen Puffer eines nicht aggregierten, nicht-void-Typs angewendet werden.|  
|`_Old_(expr)`|Wenn Sie in Vorbedingung ausgewertet wird, gibt `_Old_` den Eingabe Wert `expr`zurück.  Wenn Sie in der nach Bedingung ausgewertet wird, wird der Wert `expr` zurückgegeben, da dieser in Vorbedingung ausgewertet worden wäre.|  
|`_Param_(n)`|Der `n`Th-Parameter für eine Funktion, der von 1 bis `n`und `n` eine ganzzahlige Ganzzahl-Konstante ist. Wenn der-Parameter den Namen hat, ist diese Anmerkung identisch mit dem Zugriff auf den Parameter über den Namen. **Hinweis:** `n` können auf die Positions Parameter verweisen, die durch Auslassungs Zeichen definiert werden, oder Sie können in Funktionsprototypen verwendet werden, bei denen keine Namen verwendet werden.|  
|`return`|Das C/C++ reserved-Schlüsselwort `return` kann in einem SAL-Ausdruck verwendet werden, um den Rückgabewert einer Funktion anzugeben.  Der Wert ist nur im Post-Zustand verfügbar. Es handelt sich hierbei um einen Syntax Fehler, der im vorab Zustand verwendet werden kann.|  
  
## <a name="string-specific"></a>Spezifisches für Zeichenfolgen  
 Die folgenden intrinsischen Funktions Anmerkungen ermöglichen die Bearbeitung von Zeichen folgen. Alle vier dieser Funktionen dienen dem gleichen Zweck: zum Zurückgeben der Anzahl von Elementen des Typs, der vor einem NULL-Terminator gefunden wurde. Die Unterschiede sind die Arten von Daten in den Elementen, auf die verwiesen wird. Beachten Sie Folgendes: Wenn Sie die Länge eines null-terminierten Puffers angeben möchten, der nicht aus Zeichen besteht, verwenden Sie die `_Nullterm_length_(param)` Anmerkung aus dem vorherigen Abschnitt.  
  
|Anmerkung|BESCHREIBUNG|  
|----------------|-----------------|  
|`_String_length_(param)`|`param` ist die Anzahl der Elemente in der Zeichenfolge bis zu einem NULL-Terminator. Diese Anmerkung ist für Zeichen folgen Typen reserviert.|  
|`strlen(param)`|`param` ist die Anzahl der Elemente in der Zeichenfolge bis zu einem NULL-Terminator. Diese Anmerkung ist für die Verwendung in Zeichen Arrays reserviert und ähnelt der C-Lauf Zeitfunktion " [strinlen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)".|  
|`wcslen(param)`|`param` ist die Anzahl der Elemente in der Zeichenfolge bis zu einem NULL-Terminator (ohne Angabe). Diese Anmerkung ist für die Verwendung von breit Zeichen Arrays reserviert und ähnelt der C-Lauf Zeitfunktion [wcslen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Sal-Anmerkungen zum Reduzieren vonC++ C/Code-Fehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 Grundlegendes zu [SAL](../code-quality/understanding-sal.md)   
 Hinzufügen von [Anmerkungen zu Funktionsparametern und Rückgabe Werten](../code-quality/annotating-function-parameters-and-return-values.md)   
 Hinzufügen einer [Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 Hinzufügen einer [Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 Hinzufügen einer [Anmerkung zum Sperr Verhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung angewendet](../code-quality/specifying-when-and-where-an-annotation-applies.md) wird   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
