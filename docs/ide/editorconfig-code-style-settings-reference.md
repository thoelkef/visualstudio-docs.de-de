---
title: ".NET-Codeformateinstellungen für „EditorConfig“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 01
author: kaseyu
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
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: a5b26ed093ed86c8c438b2024f69d371fde2de36
ms.lasthandoff: 03/27/2017

---

# <a name="net-code-style-settings-for-editorconfig"></a>.NET-Codeformateinstellungen für „EditorConfig“

## <a name="possible-values"></a>Mögliche Werte

`options_name = false|true : none|suggestion|warning|error`

Für Codeformatoptionen müssen Sie **wahr** (diese Option vorziehen) oder **falsch** (diese Option nicht vorziehen), einen Doppelpunkt (`:`) und einen Schweregrad (`none`, `suggestion`, `warning` oder `error`) angeben. Der Schweregrad bedeutet den Grad der Durchsetzung, den Sie für das betreffende Format in Ihrer Codebasis festlegen möchten.

Schweregrad | Wirkung
------------ | -------------
Keine | Dem Benutzer nichts anzeigen, wenn dieses Format nicht eingehalten wird, die Funktionen der Codegenerierung werden allerdings in diesem Format erstellt. 
Vorschlag | Wenn dieses Format nicht eingehalten wird, dies dem Benutzer als Vorschlag (zwei unterlegte Punkte auf den ersten beiden Zeichen) anzeigen.
warning | Wenn dieses Format nicht eingehalten wird, eine Compilerwarnung anzeigen.
error | Wenn dieses Format nicht eingehalten wird, einen Compilerfehler anzeigen.

## <a name="net-code-style-options"></a>.NET-Codeformatoptionen

