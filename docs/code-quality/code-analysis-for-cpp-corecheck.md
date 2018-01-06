---
title: "Visual Studio C++ Core Richtlinien Überprüfungsprogramm Verweis | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c17574722804409b58d648af66b255888e945db2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="c-core-guidelines-checker-reference"></a>C++-Core-Richtlinien Überprüfungsprogramm Verweis
In diesem Abschnitt werden C++ Core Richtlinien Checker Warnungen aufgelistet. Informationen zur Codeanalyse finden Sie unter [/ analyze (Codeanalyse)](/cpp/build/reference/analyze-code-analysis) und [Schnellstart: Codeanalyse für C/C++-](../code-quality/quick-start-code-analysis-for-c-cpp.md).  
  
**Hinweis**: Einige Warnungen zu mehreren Gruppen gehören, und nicht alle Warnungen haben eine Referenzthema.

## <a name="ownerpointer-group"></a>OWNER_POINTER-Gruppe

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  
  Zurückgeben Sie eine Bereichsbezogene Objekt anstelle einer Heap zugewiesene, wenn es sich um einen bewegungskonstruktor aufweist. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
     
[C26403 RESET_OR_DELETE_OWNER](C26403.md)  
  Zurücksetzen oder löschen Sie Sie explizit einen Besitzer\<T > Zeiger "%Variable%". Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
     
[C26404 DONT_DELETE_INVALID](C26404.md)  
  Löschen Sie einen Besitzer nicht\<T > was u. u. nicht in einem ungültigen Zustand. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)  
  Weisen Sie einem Besitzer nicht\<T > was u. u. nicht in gültigen Zustand. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)  
  Weisen Sie einen unformatierten Zeiger nicht auf einen Benutzer\<T >. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
  
