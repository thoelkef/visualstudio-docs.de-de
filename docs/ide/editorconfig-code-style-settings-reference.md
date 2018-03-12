---
title: "Einstellungen für die .NET-Codierungskonventionen für „EditorConfig“ in Visual Studio | Microsoft-Dokumentation"
ms.date: 02/28/2018
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language conventions [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ac6c9e79e659a7f7d152541bc5a2d7deea694086
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Einstellungen für die .NET-Codierungskonventionen für „EditorConfig“

In Visual Studio 2017 können Sie das Codeformat in Ihrer Codebasis mit einer [EditorConfig](../ide/create-portable-custom-editor-options.md)-Datei definieren und verwalten. „EditorConfig“ enthält mehrere wesentliche Formatierungseigenschaften, wie z.B. `indent_style` und `indent_size`. In Visual Studio können Einstellungen für die .NET-Codierungskonventionen auch mit einer „EditorConfig“-Datei konfiguriert werden. Mit „EditorConfig“-Dateien können Sie einzelne .NET-Codierungskonventionen aktivieren oder deaktivieren und konfigurieren, inwieweit die Konvention über einen Schweregrad erzwungen werden soll. Weitere Informationen zur Verwendung „EditorConfig“ zum Erzwingen der Konsistenz in Ihrer Codebasis finden Sie in unter [Optionen zum Erstellen eines portablen benutzerdefinierten Editors](../ide/create-portable-custom-editor-options.md). Sie können sich auch die [.editorconfig-Datei der .NET Compiler Platform](https://github.com/dotnet/roslyn/blob/master/.editorconfig) als Beispiel ansehen.

Es gibt drei unterstützte Kategorien für .NET-Codierungskonventionen:

- [ Sprachkonventionen](#language-conventions)

   Regeln für die Sprache C# oder die Sprache Visual Basic. Beispielsweise können Sie Regeln hinsichtlich der Verwendung von `var` oder explizite Typen angeben, wenn Sie Variablen definieren oder Ausdruckskörpermember bevorzugen.

- [Formatierungskonventionen](#formatting-conventions)

   Regeln für das Layout und die Struktur Ihres Codes, um diesen lesbarer zu machen. Beispielsweise können Sie Regeln hinsichtlich der geschweiften Klammern (Allman) angeben, oder es werden Leerzeichen in Steuerblöcken bevorzugt.

- [Benennungskonventionen](../ide/editorconfig-naming-conventions.md)

   Regeln für die Benennung von Codeelementen. Sie können beispielsweise angeben, dass die `async`-Methoden mit „Async“ enden müssen.

## <a name="language-conventions"></a>Sprachkonventionen

Regeln für die Sprachkonventionen weisen folgendes Format auf:

`options_name = false|true : none|suggestion|warning|error`

Für jede Sprachkonventionsregel müssen Sie entweder **TRUE** (dieses Format wird bevorzugt) oder **FALSE** (dieses Format wird nicht bevorzugt) und einen **Schweregrad** angeben. Der Schweregrad gibt die Ebene der Erzwingung für dieses Format an.

In der folgenden Tabelle werden die möglichen Schweregrade und die zugehörigen Auswirkungen aufgeführt:

Schweregrad | Effekt
:------- | ------
„none“ oder „silent“ | Zeigen Sie dem Benutzer nichts mehr an, wenn gegen diese Regel verstoßen wird. Features zur Codegenerierung generieren jedoch Code in diesem Format.
Vorschlag | Wenn gegen diese Regel verstoßen wird, zeigen Sie sie dem Benutzer als Vorschlag an. Vorschläge werden in Form von drei grauen Punkten unter den ersten zwei Zeichen dargestellt.
warning | Zeigen Sie eine Compilerwarnung an, wenn gegen diese Formatregel verstoßen wird.
error | Zeigen Sie einen Compilerfehler an, wenn gegen diese Formatregel verstoßen wird.

Die folgende Liste enthält die zulässigen Sprachkonventionsregeln:

- .NET-Codeformateinstellungen
    - [Qualifizierer „This.“ und „Me.“](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Sprachschlüsselwörter anstelle von Framework-Typnamen für Typverweise](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [Einstellungen von Modifizierern](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
    - [Einstellungen auf Ausdrucksebene](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
        - dotnet\_prefer\_inferred\_tuple_names
        - dotnet\_prefer\_inferred\_anonymous\_type\_member_names
- Einstellungen für das C#-Codeformat
    - [Implizite und explizite Typen](#var)
        - csharp\_style\_var\_for\_built\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - csharp\_style\_var_elsewhere
    - [Ausdruckskörpermember](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Mustervergleich](#pattern_matching)
        - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
        - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
    - [Inline-Variablendeklarationen](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [Einstellungen auf Ausdrucksebene](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - csharp\_style\_deconstructed\_variable_declaration
        - csharp\_style\_pattern\_local\_over\_anonymous_function
    - [Einstellungen für die NULL-Überprüfung](#null_checking)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Codeblockeinstellungen](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>Einstellungen für das .NET-Codeformat

Die Formatregeln in diesem Abschnitt gelten für C# und für Visual Basic. Wenn Sie Codebeispiele in Ihrer bevorzugten Programmiersprache anzeigen möchten, wählen Sie diese in der oberen rechten Ecke Ihres Browserfensters im Dropdownmenü **Sprache** aus.

#### <a name="this_and_me">Qualifizierer „This.“ und „Me.“</a>

Diese Formatregel (Regel-IDs IDE0003 und IDE0009) kann auf Felder, Eigenschaften, Methoden oder Ereignisse angewendet werden. Wenn **TRUE** festgelegt ist, wird dem Codesymbol in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt. Wenn **FALSE** festgelegt ist, wird dem Codeelement bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Die folgende Tabelle zeigt die Regelnamen, gültigen Programmiersprachen und Standardwerte:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standardwert |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# und Visual Basic | false:none |
| dotnet_style_qualification_for_property | C# und Visual Basic | false:none |
| dotnet_style_qualification_for_method | C# und Visual Basic | false:none |
| dotnet_style_qualification_for_event | C# und Visual Basic | false:none |

**dotnet\_style\_qualification\_for_field**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird Feldern in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird Feldern bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Codebeispiele:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

**dotnet\_style\_qualification\_for_property**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird Eigenschaften in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird Eigenschaften bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Codebeispiele:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

**dotnet\_style\_qualification\_for_method**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird Methoden in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird Methoden bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Codebeispiele:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

**dotnet\_style\_qualification\_for_event**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird Ereignissen in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird Ereignissen bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Codebeispiele:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

Diese Regeln könnten in einer .editorconfig-Datei wie folgt angezeigt werden:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords">Sprachschlüsselwörter anstelle von Framework-Typnamen für Typverweise</a>

Diese Formatregel kann auf lokale Variablen, Methodenparameter und Klassenmember oder als separate Regel für Typmemberzugriffsausdrücke angewendet werden. Wenn der Wert **TRUE** festgelegt ist, wird bei Typen, die durch ein Schlüsselwort dargestellt werden, das Sprachschlüsselwort (z.B. `int` oder `Integer`) vor dem Typnamen (z.B. `Int32`) bevorzugt. Wenn der Wert **FALSE** festgelegt ist, wird der Typname vor dem Sprachschlüsselwort bevorzugt.

Die folgende Tabelle zeigt die Regelnamen, Regel-IDs, gültigen Programmiersprachen und Standardwerte:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 und IDE0014 | C# und Visual Basic | true:none |
| dotnet_style_predefined_type_for_member_access | IDE0013 und IDE0015 | C# und Visual Basic | true:none |

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird bei Typen, die durch ein Schlüsselwort dargestellt werden, das Sprachschlüsselwort für lokale Variablen, Methodenparameter und Klassenmember vor dem Typnamen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der Typname für lokale Variablen, Methodenparameter und Klassenmember vor dem Sprachschlüsselwort bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

**dotnet\_style\_predefined\_type\_for\_member_access**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird bei Typen, die durch ein Schlüsselwort dargestellt werden, das Sprachschlüsselwort für Memberzugriffsausdrücke vor dem Typnamen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der Typname für Memberzugriffsausdrücke vor dem Sprachschlüsselwort bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

Diese Regeln könnten in einer .editorconfig-Datei wie folgt angezeigt werden:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers">Einstellungen von Modifizierern</a>

Die Formatregeln in diesem Abschnitt beziehen sich auf die Einstellungen von Modifizierern, einschließlich des Erforderns von Zugriffsmodifizierern und des Angebens der gewünschten Sortierreihenfolge für Modifizierer.

In der folgenden Tabelle werden die Regelnamen, Regel-IDs, anzuwendende Programmiersprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# und Visual Basic | for_non_interface_members:none | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:none | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:none | 15.5 |

**dotnet\_style\_require\_accessibility_modifiers**

Diese Regel akzeptiert nicht den Wert **TRUE** oder **FALSE**, sondern einen Wert aus der folgenden Tabelle:

| Wert | description |
| ----- |:----------- |
| always | Es wird bevorzugt, dass Zugriffsmodifizierer angegeben werden |
| for\_non\_interface_members | Es wird bevorzugt, dass Zugriffsmodifizierer deklariert werden (außer für Members von öffentlichen Schnittstellen). Dies unterscheidet sich derzeit nicht von **always** und fungiert als zukünftige Korrekturhilfe, falls Standard-Schnittstellenmethoden in C# hinzugefügt werden. |
| never | Es wird bevorzugt, dass Zugriffsmodifizierer nicht angegeben werden |

Codebeispiele:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst= "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst= "constant";
}
```

**csharp_preferred_modifier_order**

- Wenn diese Regel auf eine Liste von Modifizierern festgelegt ist, wird die angegebene Sortierung bevorzugt.
- Wenn diese Regel in der Datei nicht vorhanden ist, wird keine Reihenfolge der Modifizierer bevorzugt.

Codebeispiele:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- Wenn diese Regel auf eine Liste von Modifizierern festgelegt ist, wird die angegebene Sortierung bevorzugt.
- Wenn diese Regel in der Datei nicht vorhanden ist, wird keine Reihenfolge der Modifizierer bevorzugt.

Codebeispiele:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

Diese Regeln könnten in einer .editorconfig-Datei wie folgt angezeigt werden:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="expression_level">Einstellungen auf Ausdrucksebene</a>

Die Formatregeln in diesem Abschnitt betreffen Einstellungen auf Ausdrucksebene, einschließlich der Verwendung von Objektinitialisierern, Auflistungsinitialisierern, expliziter Tupelnamen und NULL-Sammelausdrücken im Vergleich zu ternären Operatoren und dem Operator mit NULL-Bedingung.

In der folgenden Tabelle werden die Regelnamen, Regel-IDs, anzuwendende Programmiersprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# und Visual Basic | true:suggestion | Erste Version |
| dotnet_style_collection_initializer | IDE0028 | C# und Visual Basic | true:suggestion | Erste Version |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0 und höher und Visual Basic 15 und höher | true:suggestion | Erste Version |
| dotnet_style_coalesce_expression | IDE0029 | C# und Visual Basic | true:suggestion | Erste Version |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ und Visual Basic 14+ | true:suggestion | Erste Version |
| dotnet_prefer_inferred_tuple_names | IDE0037 | C# 7.1 und höher und Visual Basic 15 und höher | true:suggestion | 15.6 Vorschauversion 2 |
| dotnet_prefer_inferred_anonymous_type_member_names | IDE0037 | C# und Visual Basic | true:suggestion | 15.6 Vorschauversion 2 |

**dotnet\_style\_object_initializer**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird, sofern möglich, die Initialisierung von Objekten mithilfe von Objektinitialisierern bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die Initialisierung von Objekten mithilfe von Objektinitialisierern *nicht* bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**dotnet\_style\_collection_initializer**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird, sofern möglich, die Initialisierung von Auflistungen mithilfe von Auflistungsinitialisierern bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die Initialisierung von Auflistungen mithilfe von Auflistungsinitialisierern *nicht* bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

**dotnet\_style\_explicit\_tuple_names**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden Tupelnamen vor ItemX-Eigenschaften bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden ItemX-Eigenschaften vor Tupelnamen bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**dotnet\_style\_coalesce_expression**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden NULL-Sammelausdrücke vor der ternären Operatorüberprüfung bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die ternäre Operatorüberprüfung vor NULL-Sammelausdrücken bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird, sofern möglich, der Operator mit NULL-Bedingung bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird nach Möglichkeit die ternäre NULL-Überprüfung verwendet.

Codebeispiele:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

**dotnet\_prefer\_inferred\_tuple_names**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden abgeleitete Tupelelementnamen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden explizite Tupelelementnamen bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden abgeleitete Membernamen vom anonymen Typ bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden explizite Membernamen vom anonymen Typ bevorzugt.

Codebeispiele:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };

```

Diese Regeln könnten in einer .editorconfig-Datei wie folgt angezeigt werden:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
```

### <a name="c-code-style-settings"></a>Einstellungen für das C#-Codeformat

Die Formatregeln in diesem Abschnitt gelten nur für C#.

#### <a name="var">Implizite und explizite Typen</a>

Die Formatregeln in diesem Abschnitt (Regel-IDs IDE0007 und IDE0008) betreffen die Verwendung des Schlüsselworts [var](/dotnet/csharp/language-reference/keywords/var) im Vergleich zu einem expliziten Typ in einer Variablendeklaration. Diese Regel kann getrennt auf integrierte Typen angewendet werden, wenn diese Typen offensichtlich sind und sich an einer anderen Position befinden.

Die folgende Tabelle zeigt die Regelnamen, gültigen Programmiersprachen und Standardwerte:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true:none |
| csharp_style_var_when_type_is_apparent | C# | true:none |
| csharp_style_var_elsewhere | C# | true:none |

**csharp\_style\_var\_for\_built\_in_types**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird bevorzugt `var` zum Deklarieren von Variablen mit integrierten Systemtypen wie `int` verwendet.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der explizite Typ vor `var` zum Deklarieren von Variablen mit integrierten Systemtypen wie `int` bevorzugt.

Codebeispiele:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird `var` bevorzugt, wenn der Typ bereits auf der rechten Seite eines Deklarationsausdrucks erwähnt wird.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der explizite Typ vor `var` bevorzugt, wenn der Typ bereits auf der rechten Seite eines Deklarationsausdrucks erwähnt wird.

Codebeispiele:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird `var` in allen Fällen vor dem expliziten Typ bevorzugt, es sei denn, es wird von einer anderen Codeformatregel überschrieben.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der explizite Typ in allen Fällen vor `var` bevorzugt, es sei denn, er wird von einer anderen Codeformatregel überschrieben.

Codebeispiele:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members">Ausdruckskörpermember</a>

Die Formatregeln in diesem Abschnitt betreffen die Verwendung von [Ausdruckskörpermember](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members), wenn die Logik aus einem einzelnen Ausdruck besteht. Diese Regel kann auf Methoden, Konstruktoren, Operatoren, Eigenschaften, Indexer und Accessoren angewendet werden.

In der folgenden Tabelle werden die Regelnamen, Regel-IDs, anzuwendende Sprachversionen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0 und höher | false:none | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0 und höher | false:none | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 und IDE0024 | C# 7.0 und höher | false:none | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0 und höher | true:none | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0 und höher | true:none | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0 und höher | true:none | 15.3 |

**csharp\_style\_expression\_bodied_methods**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | description |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Methoden bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Methoden bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Methoden bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | description |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Konstruktoren bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Konstruktoren bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Konstruktoren bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | description |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Operatoren bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Operatoren bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Operatoren bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | description |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Eigenschaften bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Eigenschaften bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Eigenschaften bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | description |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Indexer bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Indexer bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Indexer bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _value[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

Diese Regel akzeptiert Werte aus der folgenden Tabelle:

| Wert | description |
| ----- |:----------- |
| true | Ausdruckskörpermember werden für Accessoren bevorzugt |
| when_on_single_line | Ausdruckskörpermember werden für Accessoren bevorzugt, wenn diese aus einer einzelnen Zeile bestehen |
| False | Blocktexte werden für Accessoren bevorzugt |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching">Mustervergleich</a>

Die Formatregeln in diesem Abschnitt betreffen die Verwendung von [Mustervergleich](/dotnet/csharp/pattern-matching) in C#.

Die folgende Tabelle zeigt die Regelnamen, Regel-IDs, gültigen Sprachversionen und Standardwerte:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0 und höher | true:suggestion |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0 und höher | true:suggestion |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird der Mustervergleich vor `is`-Ausdrücken mit Typumwandlungen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden `is`-Ausdrücke mit Typumwandlungen vor dem Mustervergleich bevorzugt.

Codebeispiele:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird der Mustervergleich vor `as`-Ausdrücken mit NULL-Überprüfungen für die Bestimmung bevorzugt, ob etwas von einem bestimmten Typ ist.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden `as`-Ausdrücke mit NULL-Überprüfungen vor dem Mustervergleich für die Bestimmung bevorzugt, ob etwas von einem bestimmten Typ ist.

Codebeispiele:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations">Inline-Variablendeklarationen</a>

Diese Formatregel bezieht sich darauf, ob `out`-Variablen inline deklariert werden oder nicht. Ab C# 7 können Sie [in der Argumentliste eines Methodenaufrufs eine out-Variable deklarieren](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), anstatt dies in einer separaten Variablendeklaration zu machen.

Die folgende Tabelle zeigt die Regelnamen, Regel-IDs, gültigen Sprachversionen und Standardwerte:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0 und höher | true:suggestion |

**csharp\_style\_inlined\_variable_declaration**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden, sofern möglich, die `out`-Variablen bevorzugt, die in der Argumentliste eines Methodenaufrufs inline deklariert werden.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden zu deklarierende `out`-Variablen vor dem Methodenaufruf bevorzugt.

Codebeispiele:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp">Einstellungen auf Ausdrucksebene</a>

Die Stilregeln in diesem Abschnitt beziehen sich auf die Einstellungen auf Ausdrucksebene, einschließlich der Verwendung von [default-Ausdrücken](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), dekonstruierten Variablen und lokalen Funktionen statt anonymen Funktionen.

In der folgenden Tabelle werden der Regelname, Regel-IDs, anzuwendende Sprachversionen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0 und höher | true:suggestion | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0 und höher | true:suggestion | 15.5 |

**csharp\_prefer\_simple\_default_expression**

Diese Formatregel bezieht sich auf die Verwendung des [`default`-Literals für Standardwertausdrücke](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), wenn der Compiler den Typ des Ausdrucks ableiten kann.

- Wenn diese Regel auf **TRUE** festgelegt ist, wird `default` vor `default(T)` bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird `default(T)` vor `default` bevorzugt.

Codebeispiele:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird die Deklaration von dekonstruierten Variablen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die Deklaration von dekonstruierten Variablen nicht bevorzugt.

Codebeispiele:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden lokale Funktionen vor anonymen Funktionen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden anonyme Funktionen gegenüber lokalen Funktionen bevorzugt.

Codebeispiele:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking">Einstellungen für die NULL-Überprüfung</a>

Diese Formatregeln beziehen sich auf die Syntax hinsichtlich der `null`-Prüfung, einschließlich der Verwendung von `throw`-Ausdrücken oder `throw`-Anweisungen; ferner bezieht sie sich darauf, ob eine NULL-Überprüfung durchgeführt oder der bedingte Sammeloperator (`?.`) verwendet werden soll, wenn ein [Lambdaausdruck](/dotnet/csharp/lambda-expressions) aufgerufen wird.

Die folgende Tabelle zeigt die Regelnamen, Regel-IDs, gültigen Sprachversionen und Standardwerte:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0 und höher | true:suggestion |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0 und höher | true:suggestion |

**csharp\_style\_throw_expression**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird die Verwendung von `throw`-Ausdrücken vor `throw`-Anweisungen bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird die Verwendung von `throw`-Anweisungen vor `throw`-Ausdrücken bevorzugt.

Codebeispiele:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird beim Abrufen eines Lambdaausdrucks die Verwendung des bedingten Sammeloperators (`?.`) vor der Durchführung einer NULL-Überprüfung bevorzugt.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird vor dem Abrufen eines Lambdaausdrucks die Durchführung einer NULL-Überprüfung vor der Verwendung des bedingten Sammeloperators (`?.`) bevorzugt.

Codebeispiele:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block">Codeblockeinstellungen</a>

Diese Formatregel bezieht sich auf die Verwendung der geschweiften Klammern `{ }`, die Codeblöcke umgeben.

In der folgenden Tabelle werden der Regelname, Regel-IDs, anzuwendende Sprachversionen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Regel-ID | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_braces | IDE0011 | C# | true:none | 15.3 |

**csharp\_prefer\_braces**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden geschweifte Klammern bevorzugt, auch für eine Codezeile.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden, sofern zulässig, keine geschweiften Klammern bevorzugt.

Codebeispiele:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>Formatierungskonventionen

Die meisten Regeln für Formatierungskonventionen weisen folgendes Format auf:

`rule_name = false|true`

Sie geben entweder **TRUE** (dieses Format bevorzugen) oder **FALSE** (dieses Format nicht bevorzugen) an. Sie geben keinen Schweregrad an. Für einige Regeln geben Sie statt „TRUE“ und „FALSE“ andere Werte an, um zu beschreiben, wann und wo die Regel angewendet wird.

In der folgenden Liste werden die Regeln für Formatierungskonventionen angezeigt, die in Visual Studio verfügbar sind:

- .NET-Formatierungseinstellungen
    - [Using-Direktiven organisieren](#usings)
        - dotnet_sort_system_directives_first
- C#-Formatierungseinstellungen
    - [Zeilenvorschuboptionen](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Einzugsoptionen](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Leerzeichenoptionen](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
    - [Umbruchoptionen](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>.NET-Formatierungseinstellungen

Die Formatierungsregeln in diesem Abschnitt gelten für C# und für Visual Basic.

#### <a name="usings">Organisieren von Using-Direktiven</a>

Diese Formatierungsregel bezieht sich auf die Platzierung von System.* using-Direktiven in Bezug auf andere using-Direktiven.

In der folgenden Tabelle werden der Regelname, anzuwendende Sprachen, der Standardwert und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_sort_system_directives_first |  C# und Visual Basic | true | 15.3  |

**dotnet\_sort\_system\_directives_first**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden System.* using-Direktiven alphabetisch sortiert und vor anderen using-Direktiven platziert.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden keine System.* using-Direktiven vor anderen using-Direktiven platziert.

Codebeispiele:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

.editorconfig-Beispieldatei:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

### <a name="c-formatting-settings"></a>C#-Formatierungseinstellungen

Die Formatierungsregeln in diesem Abschnitt gelten nur für C#-Code.

#### <a name="newline">Zeilenvorschuboptionen</a>

Diese Formatierungsregeln beziehen sich auf die Verwendung neuer Zeilen zur Codeformatierung.

In der folgenden Tabelle werden die Regelnamen für „neue Zeile“, anzuwendende Sprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_new_line_before_open_brace |  C# | alle | 15.3  |
| csharp_new_line_before_else |  C# | true | 15.3  |
| csharp_new_line_before_catch |  C# | true | 15.3  |
| csharp_new_line_before_finally |  C# | true | 15.3  |
| csharp_new_line_before_members_in_object_initializers |  C# | true | 15.3  |
| csharp_new_line_before_members_in_anonymous_types |  C# | true | 15.3  |
| csharp_new_line_between_query_expression_clauses |  C# | true | 15.3  |

**csharp\_new\_line\_before\_open_brace**

Diese Regel bezieht sich auf die Frage, ob eine öffnende geschweifte Klammer `{` in derselben Zeile wie der vorangehende Code oder in einer neuen Zeile platziert werden soll. Bei dieser Regel geben Sie nicht **TRUE** oder **FALSE** an. Stattdessen geben Sie **Alle**, **Keine** oder mindestens ein Codeelement an, wie z.B. **Methoden** oder **Eigenschaften**, um festzulegen, wann diese Regel angewendet werden sollte. Die vollständige Liste der zulässigen Werte wird in der folgenden Tabelle dargestellt:

| Wert | description
| ------------- |:-------------|
| accessors, anonymous_methods, anonymous_types, control_blocks, events, indexers, lambdas, local_functions, methods, object_collection, properties, types.<br>(Trennen Sie mehrere Arten mit einem Komma). | Klammern müssen für die angegebenen Codeelemente in einer neuen Zeile stehen (Stil „Allman“) |
| alle | Klammern müssen für alle Ausdrücke in einer neuen Zeile stehen (Stil „Allman“) |
| Keine | Klammern müssen für alle Ausdrücke in der gleichen Zeile stehen („K&R“) |

Codebeispiele:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden `else`-Anweisungen in einer neuen Zeile platziert.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden `else`-Anweisungen in derselben Zeile platziert.

Codebeispiele:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden `catch`-Anweisungen in einer neuen Zeile platziert.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden `catch`-Anweisungen in derselben Zeile platziert.

Codebeispiele:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**

- Wenn diese Regel auf **TRUE** festgelegt ist, müssen `finally`-Anweisungen in einer neuen Zeile hinter der schließenden geschweiften Klammer stehen.
- Wenn diese Regel auf **FALSE** festgelegt ist, müssen `finally`-Anweisungen in derselben Zeile wie die schließende geschweifte Klammer stehen.

Codebeispiele:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**

- Wenn diese Regel auf **TRUE** festgelegt ist, müssen Member von Objektinitialisierern in separaten Zeilen stehen.
- Wenn diese Regel auf **FALSE** festgelegt ist, müssen Member von Objektinitialisierern in derselben Zeile stehen.

Codebeispiele:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**

- Wenn diese Regel auf **TRUE** festgelegt ist, müssen Member von anonymen Typen in separaten Zeilen stehen.
- Wenn diese Regel auf **FALSE** festgelegt ist, müssen Member von anonymen Typen in derselben Zeile stehen.

Codebeispiele:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- Wenn diese Regel auf **TRUE** festgelegt ist, müssen Elemente von Abfrageausdrucksklauseln in separaten Zeilen stehen.
- Wenn diese Regel auf **FALSE** festgelegt ist, müssen Elemente von Abfrageausdrucksklauseln in derselben Zeile stehen.

Codebeispiele:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent">Einzugsoptionen</a>

Diese Formatierungsregeln beziehen sich auf die Verwendung von Einzügen zur Codeformatierung.

In der folgenden Tabelle werden die Regelnamen, anzuwendende Sprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_indent_case_contents |  C# | true | 15.3  |
| csharp_indent_switch_labels |  C# | true | 15.3  |
| csharp_indent_labels |  C# | no_change | 15.3  |

**csharp\_indent\_case_contents**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden die `switch`-Fallinhalte eingezogen.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden die `switch`-Fallinhalte nicht eingezogen.

Codebeispiele:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden die `switch`-Bezeichnungen eingezogen.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden die `switch`-Bezeichnungen nicht eingezogen.

Codebeispiele:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**

Diese Regel akzeptiert nicht den Wert **TRUE** oder **FALSE**, sondern einen Wert aus der folgenden Tabelle:

| Wert | description |
| ----- |:----------- |
| flush_left | Bezeichnungen werden in der Spalte ganz links angeordnet |
| one_less_than_current | Bezeichnungen werden mit geringerem Einzug platziert als der aktuelle Kontext. |
| no_change | Bezeichnungen werden mit dem gleichen Einzug platziert wie der aktuelle Kontext. |

Codebeispiele:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing">Leerzeichenoptionen</a>

Diese Formatierungsregeln beziehen sich auf die Verwendung von Leerzeichen zur Codeformatierung.

In der folgenden Tabelle werden die Regelnamen, anzuwendende Sprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_space_after_cast |  C# | False | 15.3  |
| csharp_space_after_keywords_in_control_flow_statements |  C# | true | 15.3  |
| csharp_space_between_method_declaration_parameter_list_parentheses |  C# | False | 15.3  |
| csharp_space_between_method_call_parameter_list_parentheses |  C# | False | 15.3  |
| csharp_space_between_parentheses |  C# | False | 15.3  |

**csharp\_space\_after_cast**

- Wenn diese Regel auf **TRUE** festgelegt ist, ist zwischen einer Typumwandlung und dem Wert ein Leerzeichen erforderlich.
- Wenn diese Regel auf **FALSE** festgelegt ist, ist zwischen einer Typumwandlung und dem Wert _kein_ Leerzeichen erforderlich.

Codebeispiele:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Wenn diese Regel auf **TRUE** festgelegt ist, ist hinter einem Schlüsselwort in einer Ablaufsteuerungsanweisung ein Leerzeichen erforderlich, z.B. in einer `for`-Schleife.
- Wenn diese Regel auf **FALSE** festgelegt ist, ist hinter einem Schlüsselwort in einer Ablaufsteuerungsanweisung _kein_ Leerzeichen erforderlich, z.B. in einer `for`-Schleife.

Codebeispiele:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Wenn diese Regel auf **TRUE** festgelegt ist, platzieren Sie bei einer Parameterliste der Methodendeklaration hinter der öffnenden Klammer und vor der schließenden Klammer ein Leerzeichen.
- Wenn diese Regel auf **FALSE** festgelegt ist, platzieren Sie bei einer Parameterliste der Methodendeklaration hinter der öffnenden Klammer und vor der schließenden Klammer kein Leerzeichen.

Codebeispiele:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Wenn diese Regel auf **TRUE** festgelegt ist, platzieren Sie bei einem Methodenaufruf hinter der öffnenden Klammer und vor der schließenden Klammer ein Leerzeichen.
- Wenn diese Regel auf **FALSE** festgelegt ist, platzieren Sie bei einem Methodenaufruf hinter der öffnenden Klammer und vor der schließenden Klammer kein Leerzeichen.

Codebeispiele:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Diese Regel akzeptiert nicht den Wert **TRUE** oder **FALSE**, sondern einen Wert aus der folgenden Tabelle:

| Wert | description |
| ----- |:------------|
| control_flow_statements | Leerzeichen zwischen Klammern von Ablaufsteuerungsanweisungen einfügen. |
| Ausdrücke | Leerzeichen zwischen Klammern von Ausdrücken einfügen. |
| type_casts | Leerzeichen zwischen Klammern in Typumwandlungen einfügen. |

Codebeispiele:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for( int i;i<x;i++ ) { ... }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3);

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
```

#### <a name="wrapping">Umbruchoptionen</a>

Diese Formatierungsregeln beziehen sich auf die Verwendung von einzelnen Zeilen im Vergleich zu separaten Zeilen bei Anweisungen und Codeblöcken.

In der folgenden Tabelle werden die Regelnamen, anzuwendende Sprachen, Standardwerte und die erste unterstützte Version von Visual Studio angezeigt:

| Regelname | Anzuwendende Sprachen | Visual Studio-Standard | Visual Studio 2017-Version |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_preserve_single_line_statements |  C# | true | 15.3  |
| csharp_preserve_single_line_blocks |  C# | true | 15.3  |

**csharp_preserve_single_line_statements**

- Wenn diese Regel auf **TRUE** festgelegt ist, werden Anweisungen und Memberdeklarationen in derselben Zeile belassen.
- Wenn diese Regel auf **FALSE** festgelegt ist, werden Anweisungen und Memberdeklarationen in unterschiedlichen Zeilen belassen.

Codebeispiele:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Wenn diese Regel auf **TRUE** festgelegt ist, wird der Codeblock in einer einzelnen Zeile belassen.
- Wenn diese Regel auf **FALSE** festgelegt ist, wird der Codeblock in separaten Zeilen belassen.

Codebeispiele:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

.editorconfig-Beispieldatei:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="see-also"></a>Siehe auch

- [Schnelle Aktionen](../ide/quick-actions.md)
- [.NET-Namenskonventionen für EditorConfig](../ide/editorconfig-naming-conventions.md)
- [Erstellen portierbarer benutzerdefinierter Editor-Optionen](../ide/create-portable-custom-editor-options.md)
- [.editorconfig-Datei der .NET Compiler Platform](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
