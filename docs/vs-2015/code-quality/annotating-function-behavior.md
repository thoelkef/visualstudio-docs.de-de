---
title: Hinzufügen einer Anmerkung zum Funktionsverhalten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 7ebda5933f73e2511932f8968104327a56ee7606
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277868"
---
# <a name="annotating-function-behavior"></a>Hinzufügen einer Anmerkung zum Funktionsverhalten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zusätzlich zum Kommentieren von [Funktionsparametern und Rückgabe Werten](../code-quality/annotating-function-parameters-and-return-values.md)können Sie die Eigenschaften der gesamten Funktion mit Anmerkungen versehen.  
  
## <a name="function-annotations"></a>Funktionsanmerkungen  
 Die folgenden Anmerkungen gelten für die Funktion als Ganzes und beschreiben, wie Sie sich verhält oder was Sie erwartet.  
  
|Anmerkung|BESCHREIBUNG|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Nicht für eigenständige bereitstellen. Stattdessen ist es ein Prädikat, das mit der-Anmerkung verwendet werden soll `_When_` . Weitere Informationen finden Sie unter [angeben, wann und wo eine Anmerkung anwendbar](../code-quality/specifying-when-and-where-an-annotation-applies.md)ist.<br /><br /> Der- `name` Parameter ist eine beliebige Zeichenfolge, die auch in einer Anmerkung `_Function_class_` in der Deklaration einiger Funktionen angezeigt wird.  `_Called_from_function_class_` Gibt einen Wert ungleich 0 (null) zurück, wenn die Funktion, die gerade analysiert wird `_Function_class_` , mit dem gleichen Wert von versehen wird, `name` andernfalls wird 0 (null) zurückgegeben.|  
|`_Check_return_`|Kommentiert einen Rückgabewert und gibt an, dass der Aufrufer ihn überprüfen soll. Die Prüfung meldet einen Fehler, wenn die Funktion in einem leeren Kontext aufgerufen wird.|  
|`_Function_class_(name)`|Der- `name` Parameter ist eine beliebige Zeichenfolge, die vom Benutzer angegeben wird.  Es ist in einem Namespace vorhanden, der sich von anderen Namespaces unterscheidet. Eine Funktion, ein Funktionszeiger oder – am nützlichsten – ein Funktions Zeigertyp kann als zu einer oder mehreren Funktionsklassen gehörend festgelegt werden.|  
|`_Raises_SEH_exception_`|Kommentiert eine Funktion, die immer eine strukturierte Ausnahmehandler-Ausnahme (SEH) auslöst, unterliegt `_When_` den `_On_failure_` Bedingungen und. Weitere Informationen finden Sie unter [angeben, wann und wo eine Anmerkung anwendbar](../code-quality/specifying-when-and-where-an-annotation-applies.md)ist.|  
|`_Maybe_raises_SEH_exception_`|Kommentiert eine Funktion, die optional eine SEH-Ausnahme auslöst, unterliegt den `_When_` `_On_failure_` Bedingungen und.|  
|`_Must_inspect_result_`|Kommentiert jeden Ausgabewert, einschließlich des Rückgabewerts, der Parameter und Globals.  Der Analyzer meldet einen Fehler, wenn der Wert im Objekt mit Anmerkungen nicht nachfolgend überprüft wird. "Überprüfung" gibt an, ob es in einem bedingten Ausdruck verwendet wird, einem Ausgabeparameter oder einem globalen Ausdruck zugewiesen ist oder als Parameter übergeben wird.  Bei Rückgabe Werten `_Must_inspect_result_` impliziert `_Check_return_` .|  
|`_Use_decl_annotations_`|Kann in einer Funktionsdefinition (auch als Funktions Rumpf bezeichnet) anstelle der Liste der Anmerkungen in der Kopfzeile verwendet werden.  Wenn `_Use_decl_annotations_` verwendet wird, werden die Anmerkungen, die in einem Gültigkeitsbereich für die gleiche Funktion angezeigt werden, so verwendet, als wären Sie auch in der Definition mit der-Anmerkung vorhanden `_Use_decl_annotations_` .|  
  
## <a name="successfailure-annotations"></a>Erfolg/Fehler-Anmerkungen  
 Eine Funktion kann fehlschlagen, und wenn dies der Fall ist, sind die Ergebnisse möglicherweise unvollständig oder unterscheiden sich von den Ergebnissen, wenn die Funktion erfolgreich ausgeführt wird.  Die Anmerkungen in der folgenden Liste bieten Möglichkeiten, das Fehler Verhalten auszudrücken.  Um diese Anmerkungen zu verwenden, müssen Sie Sie aktivieren, um den Erfolg zu ermitteln. Daher ist eine Anmerkung `_Success_` erforderlich.  Beachten Sie, dass `NTSTATUS` und `HRESULT` bereits eine Anmerkung `_Success_` integriert sind. Wenn Sie jedoch ihre eigene Anmerkung `_Success_` für `NTSTATUS` oder angeben `HRESULT` , wird die integrierte Anmerkung überschrieben.  
  
|Anmerkung|BESCHREIBUNG|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Entspricht, `anno_list _On_failure_(anno_list)` d. h. die Anmerkungen in gelten, unabhängig davon, `anno_list` ob die Funktion erfolgreich ausgeführt wurde.|  
|`_On_failure_(anno_list)`|Wird nur verwendet, wenn `_Success_` auch verwendet wird, um die Funktion zu kommentieren – entweder explizit oder implizit über `_Return_type_success_` eine typedef. Wenn die Anmerkung `_On_failure_` in einem Funktionsparameter oder Rückgabewert vorhanden ist, verhält sich jede Anmerkung in `anno_list` (anno) so, als ob Sie als programmiert wäre `_When_(!expr, anno)` , wobei `expr` der Parameter für die erforderliche `_Success_` Anmerkung ist. Dies bedeutet, dass die implizite Anwendung von `_Success_` auf alle Post Bedingungen nicht für gilt `_On_failure_` .|  
|`_Return_type_success_(expr)`|Kann auf eine typedef angewendet werden. Gibt an, dass alle Funktionen, die diesen Typ zurückgeben und nicht explizit vorhanden `_Success_` sind, so kommentiert werden, als wären Sie hätten `_Success_(expr)` . `_Return_type_success_` kann nicht für eine Funktion oder eine funktionszeigertypedef verwendet werden.|  
|`_Success_(expr)`|`expr` ein Ausdruck, der einen Rvalue-Wert ergibt. Wenn die Anmerkung in `_Success_` einer Funktionsdeklaration oder-Definition vorhanden ist, verhält sich jede Anmerkung ( `anno` ) in der Funktion und in der Post-Bedingung so, als wäre sie als codiert `_When_(expr, anno)` . Die-Anmerkung `_Success_` kann nur für eine Funktion verwendet werden, nicht für deren Parameter oder Rückgabetyp. Es kann höchstens eine Anmerkung `_Success_` für eine Funktion geben, und Sie darf nicht in `_When_` , `_At_` oder sein `_Group_` . Weitere Informationen finden Sie unter [angeben, wann und wo eine Anmerkung anwendbar](../code-quality/specifying-when-and-where-an-annotation-applies.md)ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Sal-Anmerkungen zum Reduzieren von C/C++-Code Fehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Grundlegendes zur SAL](../code-quality/understanding-sal.md)   
 [Kommentieren von Funktionsparametern und Rückgabe Werten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperr Verhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung angewendet wird](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Intrinsische Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
