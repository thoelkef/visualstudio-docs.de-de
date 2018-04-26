---
title: Referenz zu Visual Studio C++ Core Richtlinien Checker
ms.date: 03/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 09abcf8b1ece1360056a479df568db3a4e569ff1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="c-core-guidelines-checker-reference"></a>C++-Core-Richtlinien Überprüfungsprogramm Verweis

In diesem Abschnitt werden C++ Core Richtlinien Checker Warnungen aufgelistet. Informationen zur Codeanalyse finden Sie unter [/ analyze (Codeanalyse)](/cpp/build/reference/analyze-code-analysis) und [Schnellstart: Codeanalyse für C/C++-](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Einige Warnungen zu mehreren Gruppen gehören, und nicht alle Warnungen haben eine vollständige Referenz-Thema.

## <a name="ownerpointer-group"></a>OWNER_POINTER-Gruppe

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) eine Bereichsbezogene Objekt anstelle einer Heap zugewiesenen zurückgeben, wenn es sich um einen bewegungskonstruktor aufweist. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) zurücksetzen oder löschen Sie Sie explizit einen Besitzer\<T > Zeiger "%Variable%". Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) löschen Sie einen Besitzer nicht\<T >, die möglicherweise in einem ungültigen Zustand. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) keinen Besitzer zuweisen\<T >, die möglicherweise in gültigen Zustand. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) weisen einen unformatierten Zeiger auf einen Benutzer nicht\<T >. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) Objekte des festgelegten bevorzugen, keine Heap-belegen unnötig. Finden Sie unter [C++ Core Richtlinien R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) Symbol "Symbol %" wird nie Nullness getestet, es kann z. B. Not_null markiert werden. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "Symbol %" wurde nicht für Nullness auf alle Pfade getestet. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) der Typ des Ausdrucks "% Expr %" wird bereits gsl::not_null. Testen Sie es nicht für Nullness. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>RAW_POINTER-Gruppe

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) weisen Sie das Ergebnis eine Zuordnung oder ein Funktionsaufruf nicht mit dem Besitzer\<T > Rückgabewert in einen unformatierten Zeiger; verwenden Sie Besitzer\<T > stattdessen. Finden Sie unter [C++ Core Richtlinien I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) löschen Sie einen unformatierten Zeiger, der nicht der Besitzer ist nicht\<T >. Finden Sie unter [C++ Core Richtlinien I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   eine Bereichsbezogene Objekt anstelle einer Heap zugewiesenen zurückgeben, wenn es sich um einen bewegungskonstruktor aufweist. Finden Sie unter [C++ Core Richtlinien R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) malloc() und free() vermeiden, bevorzugen die Nothrow-Version des erstmals für löschen. Finden Sie unter [C++ Core Richtlinien r. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) vermeiden Sie Aufrufe, die neuen und explizit löschen, verwenden Sie std::make_unique\<T > stattdessen. Finden Sie unter [C++ Core Richtlinien r. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) Symbol "Symbol %" wird nie Nullness getestet, es kann z. B. Not_null markiert werden. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "Symbol %" wurde nicht für Nullness auf alle Pfade getestet. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) der Typ des Ausdrucks "% Expr %" wird bereits gsl::not_null. Testen Sie es nicht für Nullness. Finden Sie unter [C++ Core Richtlinien F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen die Spanne. Finden Sie unter [C++ Core Richtlinien Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Der Ausdruck "% Expr %": kein Zeiger Decay-Array. Finden Sie unter [C++ Core Richtlinien Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>UNIQUE_POINTER-Gruppe

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) der Parameter "% Parameter %" ist ein Verweis auf `const` eindeutige-Zeiger ist, verwenden Sie const T * oder const T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) der Parameter "% Parameter %" ist ein Verweis auf eindeutige Zeiger, und es ist nie zurückgesetzt oder neu zugewiesen, verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) verschieben, kopieren, neu zuweisen oder einen lokalen intelligenten Zeiger "% Symbol %" zurückgesetzt. Finden Sie unter [C++ Core Richtlinien R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) intelligenten Zeiger-Parameter "% Symbol %" wird verwendet, nur um eigenständige Zeiger zuzugreifen. Verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>SHARED_POINTER-Gruppe

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) verschieben, kopieren, neu zuweisen oder einen lokalen intelligenten Zeiger "% Symbol %" zurückgesetzt. Finden Sie unter [C++ Core Richtlinien R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) intelligenten Zeiger-Parameter "% Symbol %" wird verwendet, nur um eigenständige Zeiger zuzugreifen. Verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) Zeiger "Shared"-Parameter "% Symbol %" als Rvalue-Verweis übergeben wird. Stattdessen als Wert übergeben. Finden Sie unter [C++ Core Richtlinien R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) Zeiger "Shared"-Parameter "% Symbol %" wird als Verweis übergeben wird und nicht zurückgesetzt oder neu zugewiesen. Verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) Zeiger "Shared"-Parameter "% Symbol %" nicht kopiert oder verschoben wird. Verwenden Sie T * oder T & stattdessen. Finden Sie unter [C++ Core Richtlinien R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>DEKLARATION Gruppe

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) globale Initialisierer Aufruf einer nicht-Constexpr-Funktion "% Symbol %". Finden Sie unter [C++ Core Richtlinien I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) globale Initialisierer greift auf "extern" Objekt "% Symbol %". Finden Sie unter [C++ Core Richtlinien I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) unbenannte Objekte mit benutzerdefinierten Konstruktion und Zerstörung vermeiden. Finden Sie unter [ES.84: (versuchen Sie nicht,) deklarieren Sie eine lokale Variable ohne Namen](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Group-Klasse

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) , wenn Sie definieren, oder löschen alle Standardvorgang im Typ "% Symbol %", definieren, oder löschen sie alle. Finden Sie unter [C++ Core Richtlinien c. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) Funktion "% Symbol %" sollte mit "Override" markiert werden. Finden Sie unter [C.128: virtuelle Funktionen sollten genau einem der virtuellen, "Override", oder den abschließenden angeben](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) Funktion "% symbol_1 %" Blendet eine nicht virtuelle Funktion "% symbol_2 %". Finden Sie unter [C++ Core Richtlinien C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) Funktion "% Symbol %" sollten genau einem "virtual", "override" oder "Letzte" angeben. Finden Sie unter [C.128: virtuelle Funktionen sollten genau einem der virtuellen, "Override", oder den abschließenden angeben](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


[C26436 NEED_VIRTUAL_DTOR](C26436.md) der Typ "% Symbol %" mit einer virtuellen Funktion benötigt entweder öffentliche virtuelle oder geschützte nicht virtuellen Destruktor. Finden Sie unter [C++ Core Richtlinien C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) überschreiben Destruktor sollten nicht verwenden, explizite "Override" oder "virtual" Spezifizierer. Finden Sie unter [C.128: virtuelle Funktionen sollten genau einem der virtuellen, "Override", oder den abschließenden angeben](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>Typ-Gruppe

[C26437 DONT_SLICE](C26437.md) nicht Slices aufteilen. Finden Sie unter [C++ Core Richtlinien ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Stil-Gruppe

[C26438 NO_GOTO](C26438.md) vermeiden `goto`. Finden Sie unter [C++ Core Richtlinien ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Funktionsgruppe

[C26439 SPECIAL_NOEXCEPT](C26439.md) dieser Art von Funktion möglicherweise nicht ausgelöst. Deklarieren Sie es `noexcept`. Finden Sie unter [C++ Core Richtlinien F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) kann die Funktion "% Symbol %" deklariert werden `noexcept`. Finden Sie unter [C++ Core Richtlinien F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) die Funktionsdeklaration **Noexcept** jedoch Ruft eine Funktion, die möglicherweise Ausnahmen ausgelöst.
Finden Sie unter [C++ Core Richtlinien: F.6: Wenn die Funktion nicht ausgelöst werden kann, deklarieren Sie es Noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>CONCURRENCY-Gruppe

[C26441 NO_UNNAMED_GUARDS](C26441.md) Guard Objekte müssen benannt sein. Finden Sie unter [C++ Core Richtlinien cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>CONST-Gruppe

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) der Verweisargument "% Argument %" für die Funktion "% Funktion %" kann z. B. markiert werden `const`. Finden Sie unter [C++ Core Richtlinien con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): die Zeigerargument "% Argument %" für die Funktion "% Funktion %" kann z. B. ein Zeiger auf markiert werden `const`. Finden Sie unter [C++ Core Richtlinien con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) der Wert auf "%Variable%" zeigt nur einmal zugeordnet ist, markieren Sie es als Zeiger auf `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) die Elemente des Arrays "% Array %" werden nur einmal zugewiesen Markierung Elemente `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) die Werte, die auf die Elemente des Arrays "% Array %" werden nur einmal zugewiesen Markierung Elemente als Zeiger auf `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) die Variable "%-Variable %" wird nur einmal zugewiesen ist, markieren Sie sie als `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) kann diese Funktion "%-Funktion" gekennzeichnet werden `constexpr` Wenn kompilierzeitauswertung gewünscht ist. Finden Sie unter [C++ Core Richtlinien F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) können Sie diese Funktion Aufruf "%-Funktion" `constexpr` Wenn kompilierzeitauswertung gewünscht ist. Finden Sie unter [C++ Core Richtlinien con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Typ-Gruppe

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) verwenden Sie keine `const_cast` umwandeln `const`. `const_cast` ist nicht erforderlich. Durch diese Konvertierung wird nicht Constness oder Flüchtigkeit entfernt wird. Finden Sie unter [C++ Core Richtlinien Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) verwenden Sie keine `static_cast` Umwandlungen. Eine Umwandlung in einen polymorphen Typ sollten Dynamic_cast verwenden. Finden Sie unter [C++ Core Richtlinien Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) verwenden Sie keine `reinterpret_cast`. Können Sie eine Typumwandlung von "void" * `static_cast`. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) verwenden Sie kein `static_cast` für arithmetische Konvertierungen. Verwenden Sie Initialisierung mit geschweiften Klammern, gsl::narrow_cast oder gsl::narow. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) nicht eine Umwandlung zwischen Zeigertypen, in denen der Quelltyp und der Zieltyp identisch sind. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) nicht eine Umwandlung zwischen Zeigertypen, wenn die Konvertierung implizit sein kann. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) verwenden Sie keine Funktionsstil C#-Umwandlungen. Finden Sie unter [C++ Core Richtlinien ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) verwenden Sie keine `reinterpret_cast`. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) verwenden Sie keine `static_cast` Umwandlungen. Finden Sie unter [C++ Core Richtlinien Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) verwenden Sie keine `const_cast` umwandeln `const`. Finden Sie unter [C++ Core Richtlinien Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) keine C-stilartige Umwandlungen verwenden. Finden Sie unter [C++ Core Richtlinien Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) Variable "%-Variable %" wurde nicht initialisiert. Immer werden Sie ein Objekt initialisiert. Finden Sie unter [C++ Core Richtlinien Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) Variable "%-Variable %" wurde nicht initialisiert. Initialisieren Sie immer einer Membervariablen gespeichert. Finden Sie unter [C++ Core Richtlinien Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Gruppe von Grenzen

