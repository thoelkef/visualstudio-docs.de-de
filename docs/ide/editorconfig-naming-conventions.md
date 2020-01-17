---
title: .NET-Namenskonventionen für EditorConfig-Dateien
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5c4115f4d63456e105fb4a6770fd1650938770d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588602"
---
# <a name="net-naming-conventions-for-editorconfig"></a>.NET-Namenskonventionen für EditorConfig

Namenskonventionen beziehen sich auf die Benennung von Codeelementen wie z.B. Klassen, Eigenschaften und Methoden. Sie können beispielsweise angeben, dass öffentliche Mitglieder großgeschrieben werden oder dass private Felder mit `_` beginnen müssen. Sie können diese Regeln erzwingen, indem Sie sie in einer [.editorconfig](../ide/create-portable-custom-editor-options.md)-Datei angeben. Verletzungen von Namensregeln erscheinen entweder in der **Fehlerliste** oder als Vorschlag unter dem Namen, je nachdem, welchen Schweregrad Sie für Ihre Regel wählen. Es besteht keine Notwendigkeit, einen Build des Projekts zu erstellen, um Verstöße zu erkennen.

Bei jeder Namenskonvention müssen Sie die Symbole, für die sie gilt, einen Benennungsstil und einen Schweregrad zum Erzwingen der Konvention mithilfe der nachstehend beschriebenen Eigenschaften angeben. Die Reihenfolge der Eigenschaften ist ohne Bedeutung.

Wählen Sie zunächst einen Titel für Ihre Namensregel, den Sie in jeder der Eigenschaften verwenden werden, die zur vollständigen Beschreibung der Regel erforderlich sind. Beispielsweise ist `public_members_must_be_capitalized` ein guter, beschreibender Name für eine Benennungsregel. Die folgenden Abschnitte dieser Seite beziehen sich auf den von Ihnen als **<namingRuleTitle\>** gewählten Titel.

## <a name="symbols"></a>Symbole

Identifizieren Sie zuerst eine Gruppe von Symbolen, für die die Benennungsregel gelten soll. Diese Eigenschaft hat das folgende Format:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Geben Sie der Gruppe von Symbolen einen Namen, indem Sie den Wert **<symbolTitle\>** durch einen beschreibenden Titel ersetzen, z.B. `public_symbols`. Sie verwenden den Wert **<symbolTitle\>** in den drei Eigenschaftsnamen, die beschreiben, für welche Symbole die Regel gilt (Symbolarten, Zugriffsebenen und Modifizierer).

### <a name="kinds-of-symbols"></a>Symbolarten

Um die Art der Symbole zu beschreiben, für die die Namensregel gelten soll, geben Sie eine Eigenschaft im folgenden Format an:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

In der folgenden Liste werden die zulässigen Werte aufgelistet. Sie können mehrere Werte angeben, indem Sie sie durch ein Komma trennen.

- \* (verwenden Sie diesen Wert, um alle Symbole anzugeben)
- namespace
- class
- struct
- interface
- enum
- property
- Methode
- Feld
- event
- delegate
- -Parameter von
- type_parameter
- Lokal
- local_function

### <a name="accessibility-levels-of-symbols"></a>Zugriffsebenen von Symbolen

Um die Zugriffsebenen der Symbole zu beschreiben, für die die Namensregel gelten soll, geben Sie einen Eigenschaftsnamen im folgenden Format an:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

In der folgenden Liste werden die zulässigen Werte aufgelistet. Sie können mehrere Werte angeben, indem Sie sie durch ein Komma trennen.

- \* (verwenden Sie diesen Wert, um alle Zugriffsebenen anzugeben)
- public
- „internal“ oder „friend“
- private
- protected
- „protected\_internal“ oder „protected_friend“
- private\_protected
- Lokal

   Die `local`-Zugriffsebene gilt für Symbole, die innerhalb einer Methode definiert sind. Dies ist nützlich bei der Definition von Namenskonventionen für Symbole, deren Barrierefreiheit nicht im Code angegeben werden kann. Wenn Sie beispielsweise `applicable_accessibilities = local` auf einer Benennungskonvention für Konstanten (`required_modifiers = const`) angeben, gilt die Regel nur für Konstanten, die innerhalb einer Methode definiert sind, und nicht für solche, die in einem Typ definiert sind.

   ```csharp
   class TypeName
   {
     // Constant defined in a type.
     const int X = 3;

     void Method()
     {
       // Constant defined in a method with "local" accessibility.
       const int Y = 4;
     }
   }
   ```