- [Dotnet-Codeformateinstellungen](#this_and_me)
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
- [CSharp-Codeformateinstellungen](#csharp_codestyle)
    - ["var"](#var)
        - ["var" für integrierte Typen](#var_built_in)
        - ["var" wenn der Typ offensichtlich ist](#var_apparent)
        - ["var" an anderer Stelle](#var_elsewhere)
    - [Ausdruckskörpermember](#expression_bodied_members)
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
    - [Einstellungen für die NULL-Überprüfung](#null_checking)
        - [Throw-Ausdrücke](#null_checking_throw_expressions)
        - [Bedingte Delegataufrufe](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">"This.-" und "Me.-" Qualifikation</a>

### <a name="this_and_me_fields">Felder</a>

|  Name der Option | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für alle nicht statischen Felder, die in nicht statischen Methoden verwendet werden: Voranstellung von `this.` in C# oder `Me.` in Visual Basic bevorzugen. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** `Me.capacity = 0`
| False | Für alle nicht statischen Felder, die in nicht statischen Methoden verwendet werden: Keine Voranstellung von `this.` in C# oder `Me.` in Visual Basic bevorzugen. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** `capacity = 0`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Eigenschaften</a>

|  Name der Option | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für alle nicht statischen Eigenschaften, die in nicht statischen Methoden verwendet werden: Voranstellung von `this.` in C# oder `Me.` in Visual Basic bevorzugen.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** `Me.ID = 0`
| False | Für alle nicht statischen Eigenschaften, die in nicht statischen Methoden verwendet werden: *Keine* Voranstellung von `this.` in C# oder `Me.` in Visual Basic bevorzugen. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** `ID = 0`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```


### <a name="this_and_me_methods">Methoden</a>
|  Name der Option | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für alle nicht statischen Methoden, die innerhalb von nicht statischen Methoden aufgerufen werden: Voranstellung von `this.` in C# oder `Me.` in VB bevorzugen.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** `Me.Display()`
| False | Für alle nicht statischen Methoden, die innerhalb von nicht statischen Methoden aufgerufen werden: *Keine* Voranstellung von `this.` in C# oder `Me.` in VB bevorzugen. | **C#:** <br>`Display();` <br><br> **Visual Basic:** `Display()`


#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">Ereignisse</a>
|  Name der Option | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für alle nicht statischen Ereignisse, auf die von nicht statischen Methoden verwiesen wird: Voranstellung von `this.` in C# oder `Me.` in VB bevorzugen.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Me.Elapsed, AddressOf Handler`
| False | Für alle nicht statischen Ereignisse, auf die von nicht statischen Methoden verwiesen wird: *Keine* Voranstellung von `this.` in C# oder `Me.` in VB bevorzugen. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Sprachschlüsselwörter (int, string usw.) im Vergleich zu Framework-Typnamen für Typverweise</a>
### <a name="language_keywords_variables">Lokale Variablen, Parameter und Member</a>
|  Name der Option | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Für lokale Variablen, Parameter und Typmember bei Typen, die durch ein Sprachschlüsselwort (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) dargestellt werden können, die Verwendung des Schlüsselworts anstelle des Typnamens (`Int32`, `Int64` usw.) bevorzugen.| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Für lokale Variablen, Parameter und Typmember bei Typen, die durch ein Sprachschlüsselwort (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) dargestellt werden können, die Verwendung des Typnamens (`Int32`, `Int64` usw.) anstelle des Schlüsselworts bevorzugen.  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Memberzugriffsausdrücke</a>
|  Name der Option | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Immer das Schlüsselwort bevorzugen, wenn ein Memberzugriffsausdruck auf einen Typ mit Schlüsselwortdarstellung (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) angewendet wird.| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** `Dim local = Integer.MaxValue`
| False | Immer den Typnamen bevorzugen, wenn ein Memberzugriffsausdruck auf einen Typ mit Schlüsselwortdarstellung (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) angewendet wird. | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Einstellungen auf Ausdrucksebene</a>
### <a name="expression_level_object_initializers">Objektinitialisierer</a>
|  Name der Option | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Wenn möglich, die Initialisierung von Objekten mithilfe von Objektinitialisierern bevorzugen.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** `Dim c = New Customer() With { .Age = 21 }`
| False | Die Initialisierung von Objekten *nicht* mithilfe von Objektinitialisierern bevorzugen. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Auflistungsinitialisierer</a>
|  Name der Option | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Wenn möglich, die Initialisierung von Auflistungen mithilfe von Auflistungsinitialisierern bevorzugen.| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | Die Initialisierung von Auflistungen *nicht* mithilfe von Auflistungsinitialisierern bevorzugen. | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">Explizite Tupelnamen</a>
|  Name der Option | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Tupelnamen gegenüber ItemX-Eigenschaften bevorzugen.| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | ItemX-Eigenschaften gegenüber Tupelnamen bevorzugen. | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">Sammelausdrücke in der NULL-Überprüfung</a>
|  Name der Option | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Sammelausdrücke in der NULL-Überprüfung gegenüber ternärer Operatorüberprüfung bevorzugen.| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | Ternäre Operatorüberprüfung gegenüber NULL-Sammelausdrücken bevorzugen. | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">NULL-Weitergabe in der NULL-Überprüfung</a>
|  Name der Option | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | C# und Visual Basic

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Wenn möglich, die Verwendung von NULL-Bedingungsoperatoren bevorzugen.| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | Wenn möglich, die Verwendung von ternärer NULL-Überprüfung bevorzugen. | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">CSharp-Codeformateinstellungen</a>
## <a name="var">"var"</a>
### <a name="var_built_in">"var" für integrierte Typen</a>
|  Name der Option | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

### <a name="var_apparent">"var" wenn der Typ offensichtlich ist</a>
|  Name der Option | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

### <a name="var_elsewhere">"var" an anderer Stelle</a>
|  Name der Option | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

### <a name="expression_bodied_members">Methoden</a>
|  Name der Option | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

### <a name="expression_bodied_members_constructors">Konstruktoren</a>
|  Name der Option | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

### <a name="expression_bodied_members_operators">Operatoren</a>
|  Name der Option | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

### <a name="expression_bodied_members_properties">Eigenschaften</a>
|  Name der Option | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Ausdruckskörpermember für Eigenschaften bevorzugen.| **C#:** <br>`public int Age => _age;`
| False | Vermeidung von Ausdruckskörpermembern für Eigenschaften bevorzugen.| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="expression_bodied_members_indexers">Indexer</a>
|  Name der Option | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

### <a name="expression_bodied_members_accessors">Zugriffsmethoden</a>
|  Name der Option | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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
### <a name="pattern_matching_is_cast">"is" mit Umwandlungsüberprüfung</a>
|  Name der Option | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

### <a name="pattern_matching_as_null">"as" mit NULL-Überprüfung</a>
|  Name der Option | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

### <a name="inlined_variable_declarations">Inline-Variablendeklarationen</a>
|  Name der Option | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

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

## <a name="null_checking">Einstellungen für die NULL-Überprüfung</a>
### <a name="null_checking_throw_expressions">Throw-Ausdrücke</a>
|  Name der Option | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Die Verwendung von Throw-Ausdrücken anstelle von Throw-Anweisungen bevorzugen. | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | Die Verwendung von Throw-Anweisungen anstelle von Throw-Ausdrücken bevorzugen.| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">Bedingte Delegataufrufe bevorzugen</a>
|  Name der Option | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **Betroffene Sprachen** | A#

| Wert | Beschreibung | Angewendet 
| ------------- |:-------------|:-------------|
| True | Die Verwendung eines bedingten Sammelvorgangs (`?.`) beim Aufruf eines Lambda-Ausdrucks anstelle einer NULL-Überprüfung bevorzugen. | **C#:** <br>`func?.Invoke(args);`
| False | Die Ausführung einer NULL-Überprüfung vor dem Aufrufen eines Lambda-Ausdrucks anstelle der Verwendung des bedingten Sammeloperators (`?.`) bevorzugen.| **C#:** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>Editorconfig-Beispieldatei:
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

