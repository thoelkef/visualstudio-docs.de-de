---
title: "Einstellungen für die .NET-Codierungskonventionen für „EditorConfig“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 1
author: kuhlenh
ms.author: kaseyu
manager: davidcsa
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 17defdd0b96ec1c3273fc6b845af844b031a4a17
ms.openlocfilehash: ced437215b48c76e6df99699b4c6f9c916452d14
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---

# <a name="net-coding-convention-settings-for-editorconfig"></a>Einstellungen für die .NET-Codierungskonventionen für „EditorConfig“
.NET-Codierungskonventionen werden mithilfe einer [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options)-Datei konfiguriert. Mit EditorConfig-Dateien können Sie **einzelne .NET-Codierungskonventionen aktivieren/deaktivieren** und **konfigurieren, inwieweit die Konvention erzwungen werden soll** (über einen Schweregrad). Weitere Informationen zum Verwenden von „EditorConfig“ zum Erzwingen der Konsistenz in Ihrer Codebasis finden Sie in [diesem Artikel](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options).

Es gibt drei unterstützte Kategorien für .NET-Codierungskonventionen:
- **[Sprachkonventionen](#language)** sind Regeln für die Sprachen C# und Visual Basic, z.B. `var`/explicit-Typen und das Verwenden von Ausdruckskörpermembern.
- **[Formatierungsregeln](#formatting)** sind Regeln für das Layout und die Struktur Ihres Codes, um diesen einfacher lesbar zu machen, z.B. Allman-Klammern und Leerzeichen in Kontrollblöcken.
- **[Benennungskonventionen](#naming)** sind Regeln für die Benennung von Objekten, beispielsweise müssen `async`-Methoden mit „Async“ enden. 

# <a name="language"> Sprachkonventionen </a>
## <a name="overview"></a>Übersicht
**Regelformat:**
`options_name = false|true : none|suggestion|warning|error`

Für Codeformatoptionen müssen Sie **TRUE** (diese Option bevorzugen) oder **FALSE** (diese Option nicht bevorzugen), einen Doppelpunkt (`:`) und einen Schweregrad (`none`, `silent`, `suggestion`, `warning` oder `error`) angeben. Der Schweregrad bedeutet den Grad der Durchsetzung, den Sie für das betreffende Format in Ihrer Codebasis festlegen möchten.

`none` und `silent` sind synonym und bedeuten, dass dem Benutzer keinerlei Hinweis angezeigt werden soll. Damit wird diese Regel im Endeffekt deaktiviert.

Schweregrad | Wirkung
------------ | -------------
none/silent | Dem Benutzer nichts anzeigen, wenn dieses Format nicht eingehalten wird, die Funktionen der Codegenerierung werden allerdings in diesem Format erstellt. 
Vorschlag | Wenn dieses Format nicht eingehalten wird, dies dem Benutzer als Vorschlag (zwei unterlegte Punkte auf den ersten beiden Zeichen) anzeigen.
warning | Wenn dieses Format nicht eingehalten wird, eine Compilerwarnung anzeigen.
error | Wenn dieses Format nicht eingehalten wird, einen Compilerfehler anzeigen.

## <a name="net-language-convention-options"></a>Optionen für die .NET-Sprachkonvention

- **[.NET-Codeformateinstellungen](#this_and_me)**
    - ["This.-" und "Me.-" Qualifikation](#this_and_me)
        - [Felder](#this_and_me_fields)
        - [Eigenschaften](#this_and_me_properties)
        - [Methoden](#this_and_me_methods)
        - [Ereignisse](#this_and_me_events)
    - [Sprachschlüsselwörter (int, string usw.) im Vergleich zu Framework-Typnamen für Typverweise](#language_keywords)
        - [Lokale Variablen, Parameter und Member](#language_keywords_variables)
        - [Memberzugriffsausdrücke](#language_keywords_member_access)
    - [Einstellungen auf Ausdrucksebene](#expression_level)
        - [Objektinitialisierer](#expression_level_object_initializers)
        - [Auflistungsinitialisierer](#expression_level_collection_initializers)
        - [Explizite Tupelnamen](#expression_level_tuple_names)
        - [Sammelausdrücke in der NULL-Überprüfung](#expression_level_null_checking)
        - [NULL-Weitergabe in der NULL-Überprüfung](#expression_level_null_propogation)
- **[C#-Codeformateinstellungen](#csharp_codestyle)**
    - ["var"](#var)
        - ["var" für integrierte Typen](#var_built_in)
        - ["var" wenn der Typ offensichtlich ist](#var_apparent)
        - ["var" an anderer Stelle](#var_elsewhere)
    - [Ausdruckskörpermember](#expression_body)
        - [Methoden](#expression_bodied_members_methods)
        - [Konstruktoren](#expression_bodied_members_constructors)
        - [Operatoren](#expression_bodied_members_operators)
        - [Eigenschaften](#expression_bodied_members_properties)
        - [Indexer](#expression_bodied_members_indexers)
        - [Zugriffsmethoden](#expression_bodied_members_accessors)
    - [Mustervergleich](#pattern_matching)
        - ["is" mit Umwandlungsüberprüfung](#pattern_matching_is_cast)
        - ["as" mit NULL-Überprüfung](#pattern_matching_as_null)
    - [Inline-Variablendeklarationen](#inlined_variable_declarations)
    - [Voreinstellungen auf Ausdrucksebene](#expression_level_csharp) -[Vereinfachen von `default`-Ausdrücken](#expression_level_default)
    - [Einstellungen für die NULL-Überprüfung](#null_checking)
        - [Throw-Ausdrücke](#null_checking_throw_expressions)
        - [Bedingte Delegataufrufe](#null_checking_conditional_delegate_calls)
    - [Codeblockeinstellungen](#code_block)
        - [Geschweiften Klammern bevorzugen](#prefer_braces)

## <a name="this_and_me">"This.-" und "Me.-" Qualifikation</a>
### <a name="this_and_me_fields">Felder (IDE0003/IDE0009)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `dotnet_style_qualification_for_field` | C# und Visual Basic | false:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für alle nicht statischen Felder, die in nicht statischen Methoden verwendet werden: Voranstellung von `this.` in C# oder `Me.` in Visual Basic bevorzugen. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** <br> `Me.capacity = 0`
| False | Für alle nicht statischen Felder, die in nicht statischen Methoden verwendet werden: Keine Voranstellung von `this.` in C# oder `Me.` in Visual Basic bevorzugen. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** <br>`capacity = 0`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Eigenschaften (IDE0003/IDE0009) </a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_property`| C# und Visual Basic | false:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für alle nicht statischen Eigenschaften, die in nicht statischen Methoden verwendet werden: Voranstellung von `this.` in C# oder `Me.` in Visual Basic bevorzugen.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** <br>`Me.ID = 0`
| False | Für alle nicht statischen Eigenschaften, die in nicht statischen Methoden verwendet werden: *Keine* Voranstellung von `this.` in C# oder `Me.` in Visual Basic bevorzugen. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** <br> `ID = 0`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_property = false:suggestion
```

### <a name="this_and_me_methods">Methoden (IDE0003/IDE0009) </a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_method`| C# und Visual Basic | false:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für alle nicht statischen Methoden, die innerhalb von nicht statischen Methoden aufgerufen werden: Voranstellung von `this.` in C# oder `Me.` in VB bevorzugen.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** <br> `Me.Display()`
| False | Für alle nicht statischen Methoden, die innerhalb von nicht statischen Methoden aufgerufen werden: *Keine* Voranstellung von `this.` in C# oder `Me.` in VB bevorzugen. | **C#:** <br>`Display();` <br><br> **Visual Basic:** <br> `Display()`


#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">Ereignisse (IDE0003/IDE0009) </a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_event`| C# und Visual Basic | false:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für alle nicht statischen Ereignisse, auf die von nicht statischen Methoden verwiesen wird: Voranstellung von `this.` in C# oder `Me.` in VB bevorzugen.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** <br> `AddHandler Me.Elapsed, AddressOf Handler`
| False | Für alle nicht statischen Ereignisse, auf die von nicht statischen Methoden verwiesen wird: *Keine* Voranstellung von `this.` in C# oder `Me.` in VB bevorzugen. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** <br>`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Sprachschlüsselwörter (int, string usw.) im Vergleich zu Framework-Typnamen für Typverweise</a>
### <a name="language_keywords_variables"> Lokale Variablen, Parameter und Member (IDE0012/IDE0014)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_locals_parameters_members`| C# und Visual Basic | true:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für lokale Variablen, Parameter und Typmember bei Typen, die durch ein Sprachschlüsselwort (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) dargestellt werden können, die Verwendung des Schlüsselworts anstelle des Typnamens (`Int32`, `Int64` usw.) bevorzugen.| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Für lokale Variablen, Parameter und Typmember bei Typen, die durch ein Sprachschlüsselwort (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) dargestellt werden können, die Verwendung des Typnamens (`Int32`, `Int64` usw.) anstelle des Schlüsselworts bevorzugen.  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** <br> `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Memberzugriffsausdrücke (IDE0013/IDE0015)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_member_access`| C# und Visual Basic | true:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Immer das Schlüsselwort bevorzugen, wenn ein Memberzugriffsausdruck auf einen Typ mit Schlüsselwortdarstellung (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) angewendet wird.| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Integer.MaxValue`
| False | Immer den Typnamen bevorzugen, wenn ein Memberzugriffsausdruck auf einen Typ mit Schlüsselwortdarstellung (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) angewendet wird. | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Einstellungen auf Ausdrucksebene</a>
### <a name="expression_level_object_initializers">Objektinitialisierer (IDE0017)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_object_initializer`| C# und Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Wenn möglich, die Initialisierung von Objekten mithilfe von Objektinitialisierern bevorzugen.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** <br> `Dim c = New Customer() With { .Age = 21 }`
| False | Die Initialisierung von Objekten *nicht* mithilfe von Objektinitialisierern bevorzugen. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Auflistungsinitialisierer (IDE0028)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_collection_initializer`| C# und Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Wenn möglich, die Initialisierung von Auflistungen mithilfe von Auflistungsinitialisierern bevorzugen.| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | Die Initialisierung von Auflistungen *nicht* mithilfe von Auflistungsinitialisierern bevorzugen. | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">Explizite Tupelnamen (IDE0033)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_explicit_tuple_names`| C# 7.0 und höher und Visual Basic 15 und höher | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Tupelnamen gegenüber ItemX-Eigenschaften bevorzugen.| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | ItemX-Eigenschaften gegenüber Tupelnamen bevorzugen. | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">Sammelausdrücke in der NULL-Überprüfung (IDE0029)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_coalesce_expression`| C# und Visual Basic | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Sammelausdrücke in der NULL-Überprüfung gegenüber ternärer Operatorüberprüfung bevorzugen.| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | Ternäre Operatorüberprüfung gegenüber NULL-Sammelausdrücken bevorzugen. | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">NULL-Weitergabe in der NULL-Überprüfung (IDE0031)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_null_propagation`| C# 6.0+ und Visual Basic 14+ | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Wenn möglich, die Verwendung von NULL-Bedingungsoperatoren bevorzugen.| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | Wenn möglich, die Verwendung von ternärer NULL-Überprüfung bevorzugen. | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">C#-Codeformateinstellungen</a>
## <a name="var">„var“ und explizite Typen</a>
### <a name="var_built_in">„var“ für integrierte Typen (IDE0007, IDE0008)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_for_built_in_types`| C# | true:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Die Verwendung von `var` für integrierte Systemtypen, wie etwa `int`, bevorzugen.| **C#:** <br>`var x = 5;`
| False | Die Vermeidung von `var` für integrierte Systemtypen, wie etwa `int`, bevorzugen. | **C#:** <br>`int x = 5;`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">„var“ wenn der Typ offensichtlich ist (IDE0007, IDE0008)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_when_type_is_apparent`| C# | true:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | `var` bevorzugen, wenn der Typ bereits auf der rechten Seite eines Deklarationsausdrucks erwähnt ist.| **C#:** <br>`var obj = new C();`
| False | Die Vermeidung von `var` bevorzugen, wenn der Typ bereits auf der rechten Seite eines Deklarationsausdrucks erwähnt ist. | **C#:** <br>`C obj = new C();`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">„var“ an anderer Stelle (IDE0007, IDE0008) </a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_elsewhere`| C# | true:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | `var` in allen Fällen bevorzugen, sofern diese Regel nicht durch eine andere Regel zum Codeformat außer Kraft gesetzt wird.| **C#:** <br>`var f = this.Init();`
| False | Die Vermeidung von „var“ in allen Fällen bevorzugen, sofern diese Regel nicht durch eine andere Regel zum Codeformat außer Kraft gesetzt wird.| **C#:** <br>`bool f = this.Init();`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

##<a name="expression_bodied_members">Ausdruckskörpermember</a>
### <a name="expression_bodied_members_methods">Methoden (IDE0022)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_methods`| C# 6.0 und höher | false:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Ausdruckskörpermember für Methoden bevorzugen.| **C#:** <br>`public int GetAge() => this.Age;`
| False | Die Vermeidung von Ausdruckskörpermembern für Methoden bevorzugen.| **C#:** <br>`public int GetAge() { return this.Age; }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">Konstruktoren (IDE0021)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_constructors`| C# 7.0 und höher | false:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Ausdruckskörpermember für Konstruktoren bevorzugen.| **C#:** <br>`public Customer(int age) => Age = age;`
| False | Vermeidung von Ausdruckskörpermembern für Konstruktoren bevorzugen.| **C#:** <br>`public Customer(int age) { Age = age; }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">Operatoren (IDE0023, IDE0024)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_operators` | C# 7.0 und höher | false:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Ausdruckskörpermember für Operatoren bevorzugen.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | Vermeidung von Ausdruckskörpermembern für Operatoren bevorzugen.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">Eigenschaften (IDE0025)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_properties` | C# 7.0 und höher | true:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Ausdruckskörpermember für Eigenschaften bevorzugen.| **C#:** <br>`public int Age => _age;`
| False | Vermeidung von Ausdruckskörpermembern für Eigenschaften bevorzugen.| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = true:none
``` 

### <a name="expression_bodied_members_indexers">Indexer (IDE0026)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_indexers` | C# 7.0 und höher | true:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Ausdruckskörpermember für Indexer bevorzugen.| **C#:** <br>`public T this[int i] => _value[i];`
| False | Vermeidung von Ausdruckskörpermembern für Indexer bevorzugen.| **C#:** <br>`public T this[int i] { get { return _values[i]; } }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">Accessoren (IDE0027)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_accessors` | C# 7.0 und höher | true:none | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Ausdruckskörpermember für Zugriffsmethoden bevorzugen.| **C#:** <br>`public int Age { get => _age; set => _age = value; }`
| False | Vermeidung von Ausdruckskörpermembern für Zugriffsmethoden bevorzugen.| **C#:** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">Mustervergleich</a>
### <a name="pattern_matching_is_cast">„is“ mit Umwandlungsüberprüfung (IDE0020)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_is_with_cast_check` | C# 7.0 und höher | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Mustervergleich gegenüber `is`-Ausdrücken mit Typumwandlungen bevorzugen.| **C#:** <br>`if (o is int i) {...}`
| False | `is`-Ausdrücke mit Typumwandlungen gegenüber Mustervergleich bevorzugen.| **C#:** <br>`if (o is int) {var i = (int)o; ... }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">„as“ mit NULL-Überprüfung (IDE0019)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_as_with_null_check` | C# 7.0 und höher | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Mustervergleich anstelle von `as`-Ausdrücken mit NULL-Überprüfungen für die Bestimmung bevorzugen, ob etwas von einem bestimmten Typ ist.| **C#:** <br>`if (o is string s) {...}`
| False | `as`-Ausdrücke mit NULL-Überprüfungen anstelle von Mustervergleich für die Bestimmung bevorzugen, ob etwas von einem bestimmten Typ ist.| **C#:** <br>`var s = o as string; if (s != null) {...}`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">Inline-Variablendeklarationen (IDE0018)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_inlined_variable_declaration` | C# 7.0 und höher | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Wenn möglich die Inlinedeklaration von `out`-Variablen bevorzugen. | **C#:** <br>`if (int.TryParse(value, out int i) {...}`
| False | Die explizite Deklaration von `out`-Variablen bevorzugen.| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```
## <a name="expression_level_csharp">Einstellungen auf Ausdrucksebene</a>
### <a name="expression_level_default">Vereinfachen von `default`-Ausdrücken (IDE0034) </a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_simple_default_expression` | C# 7.1+ | true:suggestion | Visual Studio 2017 V. 15.3 |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | `default` gegenüber `default(T)` bevorzugen. | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default){ ... }`
| False | Bevorzugen. | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default(CancellationToken)){ ... }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

## <a name="null_checking">Einstellungen für die NULL-Überprüfung</a>
### <a name="null_checking_throw_expressions">Throw-Ausdrücke (IDE0016)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_throw_expression`  | C# 7.0 und höher | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Bevorzugen der Verwendung von `throw`-Ausdrücken anstelle von `throw`-Anweisungen. | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | Bevorzugen der Verwendung von `throw`-Anweisungen anstelle von `throw`-Ausdrücken.| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">Bedingte Delegataufrufe bevorzugen (IDE0041)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_conditional_delegate_call`  | C# 6.0 und höher | true:suggestion | Visual Studio 2017 RTW |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Die Verwendung eines bedingten Sammelvorgangs (`?.`) beim Aufruf eines Lambda-Ausdrucks anstelle einer NULL-Überprüfung bevorzugen. | **C#:** <br>`func?.Invoke(args);`
| False | Bevorzugen der Ausführung einer NULL-Überprüfung vor dem Aufrufen eines Lambda-Ausdrucks anstelle der Verwendung des bedingten Sammeloperators (`?.`).| **C#:** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

## <a name="code_block">Codeblockeinstellungen</a>
### <a name="prefer_braces">Geschweifte Klammern bevorzugen (IDE0011)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_braces`  | C#  | true:none | Visual Studio 2017 V. 15.3 |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Geschweifte Klammern bevorzugen | **C#:** <br>`if (test) { this.Display(); }`
| False | Wenn möglich, keine Klammern bevorzugen | **C#:** <br>`if (test) this.Display();`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

# <a name="formatting"> Formatierungsregeln </a>
## <a name="overview"></a>Übersicht
**Regelformat:**
`options_name = false|true`

Bei Formatierungsoptionen müssen Sie **TRUE** (diese Option bevorzugen) oder **FALSE** (diese Option nicht bevorzugen) angeben, außer in einigen Fällen, in denen Sie stattdessen angeben müssen, unter welchen Bedingungen die Regel angewendet werden soll.

## <a name="net-formatting-options"></a>.NET-Formatierungsoptionen

- **[.NET-Formatierungseinstellungen](#usings)**
    - [Using-Direktiven organisieren](#usings)
        - [Systemdirektiven zuerst sortieren](#usings_sort_system_first)
- **[C#-Formatierungseinstellungen](#newline)**
    - [Zeilenvorschuboptionen](#newline)
        - [Zeilenvorschub vor öffnender Klammer (`{`)](#newline_before_brace)
        - [Zeilenvorschub vor `else`](#newline_before_else)
        - [Zeilenvorschub vor `catch`](#newline_before_catch)
        - [Zeilenvorschub vor `finally`](#newline_before_finally)
        - [Zeilenvorschub vor Membern in Objektinitialisierern](#newline_before_object)
        - [Zeilenvorschub vor Membern in anonymen Typen](#newline_before_anonymous)
        - [Zeilenvorschub vor Membern in Abfrageausdrucksklauseln](#newline_before_query)
    - [Einzugsoptionen](#indent)
        - [`switch` Case-Inhalte einrücken](#indent_switch)
        - [`switch`-Bezeichner einrücken](#indent_switch_labels)
        - [Positionierung von Bezeichnungen](#label)
    - [Leerzeichenoptionen](#spacing)
        - [Leerzeichen nach Typumwandlung](#space_after_cast)
        - [Leerezeichen nach Schlüsselwörtern in Ablaufsteuerungsanweisungen](#space_control_flow)
        - [Leerzeichen zwischen Klammern in Methodendeklarationsparameter-Listen](#space_parameter_list)
        - [Leerzeichen innerhalb von Klammern in Methodenaufrufargument-Listen](#space_method_call)
        - [Leerzeichen innerhalb von Klammern für andere Optionen](#space_other)
    - [Umbruchoptionen](#wrapping)
        - [Anweisungen und Memberdeklarationen in der gleichen Zeile belassen](#wrapping_statement)
        - [Block in einzelner Zeile belassen](#wrapping_block)

## <a name="usings">Using-Direktiven organisieren</a>
### <a name="usings_sort_system_first">Systemdirektiven zuerst sortieren</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_sort_system_directives_first`  |  C# und Visual Basic | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | System.*using-Direktiven alphabetisch sortieren und vor anderen using-Direktiven platzieren.| **C#:** <br>`using System.Collections.Generic;`<br> `using System.Threading.Tasks;`<br> `using Octokit;`
| False | Keine Anforderungen an die Reihenfolge von using-Direktiven. | **C#:** <br>`using System.Collections.Generic;`<br> `using Octokit;` <br> `using System.Threading.Tasks;`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
``` 

# <a name="csharp_formatting">C#-Formatierungseinstellungen</a>
## <a name="newline">Zeilenvorschuboptionen</a>
### <a name="newline_before_brace"> Zeilenvorschub vor öffnender Klammer (`{`)</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_open_brace`  |  C#  | alle | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung 
| ------------- |:-------------|
| accessors, anonymous_methods, anonymous_types, control_blocks, events, indexers, lambdas, local_functions, methods, object_collection, properties, types. (Trennen Sie mehrere Werte mit Komma). | Klammern müssen für die angegebenen Ausdrücke in einer neuen Zeile stehen (Allman-Stil). |
| alle | Klammern müssen für alle Ausdrücke in einer neuen Zeile stehen (Allman). |
| Keine | Klammern müssen für alle Ausdrücke in der gleichen Zeile stehen (K&R). |

#### <a name="applied"></a>Angewendet:
```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}
```

```csharp
// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
``` 

### <a name="newline_before_else"> Zeilenvorschub vor `else`</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_else` |  C#  | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung 
| ------------- |:-------------|
| True | `else`-Anweisungen in einer neuen Zeile platzieren.  |
| False | `else`-Anweisungen in der gleichen Zeile platzieren.  |

#### <a name="applied"></a>Angewendet:
```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}
```

```csharp
// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_else = true
``` 

### <a name="newline_before_catch"> Zeilenvorschub vor `catch`</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_catch`|  C#  | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung 
| ------------- |:-------------|
| True | `catch`-Anweisungen in einer neuen Zeile platzieren.  |
| False | `catch`-Anweisungen in der gleichen Zeile platzieren. |

#### <a name="applied"></a>Angewendet:
```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}
```

```csharp
// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_catch = true
``` 

### <a name="newline_before_finally"> Zeilenvorschub vor `finally`</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_finally`|  C#  | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung 
| ------------- |:-------------|
| True | `finally`-Anweisungen müssen nach der schließenden Klammer in einer neuen Zeile stehen.  |
| False | `finally`-Anweisungen müssen nach der schließenden Klammer in der gleichen Zeile stehen.  |

#### <a name="applied"></a>Angewendet:
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
```

```csharp
// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_finally = true
``` 

### <a name="newline_before_object">Zeilenvorschub vor Membern in Objektinitialisierern</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_object_initializers`|  C#  | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung 
| ------------- |:-------------|
| True | Member von Objektinitialisierern müssen in separaten Zeilen stehen.  |
| False | Member von Objektinitialisierern müssen in der gleichen Zeile stehen.  |

#### <a name="applied"></a>Angewendet:
```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_object_initializers = true
``` 

### <a name="newline_before_anonymous"> Zeilenvorschub vor Membern in anonymen Typen</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_anonymous_types` |  C#  | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung 
| ------------- |:-------------|
| True | Member von anonymen Typen müssen in separaten Zeilen stehen.  |
| False | Member von anonymen Typen müssen in der gleichen Zeile stehen.  |

#### <a name="applied"></a>Angewendet:
```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_anonymous_types = true
``` 

### <a name="newline_before_query"> Zeilenvorschub vor Membern in Abfrageausdrucksklauseln</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_within_query_expression_clauses`  |  C#  | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung 
| ------------- |:-------------|
| True | Elemente von Abfrageausdrucksklauseln müssen in separaten Zeilen stehen.  |
| False | Elemente von Abfrageausdrucksklauseln müssen in der gleichen Zeile stehen.  |

#### <a name="applied"></a>Angewendet:
```csharp
// csharp_new_line_within_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;
```

```csharp
// csharp_new_line_within_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_within_query_expression_clauses = true
``` 

## <a name="indent">Einzugsoptionen</a>
### <a name="indent_switch">`switch` Case-Inhalte einrücken </a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_case_contents`  |  C#  | true | Visual Studio 2017 V. 15.3  |

| Wert | Beschreibung 
| ------------- |:-------------|
| True | `switch` Case-Inhalte einrücken.  |
| False | `switch` Case-Inhalte nicht einrücken. |

#### <a name="applied"></a>Angewendet:
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
```

```csharp
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

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
``` 

### <a name="indent_switch_labels">`switch`-Bezeichner einrücken</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_switch_labels`  |  C#  | true | Visual Studio 2017 V. 15.3  |

| Wert | Beschreibung 
| ------------- |:-------------|
| True | `switch`-Bezeichner einrücken  |
| False | `switch`-Bezeichner nicht einrücken |

#### <a name="applied"></a>Angewendet:
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
```

```csharp
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

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_switch_labels = true
``` 

### <a name="label">Positionierung von Bezeichnungen</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_indent_labels`  |  C#  | one_less | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung 
| ------------- |:-------------|
| one_less | Bezeichnungen werden mit geringerem Einzug platziert als der aktuelle Kontext. |
| no_change | Bezeichnungen werden mit dem gleichen Einzug platziert wie der aktuelle Kontext. |

#### <a name="applied"></a>Angewendet:
```csharp
// csharp_indent_labels = one_less
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
error:
    throw new Exception(...);
}

```

```csharp
// csharp_indent_labels= no_change
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
    error:
    throw new Exception(...);
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_labels = one_less
``` 

## <a name="spacing">Leerzeichenoptionen</a>
### <a name="space_after_cast"> Leerzeichen nach Typumwandlung </a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_cast` |  C#  | false | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung | Angewendet |
| ------------- |:-------------|:-------------|
| True | Zwischen Typumwandlung und Wert muss sich ein Leerzeichen befinden.  | **C#:** <br>`int y = (int) x;`
| False | Zwischen Typumwandlung und Wert muss sich kein Leerzeichen befinden. | **C#:** <br>`int y = (int)x;`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
``` 

### <a name="space_control_flow"> Leerezeichen nach Schlüsselwörtern in Ablaufsteuerungsanweisungen</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_keywords_in_control_flow_statements` |  C#  | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung | Angewendet |
| ------------- |:-------------|:-------------|
| True | Nach einem Schlüsselwort muss sich ein Leerzeichen befinden. | **C#:** <br>`for (int i;i<x;i++) { ... }`
| False | Nach einem Schlüsselwort muss sich kein Leerzeichen befinden. | **C#:** <br>`for(int i;i<x;i++) { ... }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_keywords_in_control_flow_statements = true
``` 

### <a name="space_parameter_list"> Leerzeichen zwischen Klammern in Methodendeklarationsargument-Listen</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_between_method_declaration_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung | Angewendet |
| ------------- |:-------------|:-------------|
| True | Nach einem Schlüsselwort muss sich ein Leerzeichen befinden. | **C#:** <br>`void Bark( int x ) { ... }`
| False | Nach einem Schlüsselwort muss sich kein Leerzeichen befinden. | **C#:** <br>`void Bark(int x) { ... }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_declaration_parameter_list_parentheses = true
```

### <a name="space_method_call"> Leerzeichen innerhalb von Klammern in Methodenaufrufargument-Listen</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_method_call_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung | Angewendet |
| ------------- |:-------------|:-------------|
| true | Leerzeichen zwischen Klammern von Ablaufsteuerungsanweisungen einfügen. | **C#:** <br>`MyMethod( argument );`
| false | Leerzeichen zwischen Klammern von Ausdrücken einfügen. | **C#:** <br>`MyMethod(argument);`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_call_parameter_list_parentheses = control_flow_statements, type_casts
```  

### <a name="space_other"> Leerzeichen innerhalb von Klammern für andere Optionen </a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_parentheses`  |  C#  | false | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung | Angewendet |
| ------------- |:-------------|:-------------|
| control_flow_statements | Leerzeichen zwischen Klammern von Ablaufsteuerungsanweisungen einfügen. | **C#:** <br>`for( int i;i<x;i++ ) { ... }`
| Ausdrücke | Leerzeichen zwischen Klammern von Ausdrücken einfügen. | **C#:** <br>`var z = ( x * y ) - ( ( y - x ) * 3);`
| type_casts | Leerzeichen zwischen Klammern in Typumwandlungen einfügen. | **C#:**<br>`int y = ( int )x;`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

## <a name="wrapping">Umbruchoptionen</a>
### <a name="wrapping_statement">Anweisungen und Memberdeklarationen in der gleichen Zeile belassen</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_preserve_single_line_statements`   |  C#  | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung |
| ------------- |:-------------|
| True | Anweisungen und Memberdeklarationen in der gleichen Zeile belassen.  | 
| False | Anweisungen und Memberdeklarationen in verschiedenen Zeilen belassen. | 

#### <a name="applied"></a>Angewendet
```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";
```

```csharp
//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
``` 

### <a name="wrapping_block">Block in einzelner Zeile belassen</a>
| **Name der Option** | **Betroffene Sprachen** | **Visual Studio-Standard** | **Unterstützte Version** |
| ----------- | -------------------- | ----------------------| ----------------  |
|   `csharp_preserve_single_line_blocks`    |  C#  | true | Visual Studio 2017 V. 15.3  |


| Wert | Beschreibung |
| ------------- |:-------------|
| True | Block in einzelner Zeile belassen. | 
| False | Block in separaten Zeilen belassen. | 

#### <a name="applied"></a>Angewendet
```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }
```

```csharp
//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_blocks = true
``` 

# <a name="naming"> Benennungskonventionen </a>
## <a name="overview"></a>Übersicht
**Regelformat:**<br>
namingRuleTitle:<br>
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`<br>
<br>
symbolTitle:<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter`<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = public, internal, private, protected, protected_internal`<br>
`dotnet_naming_symbols.<symbolTitle>.required_modifiers = abstract, async, const, readonly, static`<br>
<br>
styleTitle:<br>
`dotnet_naming_style.<styleTitle>.capitalization = pascal_case|camel_case|first_word_upper|all_upper|all_lower`<br>
`dotnet_naming_style.<styleTitle>.required_prefix = string`<br>
`dotnet_naming_style.<styleTitle>.required_suffix = string`<br>
`dotnet_naming_style.<styleTitle>.word_separator = string`<br>

## <a name="writing-a-naming-convention"></a>Schreiben einer Benennungskonvention
Bei Benennungskonventionen müssen Sie **Symbole**, das **Format** und einen **Schweregrad** angeben. Benennungskonventionen sollten von der spezifischsten zur allgemeinsten sortiert werden. Die erste Regel, die angewendet werden kann, ist die einzige Regel, die angewendet wird. 

### <a name="severity"></a>Schweregrad
Dies sind gültige Optionen für den Schweregrad einer Regel für das Benennungsformat: `none`, `silent`, `suggestion`, `warning`, `error`.

 `none` und `silent` sind synonym und bedeuten, dass dem Benutzer keinerlei Hinweis angezeigt werden soll. Damit wird diese Regel im Endeffekt deaktiviert.

 `suggestion` bedeutet, dass dem Benutzer in der Fehlerliste und der IDE ein Vorschlag angezeigt wird. Der Schweregrad `suggestion` lässt die Ausführung der Benennungsregel zu, führt jedoch nicht zu einer Unterbrechung des Buildvorgangs.

Schweregrad | Wirkung
------------ | -------------
none/silent | Dem Benutzer nichts anzeigen, wenn dieses Format nicht eingehalten wird, die Funktionen der Codegenerierung werden allerdings in diesem Format erstellt. 
Vorschlag | Wenn dieses Format nicht eingehalten wird, dies dem Benutzer als Vorschlag (zwei unterlegte Punkte auf den ersten beiden Zeichen) anzeigen.
warning | Wenn dieses Format nicht eingehalten wird, eine Compilerwarnung anzeigen.
error | Wenn dieses Format nicht eingehalten wird, einen Compilerfehler anzeigen.

### <a name="symbol-specification"></a>Symbolspezifikation
Bestimmen Sie, auf _welche_ Symbole _mit welchen_ Modifizierern _und auf welcher_ Zugriffsebene die Benennungsregel angewendet werden soll.

|  Name der Option | `dotnet_naming_rule.<namingRuleTitle>.symbols` |
| ------------- |:-------------:|
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_kinds`
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities`
|  | `dotnet_naming_symbols.<symbolTitle>.required_modifiers`

| Symbol | Barrierefreiheit | Modifizierer
| ------------- |------------- |------------- |
| `*` | `*` |  `abstract` | 
| `class` | `public` |  `must_inherit` | `async` | 
| `struct` | `internal` (C#) /  | `const` | 
| `interface` | `friend` (Visual Basic) | `readonly` | 
| `enum` | `private`  | `static` | 
| `property` | `protected` | `shared` |
| `method` |`protected_internal` (C#) | |
| `field` | `protected_friend` (Visual Basic) | |
| `event` | | |
| `delegate` | | |


### <a name="style-specification"></a>Formatangabe
Bestimmen Sie das Benennungsformat, das auf die Symbole angewendet werden soll.

|  Name der Option | `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>` |
| ------------- |:-------------:|
|  | `dotnet_naming_style.<styleTitle>.capitalization`|
|  | `dotnet_naming_style.<styleTitle>.required_prefix`|
|  | `dotnet_naming_style.<styleTitle>.required_suffix`|
|  | `dotnet_naming_style.<styleTitle>.word_separator`|


| Stil | Beschreibung |
| ------------- |:-------------:|
| Präfix | Erforderliche Zeichen, die vor dem Bezeichner angezeigt werden müssen. |
| Suffix | Erforderliche Zeichen, die nach dem Bezeichner angezeigt werden müssen. |
| Worttrennzeichen | Erforderliches Trennzeichen zwischen Wörtern im Bezeichner. |
| Großbuchstaben |`pascal_case`, `camel_case`, `first_word_upper`, `all_upper`, `all_lower` | 


### <a name="example-naming-convention"></a>Beispiel für Benennungskonvention
```
# Dotnet Naming Conventions
[*.{cs,vb}] 
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