### <a name="symbol-modifiers-optional"></a>Symbolmodifizierer (optional)

Um die Modifizierer der Symbole zu beschreiben, für die die Namensregel gelten soll, geben Sie einen Eigenschaftsnamen im folgenden Format an:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

In der folgenden Liste werden die zulässigen Werte aufgelistet (Trennen Sie mehrere Werte durch ein Komma):

- `abstract` oder `must_inherit`
- `async`
- `const`
- `readonly`
- `static` oder `shared`

   > [!NOTE]
   > Wenn Sie eine Benennungsregel für `static`- oder `shared`- Symbole haben, wird sie auch auf `const`-Symbole angewendet, da sie implizit statisch sind. Wenn Sie nicht möchten, dass die `static`-Benennungsregel auf `const`-Symbole angewendet wird, erstellen Sie eine separate Benennungsregel für `const`-Symbole.

Eine Namensregel stimmt mit den Signaturen überein, die *alle* Modifizierer besitzen, die in `required_modifiers` festgelegt sind. Wenn Sie diese Eigenschaft nicht bestimmen, wird der Standardwert einer leeren Liste verwendet, d. h. keine bestimmten Modifizierer werden für eine Übereinstimmung benötigt. Das bedeutet, dass die Modifizierer eines Symbols keine Auswirkungen darauf haben, ob die Regel angewendet wird oder nicht.

> [!TIP]
> Geben Sie nicht den Wert `*` für `required_modifiers` ein. Lassen Sie die Eigenschaft `required_modifiers` einfach weg. Ihre Benennungsregel gilt dann für alle Modifizierer.

## <a name="style"></a>Stil

Nachdem Sie die Gruppe von Symbolen bestimmt haben, für die die Benennungsregel gelten soll, können Sie den Benennungsstil beschreiben. Ein Stil kann vorgeben, dass der Name ein bestimmtes Präfix oder ein bestimmtes Suffix hat oder dass einzelne Wörter im Namen durch ein bestimmtes Zeichen getrennt sind. Sie können auch einen Groß-/Kleinschreibungsstil angeben. Die Stileigenschaft hat das folgende Format:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Geben Sie dem Stil einen Namen, indem Sie den Wert **<styleTitle\>** durch einen beschreibenden Titel ersetzen, z.B. `first_word_upper_case_style`. Sie verwenden den Wert **<styleTitle\>** in den Eigenschaftsnamen, die den Benennungsstil beschreiben (Präfix, Suffix, Worttrennzeichen und Groß-/Kleinschreibung). Verwenden Sie eine oder mehrere dieser Eigenschaften, um Ihr Format zu beschreiben.

### <a name="require-a-prefix"></a>Ein Präfix anfordern

Um festzulegen, dass Symbolnamen mit bestimmten Zeichen beginnen müssen, verwenden Sie diese Eigenschaft:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Ein Suffix anfordern

Um festzulegen, dass Symbolnamen mit bestimmten Zeichen enden müssen, verwenden Sie diese Eigenschaft:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Ein bestimmtes Worttrennzeichen anfordern

Um festzulegen, dass einzelne Wörter in Symbolnamen durch ein bestimmtes Zeichen getrennt werden müssen, verwenden Sie diese Eigenschaft:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Einen Groß-/Kleinschreibungsstil anfordern

Verwenden Sie diese Eigenschaft, um einen bestimmten Groß- und Kleinschreibungsstil für Symbolnamen anzugeben:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Folgende Werte sind für diese Eigenschaft zulässig:

- pascal_case
- camel_case
- first\_word_upper
- all\_upper
- all_lower

> [!NOTE]
> Sie müssen im Rahmen Ihres Benennungsstils einen Stil für die Groß-/Kleinschreibung angeben. Andernfalls wird Ihr Benennungsstil möglicherweise ignoriert.

## <a name="severity"></a>Schweregrad

Um den Schweregrad eines Verstoßes gegen Ihre Benennungsregel zu beschreiben, geben Sie eine Eigenschaft im folgenden Format an:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

Die folgende Tabelle zeigt die zulässigen Schweregrade und ihre Bedeutung:

Schweregrad | Effekt
------------ | -------------
Keine | Die Regel wird vollständig unterdrückt.
Refactoring oder unbeaufsichtigt | Wenn dieses Format nicht befolgt wird, wird der Benutzer nicht benachrichtigt. Automatisch generierter Code folgt jedoch diesem Format.
Vorschlag | Wenn dieses Format nicht eingehalten wird, dies dem Benutzer als Vorschlag (zwei unterlegte Punkte bei den ersten beiden Zeichen) anzeigen. Dies hat zur Kompilierzeit keine Auswirkungen.
warning | Wenn dieses Format nicht eingehalten wird, eine Compilerwarnung in der **Fehlerliste** anzeigen.
error | Wenn dieses Format nicht eingehalten wird, einen Compilerfehler in der **Fehlerliste** anzeigen.

