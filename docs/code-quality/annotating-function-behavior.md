---
title: Hinzufügen einer Anmerkung zum Funktionsverhalten
ms.date: 11/04/2016
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
ms.openlocfilehash: c7ff2551f3a99bf13909f9db3b1659482246e957
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919628"
---
# <a name="annotating-function-behavior"></a>Hinzufügen einer Anmerkung zum Funktionsverhalten
Zusätzlich zum Kommentieren von [Funktionsparametern und Rückgabe Werten](../code-quality/annotating-function-parameters-and-return-values.md)können Sie die Eigenschaften der gesamten Funktion mit Anmerkungen versehen.

## <a name="function-annotations"></a>Funktionsanmerkungen
Die folgenden Anmerkungen gelten für die Funktion als Ganzes und beschreiben, wie Sie sich verhält oder was Sie erwartet.

|Anmerkung|Beschreibung|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Nicht für eigenständige bereitstellen. Stattdessen ist es ein Prädikat, das mit der `_When_` -Anmerkung verwendet werden soll. Weitere Informationen finden Sie unter [angeben, wann und wo eine Anmerkung anwendbar](../code-quality/specifying-when-and-where-an-annotation-applies.md)ist.<br /><br /> Der `name` -Parameter ist eine beliebige Zeichenfolge, die auch `_Function_class_` in einer Anmerkung in der Deklaration einiger Funktionen angezeigt wird.  `_Called_from_function_class_`Gibt einen Wert ungleich 0 (null) zurück, wenn die Funktion, die gerade analysiert `_Function_class_` wird, mit dem gleichen Wert `name`von versehen wird, andernfalls wird 0 (null) zurückgegeben.|
|`_Check_return_`|Kommentiert einen Rückgabewert und gibt an, dass der Aufrufer ihn überprüfen soll. Die Prüfung meldet einen Fehler, wenn die Funktion in einem leeren Kontext aufgerufen wird.|
|`_Function_class_(name)`|Der `name` -Parameter ist eine beliebige Zeichenfolge, die vom Benutzer angegeben wird.  Es ist in einem Namespace vorhanden, der sich von anderen Namespaces unterscheidet. Eine Funktion, ein Funktionszeiger oder – am nützlichsten – ein Funktions Zeigertyp kann als zu einer oder mehreren Funktionsklassen gehörend festgelegt werden.|
|`_Raises_SEH_exception_`|Kommentiert eine Funktion, die immer eine strukturierte Ausnahmehandler-Ausnahme (SEH) auslöst, unterliegt `_When_` den `_On_failure_` Bedingungen und. Weitere Informationen finden Sie unter [angeben, wann und wo eine Anmerkung anwendbar](../code-quality/specifying-when-and-where-an-annotation-applies.md)ist.|
|`_Maybe_raises_SEH_exception_`|Kommentiert eine Funktion, die optional eine SEH-Ausnahme auslöst, unterliegt den `_When_` Bedingungen `_On_failure_` und.|
|`_Must_inspect_result_`|Kommentiert jeden Ausgabewert, einschließlich des Rückgabewerts, der Parameter und Globals.  Der Analyzer meldet einen Fehler, wenn der Wert im Objekt mit Anmerkungen nicht nachfolgend überprüft wird. "Überprüfung" gibt an, ob es in einem bedingten Ausdruck verwendet wird, einem Ausgabeparameter oder einem globalen Ausdruck zugewiesen ist oder als Parameter übergeben wird.  Bei Rückgabe Werten `_Must_inspect_result_` impliziert `_Check_return_`.|
|`_Use_decl_annotations_`|Kann in einer Funktionsdefinition (auch als Funktions Rumpf bezeichnet) anstelle der Liste der Anmerkungen in der Kopfzeile verwendet werden.  Wenn `_Use_decl_annotations_` verwendet wird, werden die Anmerkungen, die in einem Gültigkeitsbereich für die gleiche Funktion angezeigt werden, so verwendet, als wären Sie auch in der Definition mit der `_Use_decl_annotations_` -Anmerkung vorhanden.|

## <a name="successfailure-annotations"></a>Erfolg/Fehler-Anmerkungen
Eine Funktion kann fehlschlagen, und wenn dies der Fall ist, sind die Ergebnisse möglicherweise unvollständig oder unterscheiden sich von den Ergebnissen, wenn die Funktion erfolgreich ausgeführt wird.  Die Anmerkungen in der folgenden Liste bieten Möglichkeiten, das Fehler Verhalten auszudrücken.  Um diese Anmerkungen zu verwenden, müssen Sie Sie aktivieren, um den Erfolg zu ermitteln. Daher ist eine `_Success_` Anmerkung erforderlich.  Beachten Sie `NTSTATUS` , `HRESULT` dass und bereits `_Success_` eine Anmerkung integriert sind. Wenn Sie jedoch ihre eigene `_Success_` Anmerkung für `NTSTATUS` oder `HRESULT`angeben, wird die integrierte Anmerkung überschrieben.

|Anmerkung|Beschreibung|
|----------------|-----------------|
|`_Always_(anno_list)`|Entspricht, d. h. die Anmerkungen in `anno_list` gelten, unabhängig davon, ob die Funktion erfolgreich ausgeführt wurde. `anno_list _On_failure_(anno_list)`|
|`_On_failure_(anno_list)`|Wird nur verwendet, wenn `_Success_` auch verwendet wird, um die Funktion zu kommentieren – entweder explizit oder `_Return_type_success_` implizit über eine typedef. Wenn die `_On_failure_` Anmerkung in einem Funktionsparameter oder Rückgabewert vorhanden ist, verhält sich jede Anmerkung in `anno_list` (anno) so, als ob Sie als `_When_(!expr, anno)`programmiert wäre, `expr` wobei der Parameter für die erforderliche `_Success_` Anmerkung ist. Dies bedeutet, dass die implizite Anwendung `_Success_` von auf alle Post Bedingungen nicht für `_On_failure_`gilt.|
|`_Return_type_success_(expr)`|Kann auf eine typedef angewendet werden. Gibt an, dass alle Funktionen, die diesen Typ zurückgeben und `_Success_` nicht explizit vorhanden sind, so kommentiert werden `_Success_(expr)`, als wären Sie hätten. `_Return_type_success_`kann nicht für eine Funktion oder eine funktionszeigertypedef verwendet werden.|
|`_Success_(expr)`|`expr`ein Ausdruck, der einen Rvalue-Wert ergibt. Wenn die `_Success_` Anmerkung in einer Funktionsdeklaration oder-Definition vorhanden ist, verhält sich jede`anno`Anmerkung () in der Funktion und in der Post-Bedingung so, als wäre `_When_(expr, anno)`Sie als codiert. Die `_Success_` -Anmerkung kann nur für eine Funktion verwendet werden, nicht für deren Parameter oder Rückgabetyp. Es kann höchstens `_Success_` eine Anmerkung für eine Funktion geben, und Sie darf nicht `_When_`in, `_At_`oder `_Group_`sein. Weitere Informationen finden Sie unter [angeben, wann und wo eine Anmerkung anwendbar](../code-quality/specifying-when-and-where-an-annotation-applies.md)ist.|

## <a name="see-also"></a>Siehe auch

- [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Einführung in SAL](../code-quality/understanding-sal.md)
- [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)
- [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)
- [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)
- [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)
- [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)