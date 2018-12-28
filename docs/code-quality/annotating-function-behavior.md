---
title: Hinzufügen einer Anmerkung zum Funktionsverhalten
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 8aa47ad88f137ff9a74d0365c25995125c835c03
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53801767"
---
# <a name="annotating-function-behavior"></a>Hinzufügen einer Anmerkung zum Funktionsverhalten
Zusätzlich zum Hinzufügen von Kommentaren [Funktionsparameter und Rückgabewerte](../code-quality/annotating-function-parameters-and-return-values.md), Sie können die gesamte Funktion Eigenschaften mit Anmerkungen versehen.

## <a name="function-annotations"></a>Funktionsanmerkungen
 Die folgenden Anmerkungen gelten für die Funktion als Ganzes und beschreiben das Verhalten oder was sie erwartet, dass "true" ist.

|Anmerkung|Beschreibung|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Sollen nicht allein stehen; Stattdessen ist er ein Prädikat, mit der `_When_` Anmerkung. Weitere Informationen finden Sie unter [angeben, wenn und wo eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> Die `name` Parameter ist eine beliebige Zeichenfolge, die auch, in angezeigt einem `_Function_class_` Anmerkung in der Deklaration von einigen Funktionen.  `_Called_from_function_class_` Gibt ungleich NULL, wenn die Funktion, die gerade analysiert wird mit Anmerkung versehen ist `_Function_class_` Listenfeldsteuerelement mit den gleichen Wert des `name`ist, andernfalls wird 0 (null) zurückgegeben.|
|`_Check_return_`|Einen Rückgabewert kommentiert und gibt an, dass der Aufrufer, die sie überprüfen sollten. Die voraussetzungsprüfung meldet einen Fehler auf, wenn die Funktion in einem "void" Kontext aufgerufen wird.|
|`_Function_class_(name)`|Die `name` Parameter ist eine beliebige Zeichenfolge, die vom Benutzer festgelegt ist.  Es ist vorhanden, in einem Namespace, der aus anderen Namespaces unterschieden wird. Eine Funktion, die Funktionszeiger oder – die meisten sinnvoll – ein Funktionszeigertyp Zugehörigkeit zu einer oder mehreren Funktion Klassen festgelegt werden kann.|
|`_Raises_SEH_exception_`|Kommentiert eine Funktion, die löst immer eine strukturierte Ausnahmen (SEH)-Handler-Ausnahme unterliegen `_When_` und `_On_failure_` Bedingungen. Weitere Informationen finden Sie unter [angeben, wenn und wo eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|Kommentiert eine Funktion, die optional eine SEH-Ausnahme, unterliegt auslösen kann `_When_` und `_On_failure_` Bedingungen.|
|`_Must_inspect_result_`|Kommentiert alle Ausgabewert, einschließlich Rückgabewert, Parameter und globale Variablen.  Der Analyzer meldet einen Fehler auf, wenn der Wert in das Objekt mit Anmerkungen nicht anschließend überprüft wird. "Überprüfung" enthält, die in einem bedingten Ausdruck verwendet wird, ist ein Output-Parameter zugeordnet oder globale oder als Parameter übergeben wird.  Rückgabewerte `_Must_inspect_result_` impliziert `_Check_return_`.|
|`_Use_decl_annotations_`|Kann in einer Funktionsdefinition (auch bekannt als eines Funktionsrumpfs) anstelle der Liste der Anmerkungen im Header verwendet werden.  Wenn `_Use_decl_annotations_` wird verwendet, die Anmerkungen, die auf einem in-Scope-Header für die gleiche Funktion angezeigt werden verwendet, als ob sie auch in der Definition vorhanden sind, die die `_Use_decl_annotations_` Anmerkung.|

## <a name="successfailure-annotations"></a>Erfolg/Fehler-Anmerkungen
 Eine Funktion kann ein Fehler auftreten, und wenn dies der Fall, die Ergebnisse möglicherweise unvollständig oder die Ergebnisse unterscheiden, wenn die Funktion erfolgreich ist.  Die Anmerkungen in der folgenden Liste bieten Methoden, um das Fehlerverhalten auszudrücken.  Um diese Anmerkungen zu verwenden, müssen Sie diese um Erfolg ermitteln aktivieren; aus diesem Grund eine `_Success_` Anmerkung ist erforderlich.  Beachten Sie, dass `NTSTATUS` und `HRESULT` bereits eine `_Success_` Anmerkung, die integriert werden; jedoch wenn Sie Ihre eigenen angeben `_Success_` Anmerkung zu `NTSTATUS` oder `HRESULT`, überschreibt es die integrierte Anmerkung.

|Anmerkung|Beschreibung|
|----------------|-----------------|
|`_Always_(anno_list)`|Äquivalent zu `anno_list _On_failure_(anno_list)`; d. h. die Anmerkungen im `anno_list` gelten, und zwar unabhängig davon, ob die Funktion erfolgreich ist.|
|`_On_failure_(anno_list)`|Zu verwendende nur, wenn `_Success_` wird auch verwendet, um die Funktion mit Anmerkungen versehen – entweder explizit oder implizit über `_Return_type_success_` in einer Typedef. Wenn die `_On_failure_` Anmerkung ist vorhanden, in einem Parameter oder Rückgabewert Funktionswert, jede Anmerkung in `anno_list` (Anno) verhält, als ob es als codierte `_When_(!expr, anno)`, wobei `expr` ist der Parameter, die die erforderlichen `_Success_` Anmerkung. Dies bedeutet, dass die implizite Anwendung `_Success_` für alle nachbedingungen gilt nicht für `_On_failure_`.|
|`_Return_type_success_(expr)`|Kann auf eine Typdefinition angewendet werden. Gibt an, dass alle Funktionen, die geben und müssen explizit keine zurückgegebene `_Success_` versehen sind, als hätte sie `_Success_(expr)`. `_Return_type_success_` kann nicht in einer Funktion oder eine Funktion Pointer-Typdefinition verwendet werden.|
|`_Success_(expr)`|`expr` ist ein Ausdruck, der ein Rvalue-Wert ergibt. Wenn die `_Success_` Anmerkung ist vorhanden, auf die Deklaration einer Funktion oder die Definition, die jede Anmerkung (`anno`) für die Funktion und in der nachbedingung verhält, als ob es als codiert wurden `_When_(expr, anno)`. Die `_Success_` Anmerkung kann verwendet werden, nur für eine Funktion kann nicht auf die Parameter oder Rückgabetyp. Es kann höchstens eine `_Success_` Anmerkung für eine Funktion, und es darf sich nicht in einem `_When_`, `_At_`, oder `_Group_`. Weitere Informationen finden Sie unter [angeben, wenn und wo eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Siehe auch

- [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Einführung in SAL](../code-quality/understanding-sal.md)
- [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)
- [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)
- [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)
- [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)
- [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)