> [!NOTE]
> Sie müssen keinen Build für Ihr Projekt durchführen, damit Namensregelverstöße angezeigt werden. Sie werden bei der Bearbeitung des Codes angezeigt, entweder in der **Fehlerliste** oder als Vorschlag.

## <a name="rule-order"></a>Regelreihenfolge

::: moniker range="vs-2017"

Namenskonventionen sollten in der EditorConfig-Datei von der spezifischsten zur allgemeinsten sortiert werden. Die erste Regel, die angewendet werden kann, ist die einzige Regel, die angewendet wird. Wenn es jedoch mehrere *Regeleigenschaften* mit dem gleichen Namen gibt, hat die zuletzt gefundene Eigenschaft mit diesem Namen Vorrang. Weitere Informationen finden Sie unter [Dateihierarchie und Rangfolge](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

Ab Visual Studio 2019 Version 16.2 spielt die Reihenfolge, in der Benennungsregeln in einer EDITORCONFIG-Datei definiert werden, keine Rolle. Stattdessen ordnet Visual Studio die Benennungsregeln automatisch entsprechend der Definition der Regeln selbst. Die Erweiterung [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) kann eine EditorConfig-Datei analysieren und Fälle melden, in denen sich die Regelreihenfolge in der Datei von der Reihenfolge unterscheidet, die vom Compiler zur Laufzeit verwendet wird.

Wenn Sie eine frühere Version von Visual Studio verwenden, sollten Namenskonventionen in der EDITORCONFIG-Datei von der spezifischsten zur allgemeinsten sortiert werden. Die erste Regel, die angewendet werden kann, ist die einzige Regel, die angewendet wird. Wenn es jedoch mehrere *Regeleigenschaften* mit dem gleichen Namen gibt, hat die zuletzt gefundene Eigenschaft mit diesem Namen Vorrang. Weitere Informationen finden Sie unter [Dateihierarchie und Rangfolge](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Standardbenennungsstile

Wenn Sie keine benutzerdefinierten Benennungsregeln angeben, verwendet Visual Studio die folgenden Standardstile:

- Bei Klassen, Strukturen, Enumerationen, Eigenschaften und Ereignissen mit `public`-, `private`-, `internal`-, `protected`- oder `protected_internal`-Zugriff, ist der standardmäßige Benennungsstil die Pascal-Schreibweise.

- Bei Schnittstellen mit `public`-, `private`-, `internal`-, `protected`- oder `protected_internal`-Zugriff ist der standardmäßige Benennungsstil die Pascal-Schreibweise mit dem erforderlichen Präfix **I**.

## <a name="example"></a>Beispiel

Die folgende *EDITORCONFIG-Datei* enthält eine Namenskonvention, die angibt, dass öffentliche Eigenschaften, Methoden, Felder, Ereignisse und Delegaten großgeschrieben werden müssen. Beachten Sie, dass diese Namenskonvention mehrere Arten von Symbolen angibt, für die die Regel gelten soll, wobei die Werte durch ein Komma getrennt werden.

```ini
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

Der folgende Screenshot zeigt die Auswirkung dieser Namenskonvention im Editor. Zwei öffentliche Variablen wurden ohne Großschreibung des ersten Buchstabens benannt. Die eine ist `const` und die andere `readonly`. Da die Benennungsregel nur für `readonly`-Symbole gilt, wird nur in der Variablen `readonly` ein Vorschlag für eine Benennungsregel angezeigt.

![Vorschlag für Namensregel](media/editorconfig-naming-rule-suggestion.png)

Lassen Sie uns nun den Schweregrad des Verstoßes in `warning` ändern:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Wenn Sie Ihre Codedatei schließen und wieder öffnen, sehen Sie statt des Vorschlags unter dem Namensverstoß eine grüne Wellenlinie und eine Warnung in der Fehlerliste:

![Namensregelwarnung](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Siehe auch

- [Sprachkonventionen](editorconfig-language-conventions.md)
- [Formatierungskonventionen](editorconfig-formatting-conventions.md)
- [Roslyn-Namenskonventionen](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Erstellen portierbarer benutzerdefinierter Editor-Optionen](../ide/create-portable-custom-editor-options.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](editorconfig-code-style-settings-reference.md)
