---
title: "Hinzuf&#252;gen einer Anmerkung zum Funktionsverhalten | Microsoft Docs"
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
  - "_On_failure_"
  - "_Return_type_success_"
  - "_Always_"
  - "_Maybe_raises_SEH_exception_"
  - "_Raises_SEH_exception_"
  - "_Called_from_function_class_"
  - "_Function_class_"
  - "_Must_inspect_result_"
  - "_Success_"
  - "_Check_return_"
  - "_Use_decl_annotations_"
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Hinzuf&#252;gen einer Anmerkung zum Funktionsverhalten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Zusätzlich zum Kommentieren von [Funktionsparameter und Rückgabewerte](../code-quality/annotating-function-parameters-and-return-values.md), können Sie Eigenschaften der Ganzfunktion kommentieren.  
  
## Funktionsanmerkungen  
 Die folgenden Anmerkungen gelten für die Funktion als ganzes zu und beschreiben, wie diese sich verhält, oder welche sie erwartet, um ausgeführt zu sein.  
  
|Anmerkung|**Beschreibung**|  
|---------------|----------------------|  
|`_Called_from_function_class_(name)`|Die nicht eigenständig zu; sondern ein mit der `_When_` \- Anmerkung verwendete Prädikat.  Weitere Informationen finden Sie unter [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> Der Parameter `name` ist eine beliebige Zeichenfolge, die auch in einer `_Function_class_` in der Anmerkung Deklaration mehrerer Funktionen wird. `_Called_from_function_class_` gibt einen Wert ungleich 0 \(null\) zurück, wenn die Funktion, die Nur analysiert wird, hinzugefügt wird, indem Sie `_Function_class_` verwenden, der den gleichen Wert `name` enthält; andernfalls gibt er null zurück.|  
|`_Check_return_`|Kommentiert einen Rückgabewert und Zustände, dass der Aufrufer ihn überprüfen soll.  Der Prüfer meldet einen Fehler, wenn die Funktion in einem ungültigen Kontext aufgerufen wird.|  
|`_Function_class_(name)`|Der Parameter `name` ist eine beliebige Zeichenfolge, die vom Benutzer festgelegt wird.  Es ist in einem Namespace, der von anderen Namespaces unterscheidet.  Eine Funktion, ein Funktionszeiger oder\-höchst ein usefully\-a werden als Funktionszeigertyp gehört einer oder mehreren Funktionsklassen festgelegt werden.|  
|`_Raises_SEH_exception_`|Kommentiert eine Funktion, die immer eine Quellcode für Handler \(SEH\)\- Ausnahme der strukturierten Ausnahmehandlers je nach `_When_` und `_On_failure_` Zuständen auslöst.  Weitere Informationen finden Sie unter [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Kommentiert eine Funktion, die sich optional SEH Ausnahme je nach `_When_` und `_On_failure_` Zuständen soll.|  
|`_Must_inspect_result_`|Kommentiert jeden Ausgabewert, einschließlich den Rückgabewert, Parameter und globalen Werten.  Der Analyzer meldet einen Fehler, wenn der Wert im Objekt mit Anmerkungen anschließend nicht überprüft wird. "Überprüfung" enthält, ob sie in einem bedingten Ausdruck verwendet wird, zu einem Ausgabeparameter oder global zugewiesen wird, oder wird als Parameter übergeben.  Für Rückgabewerte bedeutet `_Must_inspect_result_``_Check_return_`.|  
|`_Use_decl_annotations_`|Kann auf eine Funktionsdefinition \(auch als Funktionsrumpf\) anstelle der Liste von Anmerkungen im Header verwendet werden. Wenn `_Use_decl_annotations_` verwendet wird, sind die Anmerkungen, die in einer im Gültigkeitsbereich befindlichen Header für die gleiche Funktion werden, verwendet, als ob ihnen auch die Definition vorhanden sind, die die Anmerkungen `_Use_decl_annotations_` verfügt.|  
  
## Erfolg\/Fehler\-Anmerkungen  
 Eine Funktion kann fehlschlagen und wenn ja, unterscheiden sich die Ergebnisse unvollständig sein oder von den Ergebnissen, wenn die Funktion folgt.  Mit Anmerkungen in der folgenden Liste liefern Methoden, das Fehlerverhalten auszudrücken.  Um diese Anmerkungen zu verwenden, müssen Sie es ermöglichen den erfolgreichen Verlauf festzustellen; Daher ist eine Anmerkung `_Success_` erforderlich.  Beachten Sie, dass `NTSTATUS` und `HRESULT` bereits eine `_Success_` Anmerkung haben, in die sie erstellt wird; Wenn Sie jedoch der eigenen `_Success_` Anmerkung auf `NTSTATUS` oder `HRESULT` angeben, überschreibt dieser die integrierte Anmerkung.  
  
|Anmerkung|**Beschreibung**|  
|---------------|----------------------|  
|`_Always_(anno_list)`|Entspricht `anno_list _On_failure_(anno_list)`; das heißt, gelten die Anmerkungen in `anno_list`, dass die Funktion erfolgreich.|  
|`_On_failure_(anno_list)`|Um nur wenn auch `_Success_`, um verwendet wird Funktion\-jedes explizit zu kommentieren oder implizit von `_Return_type_success_` in einer Typdefinition verwendet werden.  Wenn die `_On_failure_` Anmerkung auf einem Funktionsparameter oder einem Rückgabewert vorhanden ist, verhält alle Anmerkungen in `anno_list` \(anno\), als wären sie als `_When_(!expr, anno)` codiert wurde, in dem `expr` der Parameter zur erforderlichen `_Success_` Anmerkung ist.  Dies bedeutet, dass die implizite Anwendung von `_Success_` auf alle Nachbedingungen nicht `_On_failure_` gilt.|  
|`_Return_type_success_(expr)`|Kann auf eine Typ angewendet werden.  Gibt an, dass alle Funktionen, die diesen Typ zurückgeben und nicht explizit `_Success_`, gekennzeichnet sind, als ob ihnen `_Success_(expr)` haben.  `_Return_type_success_` kann nicht auf eine Funktion oder einer Funktionszeiger\-typedef verwendet werden.|  
|`_Success_(expr)`|`expr` ist ein Ausdruck, der einen R\-Wert führt.  Wenn die `_Success_` Anmerkung in einer Funktionsdeklaration oder eine Definition vorhanden ist, verhält sich jede Anmerkung \(`anno`\) in der Funktion und in der Nachbedingung, als wären sie als `_When_(expr, anno)` codiert wurde.  Die Anmerkung ist `_Success_` nur auf eine Funktion, nicht auf den Parameter oder als Rückgabetyp verwendet werden.  Es kann eine `_Success_` Anmerkung für eine Funktion höchstens geben, und kann nicht in einem `_When_`, `_At_` oder `_Group_` sein.  Weitere Informationen finden Sie unter [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## Siehe auch  
 [Verwenden von SAL\-Anmerkungen zum Reduzieren von C\/C\+\+\-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)