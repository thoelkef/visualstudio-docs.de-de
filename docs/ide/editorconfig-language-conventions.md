---
title: .NET-Sprachkonventionen für EditorConfig
ms.date: 06/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2dcd0af308da3f16af461dd4b61aae3e31af0236
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67262803"
---
# <a name="language-conventions"></a>Sprachkonventionen

Die Sprachkonventionen für EditorConfig in Visual Studio lassen sich in zwei Kategorien unterteilen:

- [Einstellungen für das .NET-Codeformat](#net-code-style-settings)

- [Einstellungen für das C#-Codeformat](#c-code-style-settings)

> [!TIP]
> Um Codebeispiele in Ihrer bevorzugten Programmiersprache anzuzeigen, wählen Sie diese mithilfe der Sprachauswahl in der oberen rechten Ecke des Browserfensters aus.

## <a name="rule-format"></a>Regelformat

Regeln für Sprachkonventionen weisen das folgende allgemeine Format auf:

`option_name = value:severity`

Für jede Sprachkonvention geben Sie einen Wert an, der definiert, ob oder wann Sie das Format bevorzugen. Viele Regeln akzeptieren den Wert `true` (dieses Format bevorzugen) oder `false` (dieses Format nicht bevorzugen). Andere akzeptieren Werte wie `when_on_single_line` oder `never`. Der zweite Teil der Regel gibt den **Schweregrad** an.

### <a name="severity"></a>Schweregrad

Der Schweregrad einer Sprachkonvention gibt an, auf welcher Ebene das Format erzwungen werden soll. In der folgenden Tabelle werden die möglichen Schweregrade und die zugehörigen Auswirkungen aufgeführt:

Schweregrad | Effekt
:------- | ------
`none` | Zeigen Sie dem Benutzer nichts mehr an, wenn gegen diese Regel verstoßen wird. Features zur Codegenerierung generieren jedoch Code in diesem Format. Regeln mit dem Schweregrad `none` werden im Menü **Schnelle Aktionen und Refactorings** nie angezeigt. In den meisten Fällen gelten diese als „deaktiviert“ oder „ignoriert“.
`silent` (auch `refactoring` in Visual Studio 2017 Version 15.8 und höher) | Zeigen Sie dem Benutzer nichts mehr an, wenn gegen diese Regel verstoßen wird. Features zur Codegenerierung generieren jedoch Code in diesem Format. Regeln mit dem Schweregrad `silent` gelten für Bereinigungsvorgänge und werden im Menü **Schnellaktionen und Refactorings** angezeigt.
`suggestion` | Wenn gegen diese Regel verstoßen wird, zeigen Sie sie dem Benutzer als Vorschlag an. Vorschläge werden in Form von drei grauen Punkten unter den ersten zwei Zeichen dargestellt.
`warning` | Zeigen Sie eine Compilerwarnung an, wenn gegen diese Formatregel verstoßen wird.
`error` | Zeigen Sie einen Compilerfehler an, wenn gegen diese Formatregel verstoßen wird.

## <a name="net-code-style-settings"></a>Einstellungen für das .NET-Codeformat

Die Formatregeln in diesem Abschnitt gelten für C# und für Visual Basic.

- [Qualifizierer „This.“ und „Me.“](#this-and-me)
   - dotnet\_style\_qualification\_for_field
   - dotnet\_style\_qualification\_for_property
   - dotnet\_style\_qualification\_for_method
   - dotnet\_style\_qualification\_for_event
- [Sprachschlüsselwörter anstelle von Framework-Typnamen für Typverweise](#language-keywords)
   - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
   - dotnet\_style\_predefined\_type\_for\_member_access
- [Einstellungen von Modifizierern](#normalize-modifiers)
   - dotnet\_style\_require\_accessibility_modifiers
   - csharp\_preferred\_modifier_order
   - visual\_basic\_preferred\_modifier_order
   - dotnet\_style\_readonly\_field
- [Einstellungen für Klammern](#parentheses-preferences)
   - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
   - dotnet\_style\_parentheses\_in\_other\_binary\_operators
   - dotnet\_style\_parentheses\_in\_other\_operators
   - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
- [Einstellungen auf Ausdrucksebene](#expression-level-preferences)
   - dotnet\_style\_object_initializer
   - dotnet\_style\_collection_initializer
   - dotnet\_style\_explicit\_tuple_names
   - dotnet\_style\_prefer\_inferred\_tuple_names
   - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
   - dotnet\_style\_prefer\_auto\_properties
   - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
   - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
   - dotnet\_style\_prefer\_conditional\_expression\_over\_return
- [Einstellungen für die NULL-Überprüfung](#null-checking-preferences)
   - dotnet\_style\_coalesce_expression
   - dotnet\_style\_null_propagation

### <a name="this-and-me"></a>Die Qualifizierer „This.“ und „Me.“

Diese Formatregel kann auf Felder, Eigenschaften, Methoden oder Ereignisse angewendet werden. Wenn **TRUE** festgelegt ist, wird dem Codesymbol in C# bevorzugt `this.` oder in Visual Basic `Me.` vorangestellt. Wenn **FALSE** festgelegt ist, wird dem Codeelement bevorzugt _nicht_ `this.` oder `Me.` vorangestellt.

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnetstylequalificationforfield"></a>dotnet\_style\_qualification\_for_field

|||
|-|-|
| **Regelname** | dotnet_style_qualification_for_field |
| **Regel-ID** | IDE0003 und IDE0009 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – Feldern in C# bevorzugt `this.` oder in Visual Basic bevorzugt `Me.` voranstellen.<br /><br />`false` – Feldern bevorzugt _nicht_ `this.` oder `Me.` voranstellen. |
| **Visual Studio-Standard** | `false:silent` |

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

#### <a name="dotnetstylequalificationforproperty"></a>dotnet\_style\_qualification\_for_property

|||
|-|-|
| **Regelname** | dotnet_style_qualification_for_property |
| **Regel-ID** | IDE0003 und IDE0009 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – Eigenschaften in C# bevorzugt `this.` oder in Visual Basic bevorzugt `Me.` voranstellen.<br /><br />`false` – Eigenschaften bevorzugt _nicht_ `this.` oder `Me.` voranstellen. |
| **Visual Studio-Standard** | `false:silent` |

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

#### <a name="dotnetstylequalificationformethod"></a>dotnet\_style\_qualification\_for_method

|||
|-|-|
| **Regelname** | dotnet_style_qualification_for_method |
| **Regel-ID** | IDE0003 und IDE0009 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – Methoden in C# bevorzugt `this.` oder in Visual Basic bevorzugt `Me.` voranstellen.<br /><br />`false` – Methoden bevorzugt _nicht_ `this.` oder `Me.` voranstellen. |
| **Visual Studio-Standard** | `false:silent` |

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

#### <a name="dotnetstylequalificationforevent"></a>dotnet\_style\_qualification\_for_event

|||
|-|-|
| **Regelname** | dotnet_style_qualification_for_event |
| **Regel-ID** | IDE0003 und IDE0009 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – Ereignissen in C# bevorzugt `this.` oder in Visual Basic bevorzugt `Me.` voranstellen.<br /><br />`false` – Ereignissen bevorzugt _nicht_ `this.` oder `Me.` voranstellen. |
| **Visual Studio-Standard** | `false:silent` |

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

### <a name="language-keywords"></a>Sprachschlüsselwörter anstelle von Framework-Typnamen für Typverweise

Diese Formatregel kann auf lokale Variablen, Methodenparameter und Klassenmember oder als separate Regel für Typmemberzugriffsausdrücke angewendet werden. Wenn der Wert auf **TRUE** festgelegt ist, wird bei Typen, die durch ein Schlüsselwort dargestellt werden, das Sprachschlüsselwort (z.B. `int` oder `Integer`) vor dem Typnamen (z.B. `Int32`) bevorzugt. Wenn der Wert **FALSE** festgelegt ist, wird der Typname vor dem Sprachschlüsselwort bevorzugt.

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnetstylepredefinedtypeforlocalsparametersmembers"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|||
|-|-|
| **Regelname** | dotnet_style_predefined_type_for_locals_parameters_members |
| **Regel-ID** | IDE0012 und IDE0014 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – bei Typen, die durch ein Schlüsselwort dargestellt werden, für lokale Variablen, Methodenparameter und Klassenmember bevorzugt das Sprachschlüsselwort anstelle des Typnamens verwenden.<br /><br />`false` – für lokale Variablen, Methodenparameter und Klassenmember bevorzugt den Typnamen anstelle des Sprachschlüsselworts verwenden. |
| **Visual Studio-Standard** | `true:silent` |

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

#### <a name="dotnetstylepredefinedtypeformemberaccess"></a>dotnet\_style\_predefined\_type\_for\_member_access

|||
|-|-|
| **Regelname** | dotnet_style_predefined_type_for_member_access |
| **Regel-ID** | IDE0013 und IDE0015 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – bei Typen, die durch ein Schlüsselwort dargestellt werden, für Memberzugriffsausdrücke bevorzugt das Sprachschlüsselwort anstelle des Typnamens verwenden.<br /><br />`false` – für Memberzugriffsausdrücke bevorzugt den Typnamen anstelle des Sprachschlüsselworts verwenden. |
| **Visual Studio-Standard** | `true:silent` |

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

### <a name="normalize-modifiers"></a>Einstellungen von Modifizierern

Die Formatregeln in diesem Abschnitt beziehen sich auf die Einstellungen von Modifizierern, einschließlich des Erforderns von Zugriffsmodifizierern und schreibgeschützten Modifizierern und des Angebens der gewünschten Sortierreihenfolge für Modifizierer.

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="dotnetstylerequireaccessibilitymodifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|||
|-|-|
| **Regelname** | dotnet_style_require_accessibility_modifiers |
| **Regel-ID** | IDE0040 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `always` – Angabe von Zugriffsmodifizierern wird bevorzugt.<br /><br />`for_non_interface_members` – Deklarieren von Zugriffsmodifizierern wird bevorzugt (außer für Member von öffentlichen Schnittstellen). (Dies entspricht **always** und fungiert als zukünftige Korrekturhilfe, falls Standard-Schnittstellenmethoden in C# hinzugefügt werden.)<br /><br />`never` – Angabe von Zugriffsmodifizierern wird nicht bevorzugt.<br /><br />`omit_if_default` – Angabe von Zugriffsmodifizierern wird bevorzugt, außer wenn es sich um Standardmodifizierer handelt. |
| **Visual Studio-Standard** | `for_non_interface_members:silent` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.5 |

Codebeispiele:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

#### <a name="csharppreferredmodifierorder"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Regelname** | csharp_preferred_modifier_order |
| **Regel-ID** | IDE0036 |
| **Gültige Sprachen** | C# |
| **Werte** | Mindestens ein C#-Modifizierer wie `public`, `private` und `protected`. |
| **Visual Studio-Standard** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.5 |

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

#### <a name="visualbasicpreferredmodifierorder"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Regelname** | visual_basic_preferred_modifier_order |
| **Regel-ID** | IDE0036 |
| **Gültige Sprachen** | Visual Basic |
| **Werte** | Mindestens ein Visual Basic-Modifizierer wie `Partial`, `Private` und `Public`. |
| **Visual Studio-Standard** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.5 |

- Wenn diese Regel auf eine Liste von Modifizierern festgelegt ist, wird die angegebene Sortierung bevorzugt.
- Wenn diese Regel in der Datei nicht vorhanden ist, wird keine Reihenfolge der Modifizierer bevorzugt.

Codebeispiele:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="dotnetstylereadonlyfield"></a>dotnet_style_readonly_field

|||
|-|-|
| **Regelname** | dotnet_style_readonly_field |
| **Regel-ID** | IDE0044 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – Felder werden bevorzugt mit `readonly` (C#) oder `ReadOnly` (Visual Basic) markiert, wenn sie auch nur einmal inline oder innerhalb eines Konstruktors zugewiesen wurden.<br /><br />`false` – keine Angabe, ob Felder bevorzugt mit `readonly` (C#) oder `ReadOnly` (Visual Basic) markiert werden. |
| **Visual Studio-Standard** | `true:suggestion` |
| **Eingeführt in Version** | Visual Studio 2017-Version 15.7 |

Codebeispiele:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

### <a name="parentheses-preferences"></a>Einstellungen für Klammern

Die Stilregeln in diesem Abschnitt betreffen Einstellungen für Klammern, einschließlich der Verwendung von Klammern für arithmetische, relationale und anderen binäre Operatoren.

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnetstyleparenthesesinarithmeticbinaryoperators"></a>dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators

|||
|-|-|
| **Regelname** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **Regel-ID** | IDE0047 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `always_for_clarity` – bevorzugt Klammern verwenden, um den Vorrang von arithmetischen Operatoren (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) zu verdeutlichen.<br /><br />`never_if_unnecessary` – bevorzugt keine Klammern verwenden, wenn der Vorrang von arithmetischen Operatoren (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) offensichtlich ist. |
| **Visual Studio-Standard** | `always_for_clarity:silent` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.8 |

Codebeispiele:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

#### <a name="dotnetstyleparenthesesinrelationalbinaryoperators"></a>dotnet\_style\_parentheses\_in\_relational\_binary_operators

|||
|-|-|
| **Regelname** | dotnet_style_parentheses_in_relational_binary_operators |
| **Regel-ID** | IDE0047 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `always_for_clarity` – bevorzugt Klammern verwenden, um den Vorrang von relationalen Operatoren (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) zu verdeutlichen.<br /><br />`never_if_unnecessary` – bevorzugt keine Klammern verwenden, wenn der Vorrang von relationalen Operatoren (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) offensichtlich ist. |
| **Visual Studio-Standard** | `always_for_clarity:silent` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.8 |

Codebeispiele:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

#### <a name="dotnetstyleparenthesesinotherbinaryoperators"></a>dotnet\_style\_parentheses\_in\_other\_binary_operators

|||
|-|-|
| **Regelname** | dotnet_style_parentheses_in_other_binary_operators |
| **Regel-ID** | IDE0047 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `always_for_clarity` – bevorzugt Klammern verwenden, um den Vorrang von anderen binären Operatoren (`&&`, `||`, `??`) zu verdeutlichen.<br /><br />`never_if_unnecessary` – bevorzugt keine Klammern verwenden, wenn der Vorrang von anderen binären Operatoren (`&&`, `||`, `??`) offensichtlich ist. |
| **Visual Studio-Standard** | `always_for_clarity:silent` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.8 |

Codebeispiele:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

#### <a name="dotnetstyleparenthesesinotheroperators"></a>dotnet\_style\_parentheses\_in\_other_operators

|||
|-|-|
| **Regelname** | dotnet_style_parentheses_in_other_operators |
| **Regel-ID** | IDE0047 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `always_for_clarity` – bevorzugt Klammern verwenden, um den Vorrang von Operatoren zu verdeutlichen.<br /><br />`never_if_unnecessary` – bevorzugt keine Klammern verwenden, wenn der Vorrang von Operatoren offensichtlich ist. |
| **Visual Studio-Standard** | `never_if_unnecessary:silent` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.8 |

Codebeispiele:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

### <a name="expression-level-preferences"></a>Einstellungen auf Ausdrucksebene

Die Formatierungsregeln in diesem Abschnitt betreffen Einstellungen auf Ausdrucksebene, einschließlich der Verwendung von Objektinitialisierern, Auflistungsinitialisierern, expliziter oder abgeleiteter Tupelnamen und abgeleiteter anonymer Typen.

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="dotnetstyleobjectinitializer"></a>dotnet\_style\_object_initializer

|||
|-|-|
| **Regelname** | dotnet_style_object_initializer |
| **Regel-ID** | IDE0017 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – Wenn möglich, die Initialisierung von Objekten mithilfe von Objektinitialisierern bevorzugen.<br /><br />`false` – Die Initialisierung von Objekten mithilfe von Objektinitialisierern *nicht* bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

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

#### <a name="dotnetstylecollectioninitializer"></a>dotnet\_style\_collection_initializer

|||
|-|-|
| **Regelname** | dotnet_style_collection_initializer |
| **Regel-ID** | IDE0028 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – Wenn möglich, die Initialisierung von Auflistungen mithilfe von Auflistungsinitialisierern bevorzugen.<br /><br />`false` – Die Initialisierung von Auflistungen mithilfe von Auflistungsinitialisierern *nicht* bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

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

#### <a name="dotnetstyleexplicittuplenames"></a>dotnet\_style\_explicit\_tuple_names

|||
|-|-|
| **Regelname** | dotnet_style_explicit_tuple_names |
| **Regel-ID** | IDE0033 |
| **Gültige Sprachen** | C# 7.0 und höher und Visual Basic 15 und höher |
| **Werte** | `true` – Tupelnamen gegenüber ItemX-Eigenschaften bevorzugen.<br /><br />`false` – ItemX-Eigenschaften gegenüber Tupelnamen bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

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

#### <a name="dotnetstylepreferinferredtuplenames"></a>dotnet\_style\_prefer\_inferred\_tuple_names

|||
|-|-|
| **Regelname** | dotnet_style_prefer_inferred_tuple_names |
| **Regel-ID** | IDE0037 |
| **Gültige Sprachen** | C# 7.1 und höher und Visual Basic 15 und höher |
| **Werte** | `true` – abgeleitete Tupelelementnamen bevorzugen.<br /><br />`false` – explizite Tupelelementnamen bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.6 |

Codebeispiele:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

#### <a name="dotnetstylepreferinferredanonymoustypemembernames"></a>dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names

|||
|-|-|
| **Regelname** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **Regel-ID** | IDE0037 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – abgeleitete anonyme Typmembernamen bevorzugen.<br /><br />`false` – explizite anonyme Typmembernamen bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.6 |

Codebeispiele:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

#### <a name="dotnetstylepreferautoproperties"></a>dotnet\_style\_prefer\_auto\_properties

|||
|-|-|
| **Regelname** | dotnet_style_prefer_auto_properties |
| **Regel-ID** | IDE0032 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – automatische Eigenschaften gegenüber Eigenschaften mit privaten Unterstützungsfeldern bevorzugen.<br /><br />`false` – Eigenschaften mit privaten Unterstützungsfeldern gegenüber automatischen Eigenschaften bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |
| **Eingeführt in Version** | Visual Studio 2017-Version 15.7 |

Codebeispiele:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

#### <a name="dotnetstylepreferisnullcheckoverreferenceequalitymethod"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|||
|-|-|
| **Regelname** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Regel-ID** | IDE0041 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – Verwenden einer NULL-Überprüfung mit Mustervergleich gegenüber `object.ReferenceEquals` bevorzugen.<br /><br />`false` – Verwenden von `object.ReferenceEquals` gegenüber einer NULL-Prüfung mit Mustervergleich bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |
| **Eingeführt in Version** | Visual Studio 2017-Version 15.7 |

Codebeispiele:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

#### <a name="dotnetstylepreferconditionalexpressionoverassignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|||
|-|-|
| **Regelname** | dotnet_style_prefer_conditional_expression_over_assignment |
| **Regel-ID** | IDE0045 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – Zuweisungen mit einem ternären bedingten Operator gegenüber einer if-else-Anweisung bevorzugen.<br /><br />`false` – Zuweisungen mit einer if-else-Anweisung gegenüber einem ternären bedingten Operator bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.8 |

Codebeispiele:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

#### <a name="dotnetstylepreferconditionalexpressionoverreturn"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|||
|-|-|
| **Regelname** | dotnet_style_prefer_conditional_expression_over_return |
| **Regel-ID** | IDE0046 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – bei return-Anweisungen einen ternären bedingten Operator gegenüber einer if-else-Anweisung bevorzugen.<br /><br />`false` – bei return-Anweisungen eine if-else-Anweisung gegenüber einem ternären bedingten Operator bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.8 |

Codebeispiele:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

### <a name="null-checking-preferences"></a>Einstellungen für die NULL-Überprüfung

Die Formatierungsregeln in diesem Abschnitt betreffen die Einstellungen der NULL-Überprüfung.

Diese Regeln werden in einer *EDITORCONFIG-Datei* z.B. folgendermaßen angezeigt:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

#### <a name="dotnetstylecoalesceexpression"></a>dotnet\_style\_coalesce_expression

|||
|-|-|
| **Regelname** | dotnet_style_coalesce_expression |
| **Regel-ID** | IDE0029 |
| **Gültige Sprachen** | C# und Visual Basic |
| **Werte** | `true` – NULL-Sammelausdrücke gegenüber der Überprüfung ternärer Operatoren bevorzugen.<br /><br />`false` – Überprüfung ternärer Operatoren gegenüber NULL-Sammelausdrücken bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

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

#### <a name="dotnetstylenullpropagation"></a>dotnet\_style\_null_propagation

|||
|-|-|
| **Regelname** | dotnet_style_null_propagation |
| **Regel-ID** | IDE0031 |
| **Gültige Sprachen** | C# 6.0+ und Visual Basic 14+ |
| **Werte** | `true` – wenn möglich, die Verwendung von NULL-Bedingungsoperatoren bevorzugen.<br /><br />`false` – wenn möglich, die Verwendung von ternärer NULL-Überprüfung bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

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

## <a name="c-code-style-settings"></a>Einstellungen für das C#-Codeformat

Die Formatregeln in diesem Abschnitt gelten nur für C#.

- [Implizite und explizite Typen](#implicit-and-explicit-types)
   - csharp\_style\_var\_for\_built\_in_types
   - csharp\_style\_var\_when\_type\_is_apparent
   - csharp\_style\_var_elsewhere
- [Ausdruckskörpermember](#expression-bodied-members)
   - csharp\_style\_expression\_bodied_methods
   - csharp\_style\_expression\_bodied_constructors
   - csharp\_style\_expression\_bodied_operators
   - csharp\_style\_expression\_bodied_properties
   - csharp\_style\_expression\_bodied_indexers
   - csharp\_style\_expression\_bodied_accessors
- [Mustervergleich](#pattern-matching)
   - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
   - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
- [Inline-Variablendeklarationen](#inlined-variable-declarations)
   - csharp\_style\_inlined\_variable_declaration
- [Einstellungen auf Ausdrucksebene](#expression-level-preferences)
   - csharp\_prefer\_simple\_default_expression
   - csharp\_style\_deconstructed\_variable_declaration
   - csharp\_style\_pattern\_local\_over\_anonymous_function
- [Einstellungen für die NULL-Überprüfung](#null-checking-preferences)
   - csharp\_style\_throw_expression
    - csharp\_style\_conditional\_delegate_call
- [Codeblockeinstellungen](#code-block-preferences)
   - csharp\_prefer_braces

### <a name="implicit-and-explicit-types"></a>Implizite und explizite Typen

Die Formatregeln in diesem Abschnitt betreffen die Verwendung des Schlüsselworts [var](/dotnet/csharp/language-reference/keywords/var) im Vergleich zu einem expliziten Typ in einer Variablendeklaration. Diese Regel kann getrennt auf integrierte Typen angewendet werden, wenn diese Typen offensichtlich sind und sich an einer anderen Position befinden.

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharpstylevarforbuiltintypes"></a>csharp\_style\_var\_for\_built\_in_types

|||
|-|-|
| **Regelname** | csharp_style_var_for_built_in_types |
| **Regel-ID** | IDE0007 und IDE0008 |
| **Gültige Sprachen** | C#  |
| **Werte** | `true` – die Verwendung von `var` zum Deklarieren von Variablen mit integrierten Systemtypen wie `int` bevorzugen.<br /><br />`false` – die Verwendung von expliziten Typen gegenüber `var` bevorzugen, um Variablen mit integrierten Systemtypen wie `int` zu deklarieren. |
| **Visual Studio-Standard** | `true:silent` |

Codebeispiele:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharpstylevarwhentypeisapparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|||
|-|-|
| **Regelname** | csharp_style_var_when_type_is_apparent |
| **Regel-ID** | IDE0007 und IDE0008 |
| **Gültige Sprachen** | C#  |
| **Werte** | `true` – `var` bevorzugen, wenn der Typ bereits auf der rechten Seite eines Deklarationsausdrucks erwähnt ist.<br /><br />`false` – einen expliziten Typ gegenüber `var` bevorzugen, wenn der Typ bereits auf der rechten Seite eines Deklarationsausdrucks erwähnt ist. |
| **Visual Studio-Standard** | `true:silent` |

Codebeispiele:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharpstylevarelsewhere"></a>csharp\_style\_var_elsewhere

|||
|-|-|
| **Regelname** | csharp_style_var_elsewhere |
| **Regel-ID** | IDE0007 und IDE0008 |
| **Gültige Sprachen** | C#  |
| **Werte** | `true` – `var` in allen Fällen gegenüber dem expliziten Typ bevorzugen, außer bei einer Überschreibung durch eine andere Codeformatregel.<br /><br />`false` – den expliziten Typ in allen Fällen gegenüber `var` bevorzugen, außer bei einer Überschreibung durch eine andere Codeformatregel. |
| **Visual Studio-Standard** | `true:silent` |

Codebeispiele:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Ausdruckskörpermember

Die Formatregeln in diesem Abschnitt betreffen die Verwendung von [Ausdruckskörpermember](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members), wenn die Logik aus einem einzelnen Ausdruck besteht. Diese Regel kann auf Methoden, Konstruktoren, Operatoren, Eigenschaften, Indexer und Accessoren angewendet werden.

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="csharpstyleexpressionbodiedmethods"></a>csharp\_style\_expression\_bodied_methods

|||
|-|-|
| **Regelname** | csharp_style_expression_bodied_methods |
| **Regel-ID** | IDE0022 |
| **Gültige Sprachen** | C# 6.0 und höher  |
| **Werte** | `true` – Ausdruckskörpermember für Methoden bevorzugen.<br /><br />`when_on_single_line` – Ausdruckskörpermember für Methoden bevorzugen, wenn diese aus einer einzelnen Zeile bestehen.<br /><br />`false` – Blocktexte für Methoden bevorzugen. |
| **Visual Studio-Standard** | `false:silent` |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharpstyleexpressionbodiedconstructors"></a>csharp\_style\_expression\_bodied_constructors

|||
|-|-|
| **Regelname** | csharp_style_expression_bodied_constructors |
| **Regel-ID** | IDE0021 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – Ausdruckskörpermember für Konstruktoren bevorzugen.<br /><br />`when_on_single_line` – Ausdruckskörpermember für Konstruktoren bevorzugen, wenn diese aus einer einzelnen Zeile bestehen.<br /><br />`false` – Blocktexte für Konstruktoren bevorzugen. |
| **Visual Studio-Standard** | `false:silent` |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharpstyleexpressionbodiedoperators"></a>csharp\_style\_expression\_bodied_operators

|||
|-|-|
| **Regelname** | csharp_style_expression_bodied_operators |
| **Regel-ID** | IDE0023 und IDE0024 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – Ausdruckskörpermember für Operatoren bevorzugen.<br /><br />`when_on_single_line` – Ausdruckskörpermember für Operatoren bevorzugen, wenn diese aus einer einzelnen Zeile bestehen.<br /><br />`false` – Blocktexte für Operatoren bevorzugen. |
| **Visual Studio-Standard** | `false:silent` |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharpstyleexpressionbodiedproperties"></a>csharp\_style\_expression\_bodied_properties

|||
|-|-|
| **Regelname** | csharp_style_expression_bodied_properties |
| **Regel-ID** | IDE0025 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – Ausdruckskörpermember für Eigenschaften bevorzugen.<br /><br />`when_on_single_line` – Ausdruckskörpermember für Eigenschaften bevorzugen, wenn diese aus einer einzelnen Zeile bestehen.<br /><br />`false` – Blocktexte für Eigenschaften bevorzugen. |
| **Visual Studio-Standard** | `true:silent` |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharpstyleexpressionbodiedindexers"></a>csharp\_style\_expression\_bodied_indexers

|||
|-|-|
| **Regelname** | csharp_style_expression_bodied_indexers |
| **Regel-ID** | IDE0026 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – Ausdruckskörpermember für Indexer bevorzugen.<br /><br />`when_on_single_line` – Ausdruckskörpermember für Indexer bevorzugen, wenn diese aus einer einzelnen Zeile bestehen.<br /><br />`false` – Blocktexte für Indexer bevorzugen. |
| **Visual Studio-Standard** | `true:silent` |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharpstyleexpressionbodiedaccessors"></a>csharp\_style\_expression\_bodied_accessors

|||
|-|-|
| **Regelname** | csharp_style_expression_bodied_accessors |
| **Regel-ID** | IDE0027 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – Ausdruckskörpermember für Zugriffsmethoden bevorzugen.<br /><br />`when_on_single_line` – Ausdruckskörpermember für Zugriffsmethoden bevorzugen, wenn diese aus einer einzelnen Zeile bestehen.<br /><br />`false` – Blocktexte für Zugriffsmethoden bevorzugen. |
| **Visual Studio-Standard** | `true:silent` |

Codebeispiele:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

### <a name="pattern-matching"></a>Musterabgleich

Die Formatregeln in diesem Abschnitt betreffen die Verwendung von [Mustervergleich](/dotnet/csharp/pattern-matching) in C#.

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharpstylepatternmatchingoveriswithcastcheck"></a>csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check

|||
|-|-|
| **Regelname** | csharp_style_pattern_matching_over_is_with_cast_check |
| **Regel-ID** | IDE0020 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – Mustervergleich gegenüber `is`-Ausdrücken mit Typumwandlungen bevorzugen.<br /><br />`false` – `is`-Ausdrücke mit Typumwandlungen gegenüber Mustervergleich bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

Codebeispiele:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharpstylepatternmatchingoveraswithnullcheck"></a>csharp\_style\_pattern\_matching\_over\_as\_with\_null_check

|||
|-|-|
| **Regelname** | csharp_style_pattern_matching_over_as_with_null_check |
| **Regel-ID** | IDE0019 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – Mustervergleich anstelle von `as`-Ausdrücken mit NULL-Überprüfungen für die Bestimmung bevorzugen, ob eine Element einen bestimmten Typ aufweist.<br /><br />`false` – `as`-Ausdrücke mit NULL-Überprüfungen anstelle von Mustervergleich für die Bestimmung bevorzugen, ob ein Element einen bestimmten Typ aufweist. |
| **Visual Studio-Standard** | `true:suggestion` |

Codebeispiele:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Inline-Variablendeklarationen

Diese Formatregel bezieht sich darauf, ob `out`-Variablen inline deklariert werden oder nicht. Ab C# 7 können Sie [in der Argumentliste eines Methodenaufrufs eine out-Variable deklarieren](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), anstatt dies in einer separaten Variablendeklaration zu machen.

#### <a name="csharpstyleinlinedvariabledeclaration"></a>csharp\_style\_inlined\_variable_declaration

|||
|-|-|
| **Regelname** | csharp_style_inlined_variable_declaration |
| **Regel-ID** | IDE0018 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – wenn möglich, `out`-Variablen bevorzugt in der Argumentliste eines Methodenaufrufs inline deklarieren.<br /><br />`false` – `out`-Variablen bevorzugt vor dem Methodenaufruf deklarieren. |
| **Visual Studio-Standard** | `true:suggestion` |

Codebeispiele:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="expression-level-preferences"></a>Einstellungen auf Ausdrucksebene

Die Stilregeln in diesem Abschnitt beziehen sich auf die Einstellungen auf Ausdrucksebene, einschließlich der Verwendung von [default-Ausdrücken](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), dekonstruierten Variablen und lokalen Funktionen statt anonymen Funktionen.

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="csharpprefersimpledefaultexpression"></a>csharp\_prefer\_simple\_default_expression

Diese Formatregel bezieht sich auf die Verwendung des [`default`-Literals für Standardwertausdrücke](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), wenn der Compiler den Typ des Ausdrucks ableiten kann.

|||
|-|-|
| **Regelname** | csharp_prefer_simple_default_expression |
| **Regel-ID** | IDE0034 |
| **Gültige Sprachen** | C# 7.1+  |
| **Werte** | `true` – `default` gegenüber `default(T)` bevorzugen.<br /><br />`false` – `default(T)` gegenüber `default` bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

Codebeispiele:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

#### <a name="csharpstyledeconstructedvariabledeclaration"></a>csharp\_style\_deconstructed\_variable_declaration

|||
|-|-|
| **Regelname** | csharp_style_deconstructed_variable_declaration |
| **Regel-ID** | IDE0042 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – dekonstruierte Variablendeklaration bevorzugen.<br /><br />`false` – Dekonstruktion in Variablendeklarationen nicht bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

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

#### <a name="csharpstylepatternlocaloveranonymousfunction"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

|||
|-|-|
| **Regelname** | csharp_style_pattern_local_over_anonymous_function |
| **Regel-ID** | IDE0039 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – lokale Funktionen gegenüber anonymen Funktionen bevorzugen.<br /><br />`false` – anonyme Funktionen gegenüber lokalen Funktionen bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

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

### <a name="null-checking-preferences"></a>Einstellungen für die NULL-Überprüfung

Diese Formatregeln beziehen sich auf die Syntax hinsichtlich der `null`-Prüfung, einschließlich der Verwendung von `throw`-Ausdrücken oder `throw`-Anweisungen; ferner bezieht sie sich darauf, ob eine NULL-Überprüfung durchgeführt oder der bedingte Sammeloperator (`?.`) verwendet werden soll, wenn ein [Lambdaausdruck](/dotnet/csharp/lambda-expressions) aufgerufen wird.

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharpstylethrowexpression"></a>csharp\_style\_throw_expression

|||
|-|-|
| **Regelname** | csharp_style_throw_expression |
| **Regel-ID** | IDE0016 |
| **Gültige Sprachen** | C# 7.0 und höher  |
| **Werte** | `true` – Verwendung von `throw`-Ausdrücken anstelle von `throw`-Anweisungen bevorzugen.<br /><br />`false` – Verwendung von `throw`-Anweisungen anstelle von `throw`-Ausdrücken bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

Codebeispiele:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharpstyleconditionaldelegatecall"></a>csharp\_style\_conditional\_delegate_call

|||
|-|-|
| **Regelname** | csharp_style_conditional_delegate_call |
| **Regel-ID** | IDE0041 |
| **Gültige Sprachen** | C# 6.0 und höher  |
| **Werte** | `true` – beim Aufrufen eines Lambdaausdrucks die Verwendung des bedingten Sammeloperators (`?.`) gegenüber der Durchführung einer NULL-Überprüfung bevorzugen.<br /><br />`false` – vor dem Aufrufen eines Lambdaausdrucks die Durchführung einer NULL-Überprüfung gegenüber der Verwendung des bedingten Sammeloperators (`?.`) bevorzugen. |
| **Visual Studio-Standard** | `true:suggestion` |

Codebeispiele:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Codeblockeinstellungen

Diese Formatregel bezieht sich auf die Verwendung der geschweiften Klammern `{ }`, die Codeblöcke umgeben.

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharppreferbraces"></a>csharp\_prefer\_braces

|||
|-|-|
| **Regelname** | csharp_prefer_braces |
| **Regel-ID** | IDE0011 |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – geschweifte Klammern auch für eine Codezeile bevorzugen.<br /><br />`false` – keine geschweiften Klammern bevorzugen, wenn zulässig. |
| **Visual Studio-Standard** | `true:silent` |

Codebeispiele:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

## <a name="see-also"></a>Siehe auch

- [Formatierungskonventionen](editorconfig-formatting-conventions.md)
- [Namenskonventionen](editorconfig-naming-conventions.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](editorconfig-code-style-settings-reference.md)