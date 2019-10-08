---
title: C++ Core Guidelines Überprüfungsprogramm Verweis
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: fc6c7c1dbc5009129e9e793f3b8eea1f7927b2bb
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018449"
---
# <a name="c-core-guidelines-checker-reference"></a>C++ Core Guidelines Überprüfungsprogramm Verweis

Dieser Abschnitt listet die Warnungen für C++ Core Richtlinien aus. Weitere Informationen zur Code Analyse finden Sie unter [/analyze (Code Analyse)](/cpp/build/reference/analyze-code-analysis) und [schnell Start: Code Analyse für C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Einige Warnungen zu mehr als eine Gruppe gehören, und nicht alle Warnungen haben eine vollständige Referenz-Thema.

## <a name="owner_pointer-group"></a>OWNER_POINTER-Gruppe

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) ein bereichsbezogenes Objekt anstelle eines vom Heap zugewiesenen Objekts zurückgeben, wenn sie einen bewegungskonstruktor verfügt. Finden Sie unter [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) zurücksetzen oder explizit löschen einen Besitzer\<T > "% Variable%"-Zeiger. Finden Sie unter [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) löschen Sie einen Besitzer nicht\<T >, die möglicherweise in einem ungültigen Zustand. Finden Sie unter [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) weisen Sie einem Besitzer nicht\<T >, die möglicherweise im ungültigen Zustand. Finden Sie unter [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) weisen Sie keinen rohzeiger zu Besitzer\<T >. Finden Sie unter [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) Bereichsbezogene Objekte bevorzugen, nicht unnötig mit Heap zuordnen. Finden Sie unter [C++ Core Guidelines 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) Symbol "% Symbol %" wird nie auf nullwertigkeit getestet, es kann als Not_null gekennzeichnet werden. Finden Sie unter [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "% Symbol %" wurde nicht in allen Pfaden nullwertigkeit getestet. Finden Sie unter [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) der Typ des Ausdrucks "% Expr %" ist bereits gsl::not_null. Testen sie nicht auf nullwertigkeit. Finden Sie unter [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>RAW_POINTER-Gruppe

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) weisen nicht das Ergebnis einer Zuteilung oder eines Funktionsaufrufs mit einem Besitzer\<T >-Rückgabewert in ein unformatierter Zeiger; verwenden Sie Besitzer\<T > stattdessen. Finden Sie unter [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) löschen Sie einen unformatierten Zeiger, der nicht der Besitzer ist nicht\<T >. Finden Sie unter [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   ein bereichsbezogenes Objekt anstelle eines vom Heap zugewiesenen Objekts zurückgeben, wenn sie einen bewegungskonstruktor verfügt. Finden Sie unter [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) zu vermeiden, malloc() und free(), bevorzugen Sie die Nothrow-Version des new "mit" löschen. Finden Sie unter [C++ Core Guidelines r. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) vermeiden Sie Aufrufe, die neuen und explizit löschen, verwenden Sie Std:: make_unique\<T > stattdessen. Finden Sie unter [C++ Core Guidelines r. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) Symbol "% Symbol %" wird nie auf nullwertigkeit getestet, es kann als Not_null gekennzeichnet werden. Finden Sie unter [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "% Symbol %" wurde nicht in allen Pfaden nullwertigkeit getestet. Finden Sie unter [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) der Typ des Ausdrucks "% Expr %" ist bereits gsl::not_null. Testen sie nicht auf nullwertigkeit. Finden Sie unter [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen die Spanne. Finden Sie unter [C++ Core Richtlinien Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Ausdruck "% expr%": Kein Array zu Zeiger Verfall. Finden Sie unter [C++ Core Richtlinien Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>UNIQUE_POINTER-Gruppe

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) der Parameter "% Parameter %" ist ein Verweis auf `const` eindeutige Zeiger ist, verwenden Sie const T * "oder" const T & stattdessen. Finden Sie unter [C++ Core Guidelines 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) der Parameter "% Parameter %" ist ein Verweis auf einen eindeutigen Zeiger und wird nie neu zugeordnet oder zurückgesetzt, verwenden Sie T * "oder" T & stattdessen. Finden Sie unter [C++ Core Guidelines 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) verschieben, kopieren, neu zuweisen oder einen lokalen intelligenten Zeiger "% Symbol %" zurücksetzen. Finden Sie unter [C++ Core Guidelines 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) Parameter für intelligente Zeiger "% Symbol %" wird verwendet, nur um enthaltenen Zeiger zuzugreifen. Verwenden von T * "oder" T & stattdessen. Finden Sie unter [C++ Core Guidelines 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>SHARED_POINTER-Gruppe

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) verschieben, kopieren, neu zuweisen oder einen lokalen intelligenten Zeiger "% Symbol %" zurücksetzen. Finden Sie unter [C++ Core Guidelines 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) Parameter für intelligente Zeiger "% Symbol %" wird verwendet, nur um enthaltenen Zeiger zuzugreifen. Verwenden von T * "oder" T & stattdessen. Finden Sie unter [C++ Core Guidelines 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) Zeiger Shared-Parameter "% Symbol %" als Rvalue-Verweis übergeben wird. Stattdessen als Wert übergeben. Finden Sie unter [C++ Core Guidelines 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) Zeiger Shared-Parameter "% Symbol %" wird als Verweis übergeben wird und nicht zurückgesetzt oder neu zugewiesen. Verwenden von T * "oder" T & stattdessen. Finden Sie unter [C++ Core Guidelines 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) Zeiger Shared-Parameter "% Symbol %" nicht kopiert oder verschoben wird. Verwenden von T * "oder" T & stattdessen. Finden Sie unter [C++ Core Guidelines 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Gruppe der DEKLARATION

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) der globale Initialisierer Ruft eine nicht-Constexpr-Funktion "% Symbol %". Finden Sie unter [C++ Core Guidelines 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) globale Initialisierer greift auf "extern" Objekt "% Symbol %". Finden Sie unter [C++ Core Guidelines 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) vermeiden Sie unbenannte Objekte mit benutzerdefinierter Konstruktion und Zerstörung. Weitere Informationen finden Sie unter [es. 84: Nicht (versuchen Sie es), eine lokale Variable ohne Namen @ no__t-0 zu deklarieren.

## <a name="class-group"></a>Gruppe der-Klasse

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) , wenn Sie definieren oder Löschen einen Standardvorgang in den Typ "% Symbol %", definieren oder löschen sie alle. Finden Sie unter [C++ Core Guidelines c. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) Funktion "% Symbol %" sollte mit "Override" markiert werden. Weitere Informationen finden Sie unter [C. 128: Virtuelle Funktionen sollten genau eine von Virtual, override oder Final @ no__t-0 angeben.

[C26434 DONT_HIDE_METHODS](C26434.md) die Funktion "% symbol_1 %" Blendet eine nicht virtuelle Funktion "% symbol_2 %". Finden Sie unter [C++ Core Guidelines 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) Funktion "% Symbol %" muss genau eines der "virtual", "override" oder "final" angeben. Weitere Informationen finden Sie unter [C. 128: Virtuelle Funktionen sollten genau eine von Virtual, override oder Final @ no__t-0 angeben.

[C26436 NEED_VIRTUAL_DTOR](C26436.md) der Typ "% Symbol %" mit einer virtuellen Funktion benötigt entweder öffentlichen virtuellen oder einen geschützten nicht virtuellen Destruktor. Finden Sie unter [C++ Core Guidelines 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) Außerkraftsetzen Destruktor sollten nicht verwenden, explizite 'Override' oder 'virtual'-Spezifizierer. Weitere Informationen finden Sie unter [C. 128: Virtuelle Funktionen sollten genau eine von Virtual, override oder Final @ no__t-0 angeben.

## <a name="type-group"></a>Typ-Gruppe

[C26437 DONT_SLICE](C26437.md) segmentieren Sie nicht. Finden Sie unter [C++ Core Guidelines 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>STYLE-Gruppe

[C26438 NO_GOTO](C26438.md) vermeiden `goto`. Finden Sie unter [C++ Core Guidelines 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Funktionsgruppe

[C26439 SPECIAL_NOEXCEPT](C26439.md) diese Art von Funktion möglicherweise nicht auslösen. Deklarieren sie `noexcept`. Finden Sie unter [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) Funktion "% Symbol %" deklariert werden `noexcept`. Finden Sie unter [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) die Funktion wird deklariert, **"noexcept"** aber Ruft eine Funktion, die Ausnahmen auslösen kann.
Weitere Informationen finden SieC++ unter [-Kern Richtlinien:  F. 6: Wenn die Funktion möglicherweise keine Ausnahme auslöst, deklarieren Sie Sie mit dem Wert @ no__t-0.

## <a name="concurrency-group"></a>CONCURRENCY-Gruppe

[C26441 NO_UNNAMED_GUARDS](C26441.md) Guard-Objekte müssen benannt werden. Finden Sie unter [C++ Core Richtlinien cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>CONST-Gruppe

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) Verweisargument "% Argument %" für Funktion "% Funktion %" kann markiert werden, als `const`. Finden Sie unter [C++ Core Richtlinien con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): Das Zeigerargument "% Argument%" für die Funktion "% Function%" kann als Zeiger auf `const` gekennzeichnet werden. Finden Sie unter [C++ Core Richtlinien con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) der Wert, der auf die von "% Variable%" gezeigt wird nur einmal zugewiesen, markieren Sie sie als Zeiger auf `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) die Elemente des Arrays "% Array %" werden nur einmal aus, markieren Sie die Elemente zugewiesen `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) die Werte, die auf Elemente des Arrays "% Array %" zeigt nur einmal aus, markieren Sie die Elemente als Zeiger auf zugewiesen `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) die Variable "% Variable%" wird nur einmal zugewiesen, markieren Sie sie als `const`. Finden Sie unter [C++ Core Richtlinien con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) konnte diese Funktion Funktion % markiert werden `constexpr` kompilierzeitauswertung gewünscht ist. Finden Sie unter [C++ Core Guidelines F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) kann von dieser Funktion Aufruf Funktion % `constexpr` kompilierzeitauswertung gewünscht ist. Finden Sie unter [C++ Core Richtlinien con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Typ-Gruppe

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) verwenden Sie keine `const_cast` zum Umwandeln von `const`. `const_cast` ist nicht erforderlich. Constness oder Volatilität wird durch diese Konvertierung nicht entfernt werden. Weitere Informationen finden Sie in den [C++ Core-Richtlinien Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) verwenden Sie keine `static_cast` Typumwandlungen. Eine Umwandlung in einen polymorphen Typ sollten Dynamic_cast verwenden. Finden Sie unter [C++ Core Richtlinien Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) verwenden Sie keine `reinterpret_cast`. Eine Umwandlung von "void" * können `static_cast`. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) verwenden Sie keine `static_cast` für arithmetische Konvertierungen. Verwenden Sie die Initialisierung mit geschweiften Klammern, gsl::narrow_cast oder gsl::narow. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) keine Umwandlung zwischen Zeigertypen durch, in denen der Quelltyp und des Zieltyps entsprechen. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) keine Umwandlung zwischen Zeigertypen, wenn die Konvertierung implizit sein kann. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) verwenden Sie keine Funktionsstil C#-Umwandlungen. Finden Sie unter [C++ Core Guidelines ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) verwenden Sie keine `reinterpret_cast`. Finden Sie unter [C++ Core Richtlinien Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) verwenden Sie keine `static_cast` Typumwandlungen. Finden Sie unter [C++ Core Richtlinien Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) verwenden Sie keine `const_cast` zum Umwandeln von `const`. Weitere Informationen finden Sie in den [C++ Core-Richtlinien Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) verwenden Sie keine C-stilartige Umwandlungen. Finden Sie unter [C++ Core Richtlinien Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) Variable "% Variable%" ist nicht initialisiert. Ein Objekt immer initialisiert werden. Finden Sie unter [C++ Core Richtlinien Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) Variable "% Variable%" ist nicht initialisiert. Initialisieren Sie eine Membervariable immer. Finden Sie unter [C++ Core Richtlinien Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Gruppe von Grenzen

[C26446 USE_GSL_AT](c26446.md) bevorzugen `gsl::at()` anstelle von ungeprüften subscript-Operator. Weitere Informationen finden SieC++ unter [-Kern Richtlinien:  Bounds. 4: Verwenden Sie keine Standard Bibliotheksfunktionen und-Typen, für die keine Begrenzungen aktiviert sind @ no__t-0.

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen die Spanne. Finden Sie unter [Bounds.1 für C++-Core-Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) index nur für Arrays mithilfe konstanter Ausdrücke. Finden Sie unter [Bounds.2 für C++-Core-Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) Wert Wert %value% ist außerhalb des gültigen Bereichs (0, gebundenen %) der Variablen "% Variable%". Index nur mithilfe konstanter Ausdrücke, die innerhalb der Grenzen des Arrays sind Arrays. Finden Sie unter [Bounds.2 für C++-Core-Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) Ausdruck "% expr%": Kein Array zu Zeiger Verfall. Finden Sie unter [Bounds.3 für C++-Core-Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL-Gruppe

[C26445 NO_SPAN_REF](c26445.md) einen Verweis auf `gsl::span` oder `std::string_view` kann darauf hinweisen, dass ein Lebensdauerproblem.
Weitere Informationen finden SieC++ unter [-Kern Richtlinien GSL. View: Sichten @ no__t-0

[C26446 USE_GSL_AT](c26446.md) bevorzugen `gsl::at()` anstelle von ungeprüften subscript-Operator. Weitere Informationen finden SieC++ unter [-Kern Richtlinien:  Bounds. 4: Verwenden Sie keine Standard Bibliotheksfunktionen und-Typen, für die keine Begrenzungen aktiviert sind @ no__t-0.

[C26448 USE_GSL_FINALLY](c26448.md) Verwenden Sie `gsl::finally`, wenn die endgültige Aktion beabsichtigt ist. Weitere Informationen finden SieC++ unter [-Kern Richtlinien:  GSL.util: Hilfsprogramme @ no__t-0.

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` oder `std::string_view` erstellt aus einer temporären werden ungültige bei temporären für ungültig erklärt. Weitere Informationen finden SieC++ unter [-Kern Richtlinien: GSL.view: Views @ no__t-0.

## <a name="deprecated-warnings"></a>Veraltete Warnungen

Die folgenden Warnungen in einer frühen experimentelle Regelsatz von Core Richtlinien Checker, vorhanden sind, aber sind jetzt veraltet und können ignoriert werden. Die Warnungen werden von Warnungen aus der Liste oben ersetzt.

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
[Verwenden der C++-Core-Richtlinienprüfungen](using-the-cpp-core-guidelines-checkers.md)