[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)  
  Bevorzugen Sie Objekte des festgelegten, belegen Sie keine Heap-unnötig. Finden Sie unter [C++ Core Richtlinien R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  

[C26429 USE_NOTNULL](C26429.md)  
  Symbol "% Symbol %" wird nie Nullness getestet, es kann z. B. Not_null markiert werden. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  Symbol "% Symbol %" wird nicht für Nullness auf alle Pfade getestet. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  Der Typ des Ausdrucks "% Expr %" wird bereits gsl::not_null. Testen Sie es nicht für Nullness. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

## <a name="rawpointer-group"></a>RAW_POINTER-Gruppe
 
[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)  
Weisen Sie das Ergebnis eine Zuordnung oder ein Funktionsaufruf nicht mit dem Besitzer\<T > Wert an einen unformatierten Zeiger zurückgeben, verwenden Sie Besitzer<T> stattdessen. Finden Sie unter [C++ Core Richtlinien I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26401 DONT_DELETE_NON_OWNER](c26401.md)  
Löschen Sie einen unformatierten Zeiger, der nicht der Besitzer ist nicht\<T >. Finden Sie unter [C++ Core Richtlinien I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   eine Bereichsbezogene Objekt anstelle einer Heap zugewiesenen zurückgeben, wenn es sich um einen bewegungskonstruktor aufweist. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
 
[C26408 NO_MALLOC_FREE](C26408.md)  
  Vermeiden Sie malloc() und free(), bevorzugen Sie die Nothrow-Version des erstmals für löschen. Finden Sie unter [C++ Core Richtlinien r. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).  
  
[C26409 NO_NEW_DELETE](C26409.md)  
  Vermeiden Sie Aufrufe, die neuen und explizit löschen, verwenden Sie std::make_unique\<T > stattdessen. Finden Sie unter [C++ Core Richtlinien r. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).  

[C26429 USE_NOTNULL](C26429.md)  
  Symbol "% Symbol %" wird nie Nullness getestet, es kann z. B. Not_null markiert werden. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  Symbol "% Symbol %" wird nicht für Nullness auf alle Pfade getestet. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  Der Typ des Ausdrucks "% Expr %" wird bereits gsl::not_null. Testen Sie es nicht für Nullness. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26481 NO_POINTER_ARITHMETIC](C26481.md)  
  Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen die Spanne. Finden Sie unter [C++ Core Richtlinien Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  Der Ausdruck "% Expr %": kein Zeiger Decay-Array. Finden Sie unter [C++ Core Richtlinien Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

## <a name="uniquepointer-group"></a>UNIQUE_POINTER-Gruppe
  
[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)  
  Der Parameter "% Parameter %" ist ein Verweis auf `const` eindeutige-Zeiger ist, verwenden Sie const T * oder const T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).  
     
[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)  
  Der Parameter "% Parameter %" ist ein Verweis auf eindeutige Zeiger, und es ist nie zurückgesetzt oder neu zugewiesen, verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).  
     
[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Verschieben, kopieren, neu zuweisen, oder einen lokalen intelligenten Zeiger "% Symbol %" zurückgesetzt. Finden Sie unter [C++ Core Richtlinien R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Intelligenter Zeiger Parameter "% Symbol %" wird nur für den Zugriff enthalten Zeiger verwendet. Verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  

## <a name="sharedpointer-group"></a>SHARED_POINTER-Gruppe

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Verschieben, kopieren, neu zuweisen, oder einen lokalen intelligenten Zeiger "% Symbol %" zurückgesetzt. Finden Sie unter [C++ Core Richtlinien R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Intelligenter Zeiger Parameter "% Symbol %" wird nur für den Zugriff enthalten Zeiger verwendet. Verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  
    
[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)  
  Für den gemeinsamen Zeiger-Parameter "% Symbol %" wird als Rvalue-Verweis übergeben. Stattdessen als Wert übergeben. Finden Sie unter [C++ Core Richtlinien R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).  
  
[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)  
  Für den gemeinsamen Zeiger-Parameter "% Symbol %" wird als Verweis übergeben wird und nicht zurückgesetzt oder neu zugewiesen. Verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).  
  
[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)  
  Für den gemeinsamen Zeiger-Parameter "% Symbol %" wird nicht kopiert oder verschoben. Verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).  

## <a name="declaration-group"></a>DEKLARATION Gruppe
    
[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)  
  Globale Initialisierer Aufruf einer nicht-Constexpr-Funktion "% Symbol %". Finden Sie unter [C++ Core Richtlinien I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)  
  Globale Initialisierer greift auf "extern" Objekt "% Symbol %". Finden Sie unter [C++ Core Richtlinien I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
## <a name="class-group"></a>Group-Klasse
    
[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)  
  Wenn Sie definieren, oder löschen alle Standardvorgang im Typ "% Symbol %", definieren Sie, oder löschen sie alle. Finden Sie unter [C++ Core Richtlinien c. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).  
  
[C26434 DONT_HIDE_METHODS](C26434.md)  
  Funktion "% symbol_1 %" Blendet eine nicht virtuelle Funktion "% symbol_2 %" aus. Finden Sie unter [C++ Core Richtlinien C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).  
  
[C26436 NEED_VIRTUAL_DTOR](C26436.md)  
  Der Typ "% Symbol %" mit einer virtuellen Funktion benötigt entweder öffentliche virtuelle oder geschützte nicht virtuellen Destruktor. Finden Sie unter [C++ Core Richtlinien C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).  

## <a name="type-group"></a>Typ-Gruppe
    
[C26437 DONT_SLICE](C26437.md)  
  Nicht unterteilen. Finden Sie unter [C++ Core Richtlinien ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).  

## <a name="style-group"></a>Stil-Gruppe  
[C26438 NO_GOTO](C26438.md)  
  Vermeiden Sie `goto`. Finden Sie unter [C++ Core Richtlinien ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).  
  
## <a name="function-group"></a>Funktionsgruppe
    
[C26439 SPECIAL_NOEXCEPT](C26439.md)  
  Diese Art von Funktion möglicherweise nicht ausgelöst. Deklarieren Sie es `noexcept`. Finden Sie unter [C++ Core Richtlinien F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  
  
[C26440 DECLARE_NOEXCEPT](C26440.md)  
  Funktion "% Symbol %" deklariert werden kann `noexcept`. Finden Sie unter [C++ Core Richtlinien F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  

## <a name="concurrency-group"></a>CONCURRENCY-Gruppe
    
[C26441 NO_UNNAMED_GUARDS](C26441.md)  
 Guard Objekte müssen benannt werden. Finden Sie unter [C++ Core Richtlinien cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).  

## <a name="const-group"></a>CONST-Gruppe
    
C26460 USE_CONST_REFERENCE_ARGUMENTS:  
  Die Verweisargument "% Argument %" für die Funktion "% Funktion %" kann z. B. markiert werden `const`. Finden Sie unter [C++ Core Richtlinien con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26461 USE_CONST_POINTER_ARGUMENTS: die Zeigerargument "% Argument %" für die Funktion "% Funktion %" kann z. B. ein Zeiger auf markiert werden `const`. Finden Sie unter [C++ Core Richtlinien con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26462 USE_CONST_POINTER_FOR_VARIABLE:  
  Der Wert auf "%Variable%" zeigt nur einmal zugeordnet ist, markieren Sie es als Zeiger auf `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26463 USE_CONST_FOR_ELEMENTS:  
  Die Elemente des Arrays "% Array %" werden nur einmal zugewiesen Markierung Elemente `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26464 USE_CONST_POINTER_FOR_ELEMENTS:  
  Die Werte, die auf die Elemente des Arrays "% Array %" werden nur einmal zugewiesen Markierung Elemente als Zeiger auf `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  

C26496 USE_CONST_FOR_VARIABLE:  
  Die Variable "%-Variable %" wird nur einmal zugewiesen ist, markieren Sie sie als `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26497 USE_CONSTEXPR_FOR_FUNCTION:  
  Kann diese Funktion "%-Funktion" gekennzeichnet werden `constexpr` Wenn kompilierzeitauswertung gewünscht ist. Finden Sie unter [C++ Core Richtlinien F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).  
  
C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL:  
  Diese Funktion Aufruf "%-Funktion" können `constexpr` Wenn kompilierzeitauswertung gewünscht ist. Finden Sie unter [C++ Core Richtlinien con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).  

## <a name="type-group"></a>Typ-Gruppe
C26465 NO_CONST_CAST_UNNECESSARY:  
  Verwenden Sie keine `const_cast` umwandeln `const`. `const_cast`ist nicht erforderlich. Durch diese Konvertierung wird nicht Constness oder Flüchtigkeit entfernt wird. Finden Sie unter [C++ Core Richtlinien Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).  
  
C26466 NO_STATIC_DOWNCAST_POLYMORPHIC:  
  Verwenden Sie keine `static_cast` Umwandlungen. Eine Umwandlung in einen polymorphen Typ sollten Dynamic_cast verwenden. Finden Sie unter [C++ Core Richtlinien Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).  
  
C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR:  
  Verwenden Sie keine `reinterpret_cast`. Können Sie eine Typumwandlung von "void" * `static_cast`. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)  
  Verwenden Sie kein `static_cast` für arithmetische Konvertierungen. Verwenden Sie die Initialisierung mit geschweiften Klammern, gsl::narrow_cast oder gsl::narow. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26473 NO_IDENTITY_CAST](C26473.md)  
  Keine Umwandlung zwischen Zeigertypen, in dem die Quell- und der Zieltyp identisch sind. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26474 NO_IMPLICIT_CAST](C26474.md)  
  Keine Umwandlung zwischen Zeigertypen, wenn die Konvertierung implizit sein kann. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)  
  Verwenden Sie nicht die Funktion Format C#-Umwandlungen. Finden Sie unter [C++ Core Richtlinien ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).  
     
C26490 NO_REINTERPRET_CAST:  
  Verwenden Sie keine `reinterpret_cast`. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26491 NO_STATIC_DOWNCAST:  
  Verwenden Sie keine `static_cast` Umwandlungen. Finden Sie unter [C++ Core Richtlinien Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26492 NO_CONST_CAST:  
  Verwenden Sie keine `const_cast` umwandeln `const`. Finden Sie unter [C++ Core Richtlinien Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
    
C26493 NO_CSTYLE_CAST:  
  Verwenden Sie keine C-stilartige Umwandlungen. Finden Sie unter [C++ Core Richtlinien Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type). 
     
C26494 VAR_USE_BEFORE_INIT:  
  Die Variable "%-Variable %" wurde nicht initialisiert. Immer werden Sie ein Objekt initialisiert. Finden Sie unter [C++ Core Richtlinien Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26495 MEMBER_UNINIT:  
  Die Variable "%-Variable %" wurde nicht initialisiert. Initialisieren Sie immer einer Membervariablen gespeichert. Finden Sie unter [C++ Core Richtlinien Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
## <a name="bounds-group"></a>Gruppe von Grenzen

[C26481 NO_POINTER_ARITHMETIC](C26481.md)   
  Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen die Spanne. Finden Sie unter [C++ Core Richtlinien Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26482 NO_DYNAMIC_ARRAY_INDEXING:  
  Index nur Konstante Ausdrücke mit Arrays. Finden Sie unter [C++ Core Richtlinien Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26483 STATIC_INDEX_OUT_OF_RANGE:  
  Wert "% Wert" liegt außerhalb des Bereichs (0, gebundenen %) der Variablen "%Variable%". Index nur Konstante Ausdrücke, die innerhalb der Grenzen des Arrays mit Arrays. Finden Sie unter [C++ Core Richtlinien Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  Der Ausdruck "% Expr %": kein Zeiger Decay-Array. Finden Sie unter [C++ Core Richtlinien Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
## <a name="see-also"></a>Siehe auch  
[Verwenden die C++-Core-Richtlinien-Prüfer](using-the-cpp-core-guidelines-checkers.md)