[C26446 USE_GSL_AT](c26446.md) bevorzugen `gsl::at()` anstelle von ungeprüften subscript-Operators. Finden Sie unter [C++ Core Richtlinien: Bounds.4: Verwenden Sie keine Standard-Library-Funktionen und Typen, die nicht geprüfte Grenzen sind](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen die Spanne. Finden Sie unter [C++ Core Richtlinien Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) index nur für Arrays mit konstanten Ausdrücken. Finden Sie unter [C++ Core Richtlinien Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) Wert "% Wert" liegt außerhalb des Bereichs (0, gebundenen %) der Variablen "%Variable%". Index nur Konstante Ausdrücke, die innerhalb der Grenzen des Arrays mit Arrays. Finden Sie unter [C++ Core Richtlinien Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) Ausdruck "% Expr %": kein Zeiger Decay-Array. Finden Sie unter [C++ Core Richtlinien Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL-Gruppe

[C26445 NO_SPAN_REF](c26445.md) einen Verweis auf `gsl::span` oder `std::string_view` kann darauf hinweisen, dass ein Lebensdauerproblem.
Finden Sie unter [C++ Core Richtlinien GSL.view: Ansichten](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) bevorzugen `gsl::at()` anstelle von ungeprüften subscript-Operators. Finden Sie unter [C++ Core Richtlinien: Bounds.4: Verwenden Sie keine Standard-Library-Funktionen und Typen, die nicht geprüfte Grenzen sind](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY ](c26448.md) verwenden Sie ggf. `gsl::finally` endgültige Aktion durchgeführt werden. Finden Sie unter [C++ Core Richtlinien: GSL.util: Hilfsprogramme](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` oder `std::string_view` erstellt ein temporäres Kennwort ist ungültig Wenn temporären ungültig ist. Finden Sie unter [C++ Core Richtlinien: GSL.view: Ansichten](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).


## <a name="deprecated-warnings"></a>Veraltete Warnungen

Die folgenden Warnungen sind in einer frühen experimentellen Regelsatz des Überprüfungsprogramms Richtlinien "Core" vorhanden, jedoch sind jetzt veraltet und können ignoriert werden. Die Warnungen werden durch Warnungen aus der Liste oben ersetzt.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Siehe auch
[Verwenden die C++-Core-Richtlinien-Prüfer](using-the-cpp-core-guidelines-checkers.md)
