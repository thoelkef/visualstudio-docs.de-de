---
title: .NET-Formatierungskonventionen für EditorConfig
ms.date: 07/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ccebfc38d5170920fe3f3c37ee77aabaf660a3b8
ms.sourcegitcommit: 8562a337cc9f674c756a4a0b2c7e288ebd61b51e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345670"
---
# <a name="formatting-conventions"></a>Formatierungskonventionen

Die Formatierungskonventionen für EditorConfig in Visual Studio lassen sich in folgende Kategorien unterteilen:

- [.NET-Formatierungseinstellungen](#net-formatting-settings)

- [C#-Formatierungseinstellungen](#c-formatting-settings)

## <a name="rule-format"></a>Regelformat

Die Regeln für Formatierungskonventionen weisen folgendes Format auf:

`rule_name = value`

Bei vielen Regeln geben Sie entweder `true` (dieses Format bevorzugen) oder `false` (dieses Format nicht bevorzugen) als `value` an. Bei anderen Regeln geben Sie einen Wert wie `flush_left` oder `before_and_after` an, um zu beschreiben, wann und wo die Regel angewendet werden soll. Sie geben keinen Schweregrad an.

## <a name="net-formatting-settings"></a>.NET-Formatierungseinstellungen

Die Formatierungsregeln in diesem Abschnitt gelten für C#- und Visual Basic-Code.

- [Organisieren von Using-Direktiven](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Organisieren von using-Direktiven

Diese Formatierungsregeln betreffen die Sortierung und Anzeige von `using`-Direktiven und `Imports`-Anweisungen.

*EDITORCONFIG-Beispieldatei:*

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnetsortsystemdirectivesfirst"></a>dotnet\_sort\_system\_directives_first

|||
|-|-|
| **Regelname** | dotnet_sort_system_directives_first |
| **Gültige Sprachen** | C# und Visual Basic |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – System.* `using`-Direktiven alphabetisch sortieren und vor anderen using-Direktiven platzieren.<br /><br />`false` – System.* `using`-Direktiven nicht vor anderen `using`-Direktiven platzieren. |
| **Visual Studio-Standard** | `true` |

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

#### <a name="dotnetseparateimportdirectivegroups"></a>dotnet\_separate\_import\_directive\_groups

|||
|-|-|
| **Regelname** | dotnet_separate_import_directive_groups |
| **Gültige Sprachen** | C# und Visual Basic |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.5 |
| **Werte** | `true` – Leerzeile zwischen `using`-Direktivengruppen platzieren.<br /><br />`false` – keine Leerzeile zwischen `using`-Direktivengruppen platzieren. |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-settings"></a>C#-Formatierungseinstellungen

Die Formatierungsregeln in diesem Abschnitt gelten nur für C#-Code.

- [Newline-Optionen](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Einzugsoptionen](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Abstandsoptionen](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [Umbruchoptionen](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>Optionen für „Neue Zeile“

Diese Formatierungsregeln beziehen sich auf die Verwendung neuer Zeilen zur Codeformatierung.

*EDITORCONFIG-Beispieldatei:*

```ini
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

#### <a name="csharpnewlinebeforeopenbrace"></a>csharp\_new\_line\_before\_open_brace

Diese Regel bezieht sich auf die Frage, ob eine öffnende geschweifte Klammer `{` in derselben Zeile wie der vorangehende Code oder in einer neuen Zeile platziert werden soll. Für diese Regel geben Sie **Alle**, **Keine** oder mindestens ein Codeelement an, wie z.B. **Methoden** oder **Eigenschaften**, um festzulegen, wann diese Regel angewendet werden soll. Um mehrere Codeelemente anzugeben, trennen Sie diese durch Komma (,).

|||
|-|-|
| **Regelname** | csharp_new_line_before_open_brace |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `all` – geschweifte Klammern müssen für alle Ausdrücke in einer neuen Zeile stehen (Allman-Format).<br /><br />`none` – geschweifte Klammern müssen für alle Ausdrücke in der gleichen Zeile stehen („K&R“).<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` – geschweifte Klammern müssen für das angegebene Codeelement in einer neuen Zeile stehen (Allman-Format). |
| **Visual Studio-Standard** | `all` |

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

#### <a name="csharpnewlinebeforeelse"></a>csharp\_new\_line\_before_else

|||
|-|-|
| **Regelname** | csharp_new_line_before_else |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – `else`-Anweisungen in einer neuen Zeile platzieren.<br /><br />`false` – `else`-Anweisungen in der gleichen Zeile platzieren. |
| **Visual Studio-Standard** | `true` |

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

#### <a name="csharpnewlinebeforecatch"></a>csharp\_new\_line\_before_catch

|||
|-|-|
| **Regelname** | csharp_new_line_before_catch |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – `catch`-Anweisungen in einer neuen Zeile platzieren.<br /><br />`false` – `catch`-Anweisungen in der gleichen Zeile platzieren. |
| **Visual Studio-Standard** | `true` |

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

#### <a name="csharpnewlinebeforefinally"></a>csharp\_new\_line\_before_finally

|||
|-|-|
| **Regelname** | csharp_new_line_before_finally |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – `finally`-Anweisungen müssen nach der schließenden geschweiften Klammer in einer neuen Zeile stehen.<br /><br />`false` – `finally`-Anweisungen müssen nach der schließenden geschweiften Klammer in der gleichen Zeile stehen. |
| **Visual Studio-Standard** | `true` |

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

#### <a name="csharpnewlinebeforemembersinobjectinitializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|||
|-|-|
| **Regelname** | csharp_new_line_before_members_in_object_initializers |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – Member von Objektinitialisierern müssen in separaten Zeilen stehen.<br /><br />`false` – Member von Objektinitialisierern müssen in der gleichen Zeile stehen. |
| **Visual Studio-Standard** | `true` |

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

#### <a name="csharpnewlinebeforemembersinanonymoustypes"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|||
|-|-|
| **Regelname** | csharp_new_line_before_members_in_anonymous_types |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – Member von anonymen Typen müssen in separaten Zeilen stehen.<br /><br />`false` – Member von anonymen Typen müssen in der gleichen Zeile stehen. |
| **Visual Studio-Standard** | `true` |

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

#### <a name="csharpnewlinebetweenqueryexpressionclauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Regelname** | csharp_new_line_between_query_expression_clauses |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – Elemente von Abfrageausdrucksklauseln müssen in separaten Zeilen stehen.<br /><br />`false` – Elemente von Abfrageausdrucksklauseln müssen in der gleichen Zeile stehen. |
| **Visual Studio-Standard** | `true` |

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

### <a name="indentation-options"></a>Einzugsoptionen

Diese Formatierungsregeln beziehen sich auf die Verwendung von Einzügen zur Codeformatierung.

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharpindentcasecontents"></a>csharp\_indent\_case_contents

|||
|-|-|
| **Regelname** | csharp_indent_case_contents |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – „`switch` case“-Inhalte einrücken.<br /><br />`false` – „`switch` case“-Inhalte nicht einrücken. |
| **Visual Studio-Standard** | `true` |

- Wenn diese Regel auf **TRUE** festgelegt ist: i.
- Wenn diese Regel auf **FALSE** festgelegt ist: d.

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

#### <a name="csharpindentswitchlabels"></a>csharp\_indent\_switch_labels

|||
|-|-|
| **Regelname** | csharp_indent_switch_labels |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – `switch`-Bezeichnungen einrücken.<br /><br />`false` – `switch`-Bezeichner nicht einrücken. |
| **Visual Studio-Standard** | `true` |

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

#### <a name="csharpindentlabels"></a>csharp\_indent_labels

|||
|-|-|
| **Regelname** | csharp_indent_labels |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `flush_left` – Bezeichnungen werden in der Spalte ganz links angeordnet.<br /><br />`one_less_than_current` – Bezeichnungen werden mit einem um eine Einheit geringerem Einzug platziert als der aktuelle Kontext.<br /><br />`no_change` – Bezeichnungen werden mit dem gleichen Einzug platziert wie der aktuelle Kontext. |
| **Visual Studio-Standard** | `no_change` |

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

#### <a name="csharpindentblockcontents"></a>csharp_indent_block_contents

|||
|-|-|
| **Regelname** | csharp_indent_block_contents |
| **Gültige Sprachen** | C# |
| **Werte** | `true` - <br /><br />`false` -  |
| **Visual Studio-Standard** | `true` |

Codebeispiele:

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharpindentbraces"></a>csharp_indent_braces

|||
|-|-|
| **Regelname** | csharp_indent_braces |
| **Gültige Sprachen** | C# |
| **Werte** | `true` - <br /><br />`false` -  |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharpindentcasecontentswhenblock"></a>csharp_indent_case_contents_when_block

|||
|-|-|
| **Regelname** | csharp_indent_case_contents_when_block |
| **Gültige Sprachen** | C# |
| **Werte** | `true` - <br /><br />`false` -  |
| **Visual Studio-Standard** | `true` |

Codebeispiele:

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a>Abstandsoptionen

Diese Formatierungsregeln beziehen sich auf die Verwendung von Leerzeichen zur Codeformatierung.

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharpspaceaftercast"></a>csharp\_space\_after_cast

|||
|-|-|
| **Regelname** | csharp_space_after_cast |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – Leerzeichen zwischen einer Umwandlung und dem Wert platzieren<br /><br />`false` – Leerzeichen zwischen einer Umwandlung und dem Wert entfernen |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharpspaceafterkeywordsincontrolflowstatements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Regelname** | csharp_space_after_keywords_in_control_flow_statements |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – Leerzeichen nach einem Schlüsselwort in einer Ablaufsteuerungsanweisung wie einer `for`-Schleife platzieren<br /><br />`false` – Leerzeichen nach einem Schlüsselwort in einer Ablaufsteuerungsanweisung wie einer `for`-Schleife entfernen |
| **Visual Studio-Standard** | `true` |

Codebeispiele:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharpspacebetweenparentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Regelname** | csharp_space_between_parentheses |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `control_flow_statements` – Leerzeichen zwischen Klammern von Ablaufsteuerungsanweisungen einfügen.<br /><br />`expressions` – Leerzeichen zwischen Klammern von Ausdrücken einfügen.<br /><br />`type_casts` – Leerzeichen zwischen Klammern in Typumwandlungen einfügen. |
| **Visual Studio-Standard** | `false` |

Wenn Sie diese Regel auslassen oder einen anderen Wert als `control_flow_statements`, `expressions` oder `type_casts` verwenden, wird die Einstellung nicht angewendet.

Codebeispiele:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharpspacebeforecolonininheritanceclause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|||
|-|-|
| **Regelname** | csharp_space_before_colon_in_inheritance_clause |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017-Version 15.7 |
| **Werte** | `true` – Leerzeichen vor dem Doppelpunkt für Basen oder Schnittstellen in einer Typdeklaration platzieren<br /><br />`false` – Leerzeichen vor dem Doppelpunkt für Basen oder Schnittstellen in einer Typdeklaration entfernen |
| **Visual Studio-Standard** | `true` |

Codebeispiele:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharpspaceaftercolonininheritanceclause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|||
|-|-|
| **Regelname** | csharp_space_after_colon_in_inheritance_clause |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017-Version 15.7 |
| **Werte** | `true` – Leerzeichen nach dem Doppelpunkt für Basen oder Schnittstellen in einer Typdeklaration platzieren<br /><br />`false` – Leerzeichen nach dem Doppelpunkt für Basen oder Schnittstellen in einer Typdeklaration entfernen |
| **Visual Studio-Standard** | `true` |

Codebeispiele:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharpspacearoundbinaryoperators"></a>csharp\_space\_around\_binary_operators

|||
|-|-|
| **Regelname** | csharp_space_around_binary_operators |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017-Version 15.7 |
| **Werte** | `before_and_after` – Leerzeichen vor und nach dem binären Operator einfügen.<br /><br />`none` – Leerzeichen vor und nach dem binären Operator entfernen.<br /><br />`ignore` – Leerzeichen um binäre Operatoren ignorieren. |
| **Visual Studio-Standard** | `before_and_after` |

Wenn Sie diese Regel auslassen oder einen anderen Wert als `before_and_after`, `none` oder `ignore` verwenden, wird die Einstellung nicht angewendet.

Codebeispiele:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharpspacebetweenmethoddeclarationparameterlistparentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Regelname** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – hinter der öffnenden Klammer und vor der schließenden Klammer einer Parameterliste der Methodendeklaration ein Leerzeichen platzieren.<br /><br />`false` – Leerzeichen nach der öffnenden Klammer und vor der schließenden Klammer einer Parameterliste der Methodendeklaration entfernen |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharpspacebetweenmethoddeclarationemptyparameterlistparentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Regelname** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017-Version 15.7 |
| **Werte** | `true` – bei einer Methodendeklaration innerhalb der Klammern für eine leere Parameterliste ein Leerzeichen einfügen.<br /><br />`false` – bei einer Methodendeklaration das Leerzeichen innerhalb der Klammern für eine leere Parameterliste entfernen. |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspacebetweenmethoddeclarationnameandopenparenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|||
|-|-|
| **Regelname** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen zwischen dem Methodennamen und der öffnenden Klammer in der Methodendeklaration platzieren<br /><br />`false` – Leerzeichen zwischen dem Methodennamen und der öffnenden Klammer in der Methodendeklaration entfernen |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharpspacebetweenmethodcallparameterlistparentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Regelname** | csharp_space_between_method_call_parameter_list_parentheses |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – hinter der öffnenden Klammer und vor der schließenden Klammer eines Methodenaufrufs ein Leerzeichen platzieren.<br /><br />`false` – Leerzeichen nach der öffnenden Klammer und vor der schließenden Klammer eines Methodenaufrufs entfernen |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharpspacebetweenmethodcallemptyparameterlistparentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Regelname** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017-Version 15.7 |
| **Werte** | `true` – Leerzeichen zwischen Klammern um leere Argumentliste einfügen.<br /><br />`false` – Leerzeichen zwischen Klammern um leere Argumentliste entfernen. |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspacebetweenmethodcallnameandopeningparenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Regelname** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017-Version 15.7 |
| **Werte** | `true` – zwischen dem Namen des Methodenaufrufs und der öffnenden Klammer ein Leerzeichen einfügen.<br /><br />`false` – das Leerzeichen zwischen dem Namen des Methodenaufrufs und der öffnenden Klammer entfernen. |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspaceaftercomma"></a>csharp_space_after_comma

|||
|-|-|
| **Regelname** | csharp_space_after_comma |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen nach einem Komma einfügen.<br /><br />`false` – Leerzeichen nach einem Komma entfernen. |
| **Visual Studio-Standard** | `true` |

Codebeispiele:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharpspacebeforecomma"></a>csharp_space_before_comma

|||
|-|-|
| **Regelname** | csharp_space_before_comma |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen vor einem Komma einfügen<br /><br />`false` – Leerzeichen vor einem Komma entfernen |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharpspaceafterdot"></a>csharp_space_after_dot

|||
|-|-|
| **Regelname** | csharp_space_after_dot |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen nach einem Punkt einfügen.<br /><br />`false` – Leerzeichen nach einem Punkt entfernen. |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharpspacebeforedot"></a>csharp_space_before_dot

|||
|-|-|
| **Regelname** | csharp_space_before_dot |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen vor einem Punkt einfügen <br /><br />`false` – Leerzeichen vor einem Punkt entfernen |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharpspaceaftersemicoloninforstatement"></a>csharp_space_after_semicolon_in_for_statement

|||
|-|-|
| **Regelname** | csharp_space_after_semicolon_in_for_statement |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen nach jedem Semikolon in einer `for`-Anweisung einfügen<br /><br />`false` – Leerzeichen nach jedem Semikolon in einer `for`-Anweisung entfernen |
| **Visual Studio-Standard** | `true` |

Codebeispiele:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharpspacebeforesemicoloninforstatement"></a>csharp_space_before_semicolon_in_for_statement

|||
|-|-|
| **Regelname** | csharp_space_before_semicolon_in_for_statement |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen vor jedem Semikolon in einer `for`-Anweisung einfügen <br /><br />`false` – Leerzeichen vor jedem Semikolon in einer `for`-Anweisung entfernen |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharpspacearounddeclarationstatements"></a>csharp_space_around_declaration_statements

|||
|-|-|
| **Regelname** | csharp_space_around_declaration_statements |
| **Gültige Sprachen** | C# |
| **Werte** | `ignore` – Keine zusätzlichen Leerzeichen in Deklarationsanweisungen entfernen<br /><br />`false` – Zusätzliche Leerzeichen in Deklarationsanweisungen entfernen |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharpspacebeforeopensquarebrackets"></a>csharp_space_before_open_square_brackets

|||
|-|-|
| **Regelname** | csharp_space_before_open_square_brackets |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen vor öffnenden eckigen Klammern einfügen `[` <br /><br />`false` – Leerzeichen vor öffnenden eckigen Klammern entfernen `[` |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharpspacebetweenemptysquarebrackets"></a>csharp_space_between_empty_square_brackets

|||
|-|-|
| **Regelname** | csharp_space_between_empty_square_brackets |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen zwischen leeren eckigen Klammern einfügen `[ ]` <br /><br />`false` – Leerzeichen zwischen leeren eckigen Klammern entfernen `[]` |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharpspacebetweensquarebrackets"></a>csharp_space_between_square_brackets

|||
|-|-|
| **Regelname** | csharp_space_between_square_brackets |
| **Gültige Sprachen** | C# |
| **Werte** | `true` – Leerzeichen in nicht leeren eckigen Klammern einfügen `[ 0 ]` <br /><br />`false` – Leerzeichen aus nicht leeren eckigen Klammern entfernen `[0]` |
| **Visual Studio-Standard** | `false` |

Codebeispiele:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Umbruchoptionen

Diese Formatierungsregeln beziehen sich auf die Verwendung von einzelnen Zeilen im Vergleich zu separaten Zeilen bei Anweisungen und Codeblöcken.

*EDITORCONFIG-Beispieldatei:*

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharppreservesinglelinestatements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Regelname** | csharp_preserve_single_line_statements |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – Anweisungen und Memberdeklarationen in der gleichen Zeile belassen.<br /><br />`false` – Anweisungen und Memberdeklarationen in verschiedenen Zeilen belassen. |
| **Visual Studio-Standard** | `true` |

Codebeispiele:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharppreservesinglelineblocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Regelname** | csharp_preserve_single_line_blocks |
| **Gültige Sprachen** | C# |
| **Eingeführt in Version** | Visual Studio 2017 Version 15.3 |
| **Werte** | `true` – Codeblock in einzelner Zeile belassen.<br /><br />`false` – Codeblock in separaten Zeilen belassen. |
| **Visual Studio-Standard** | `true` |

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

## <a name="see-also"></a>Siehe auch

- [Sprachkonventionen](editorconfig-language-conventions.md)
- [Namenskonventionen](editorconfig-naming-conventions.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](editorconfig-code-style-settings-reference.md)
