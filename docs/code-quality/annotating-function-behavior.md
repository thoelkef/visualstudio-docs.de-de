---
title: Hinzufügen einer Anmerkung zum Funktionsverhalten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c061c12e7c34a67692af41b72ea7b04b6f06e07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="annotating-function-behavior"></a>Hinzufügen einer Anmerkung zum Funktionsverhalten
Zusätzlich zum Hinzufügen einer Anmerkung zu [Funktionsparameter und Rückgabewerte](../code-quality/annotating-function-parameters-and-return-values.md), Sie können die Eigenschaften der gesamten Funktion mit Anmerkungen versehen.  
  
## <a name="function-annotations"></a>Funktionsanmerkungen  
 Die folgenden Anmerkungen gelten für die Funktion als Ganzes und beschreiben das Verhalten oder was er davon ausgeht, "true" sein.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Sollen nicht eigenständig; Stattdessen ist er ein Prädikat mit dem `_When_` Anmerkung. Weitere Informationen finden Sie unter [angeben, wenn und, in dem eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> Die `name` Parameter ist eine beliebige Zeichenfolge, die auch, in angezeigt eine `_Function_class_` Anmerkung in der Deklaration von einigen Funktionen.  `_Called_from_function_class_` Gibt ungleich NULL, wenn die Funktion, die gerade analysierten mit kommentiert wird `_Function_class_` , besitzt den gleichen Wert für `name`ist, andernfalls wird 0 (null) zurückgegeben.|  
|`_Check_return_`|Einen Rückgabewert merkt und besagt, dass der Aufrufer untersucht werden sollten. Das Überprüfungsprogramm meldet einen Fehler auf, wenn die Funktion in einer "void" Kontext aufgerufen wird.|  
|`_Function_class_(name)`|Die `name` Parameter ist eine beliebige Zeichenfolge, die vom Benutzer festgelegt ist.  Es ist in einem Namespace, der sich von anderen Namespaces ist vorhanden. Eine Funktion, die Funktionszeiger oder – die meisten sinnvoll – ein Funktionszeigertyp Zugehörigkeit zu einer oder mehreren Funktion Klassen festgelegt werden kann.|  
|`_Raises_SEH_exception_`|Eine Funktion, die löst immer eine Ausnahme Exception Handling, strukturierte Handler (SEH) unterliegen merkt `_When_` und `_On_failure_` Bedingungen. Weitere Informationen finden Sie unter [angeben, wenn und, in dem eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Eine Funktion, die optional eine SEH-Ausnahme, unterliegen auslösen kann merkt `_When_` und `_On_failure_` Bedingungen.|  
|`_Must_inspect_result_`|Merkt ausnahmslos Ausgabe, einschließlich Rückgabewert, Parameter und globale Variablen an.  Der Analyzer meldet einen Fehler auf, wenn der Wert in das Objekt mit Anmerkungen nicht anschließend überprüft wird. "Überprüfung" gehören, ob es in einem bedingten Ausdruck verwendet wird, ein Output-Parameter zugewiesen oder globale ist oder als Parameter übergeben wird.  Für Rückgabewerte `_Must_inspect_result_` impliziert `_Check_return_`.|  
|`_Use_decl_annotations_`|Kann auf einer Funktionsdefinition (auch bekannt als eines Funktionsrumpfs) anstelle der Liste der Anmerkungen im Header verwendet werden.  Wenn `_Use_decl_annotations_` wird verwendet, werden die Anmerkungen, die auf einen in-Scope-Header für die gleiche Funktion angezeigt werden, als wäre sie auch in der Definition vorhanden sind, die hat verwendet die `_Use_decl_annotations_` Anmerkung.|  
  
## <a name="successfailure-annotations"></a>Erfolg/Fehler-Anmerkungen  
 Eine Funktion kann fehlschlagen, und wenn dies der Fall ist, ihre Ergebnisse ist möglicherweise unvollständig oder die Ergebnisse unterscheiden, wenn die Funktion erfolgreich ausgeführt wird.  Die Anmerkungen in der folgenden Liste ermöglichen das Fehlerverhalten express.  Um diese Anmerkungen zu verwenden, müssen Sie diese um Erfolg ermitteln aktivieren; aus diesem Grund eine `_Success_` Anmerkung ist erforderlich.  Beachten Sie, dass `NTSTATUS` und `HRESULT` bereits eine `_Success_` Anmerkung integriert werden; allerdings, wenn Sie eine eigene angeben `_Success_` Anmerkung zum `NTSTATUS` oder `HRESULT`, überschreibt die integrierten Anmerkung.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Entspricht `anno_list _On_failure_(anno_list)`; d. h. die Anmerkungen im `anno_list` gelten, und zwar unabhängig davon, ob die Funktion erfolgreich ausgeführt wird.|  
|`_On_failure_(anno_list)`|Zu verwendende nur, wenn `_Success_` dient außerdem zum Kommentieren der Funktion – entweder explizit oder implizit über `_Return_type_success_` auf eine Typdefinition. Wenn die `_On_failure_` Anmerkung ist vorhanden, auf einen Parameter oder Rückgabetyp Funktionswert, jede Anmerkung in `anno_list` (Anno) verhält sich, als ob er wie folgt codiert wurden `_When_(!expr, anno)`, wobei `expr` ist der Parameter, die die erforderlichen `_Success_` Anmerkung. Dies bedeutet, dass die implizite Anwendung `_Success_` auf alle nach der Bedingungen gilt nicht für `_On_failure_`.|  
|`_Return_type_success_(expr)`|Kann auf eine Typdefinition angewendet werden. Gibt an, dass alle Funktionen, die geben und müssen explizit keine zurückgegebene `_Success_` sind mit Anmerkungen versehen, als ob diesem Unternehmen arbeitete `_Success_(expr)`. `_Return_type_success_` kann nicht auf eine Funktion oder eine Funktion Pointer-Typdefinition verwendet werden.|  
|`_Success_(expr)`|`expr` ist ein Ausdruck, der ein Rvalue-Wert ergibt. Wenn die `_Success_` Anmerkung ist vorhanden, auf eine Deklaration oder Definition, die Anmerkungen (`anno`) für die Funktion und in der nachbedingung verhält sich, als ob er wie folgt codiert wurden `_When_(expr, anno)`. Die `_Success_` Anmerkung kann nur für eine Funktion, nicht auf ihre Parameter verwendet werden oder als Rückgabetyp. Es kann höchstens eine `_Success_` Anmerkung für eine Funktion, und es darf sich nicht in einem `_When_`, `_At_`, oder `_Group_`. Weitere Informationen finden Sie unter [angeben, wenn und, in dem eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)