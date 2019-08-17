---
title: Code Analyse Warnungen unterdrücken
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 60fcb13c978d614d40964bd8d6da21e8cf41f00f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551074"
---
# <a name="suppress-code-analysis-warnings"></a>Code Analyse Warnungen unterdrücken

Häufig ist es hilfreich, anzugeben, dass eine Warnung nicht anwendbar ist. Dies weist Teammitgliedern an, dass der Code überprüft wurde und dass die Warnung unterdrückt werden kann. In-Source-Unterdrückung (ISS) verwendet <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> das-Attribut, um eine Warnung zu unterdrücken. Das-Attribut kann in der Nähe des Code Segments platziert werden, das die Warnung generiert hat. Sie können das <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut zur Quelldatei hinzufügen, indem Sie es eingeben, oder Sie können das Kontextmenü für eine Warnung im **Fehlerliste** verwenden, um es automatisch hinzuzufügen.

Das <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut ist ein bedingtes Attribut, das in den IL-Metadaten der verwalteten Codeassembly enthalten ist, nur wenn das CODE_ANALYSIS-Kompilierungs Symbol zur Kompilierzeit definiert ist.

Verwenden C++Sie in/CLI die Makros\_der ZS\_-unter\_Unterdrückung oder\_der globalen SUPPRESS_MESSAGE der Zertifizierungsstelle in der Header Datei, um das-Attribut hinzuzufügen.

> [!NOTE]
> Sie sollten keine in-Source-Unterdrückungen für Releasebuilds verwenden, um zu verhindern, dass die in-Source-Unterdrückungs Metadaten versehentlich versendet werden. Außerdem kann die Leistung Ihrer Anwendung aufgrund der Verarbeitungskosten der in-Source-Unterdrückung beeinträchtigt werden.

> [!NOTE]
> Wenn Sie ein Projekt zu Visual Studio 2017 oder Visual Studio 2019 migrieren, kann es vorkommen, dass eine große Anzahl von Code Analyse Warnungen angezeigt wird. Wenn Sie die Warnungen nicht beheben können, können Sie alle unterdrücken, indem Sie **analysieren** > **Code Analyse ausführen und aktive Probleme unterdrücken**auswählen.
>
> ![Ausführen der Code Analyse und unterdrücken von Problemen in Visual Studio](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage-Attribut

Wenn Sie im **Fehlerliste**die Option unter **drücken** im Kontextmenü oder im Kontextmenü einer Code Analyse Warnung auswählen, wird <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> entweder im Code oder in der globalen Unterdrückungs Datei des Projekts ein-Attribut hinzugefügt.

Das <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut weist das folgende Format auf:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Zu den Eigenschaften des-Attributs gehören:

- **Kategorie** : die Kategorie, in der die Regel definiert ist. Weitere Informationen zu Code Analyse-Regel Kategorien finden Sie unter [Warnungen für verwalteten Code](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** : der Bezeichner der Regel. Die Unterstützung umfasst sowohl einen kurzen als auch einen langen Namen für den Regel Bezeichner. Der Kurzname ist "CAXXXX;". der lange Name ist "CAXXXX: friendlytykiame".

- **Begründung** : der Text, der verwendet wird, um den Grund für das Unterdrücken der Nachricht zu dokumentieren.

- **MessageId** : eindeutiger Bezeichner eines Problems für jede Nachricht.

- **Bereich** : das Ziel, für das die Warnung unterdrückt wird. Wenn das Ziel nicht angegeben ist, wird es auf das Ziel des Attributs festgelegt. Folgende [Bereiche](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) werden unterstützt:

  - `module`

  - `resource`

  - `type`

  - `member`

  - `namespace`: Dieser Bereich unterdrückt Warnungen für den Namespace selbst. Warnungen für Typen im-Namespace werden nicht unterdrückt.

  - `namespaceanddescendants`-(Neu in Visual Studio 2019) dieser Bereich unterdrückt Warnungen in einem Namespace und allen untergeordneten Symbolen. Der `namespaceanddescendants` Wert wird von der Legacy Analyse ignoriert.

- **Target** : ein Bezeichner, der verwendet wird, um das Ziel anzugeben, auf dem die Warnung unterdrückt wird. Er muss einen voll qualifizierten Elementnamen enthalten.

## <a name="suppressmessage-usage"></a>SuppressMessage-Verwendung

Code Analyse Warnungen werden auf der Ebene unterdrückt, auf <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> die das Attribut angewendet wird. Das-Attribut kann z. b. auf Assembly-, Modul-, Typ-, Element-oder Parameter Ebene angewendet werden. Dies dient dazu, die Unterdrückungs Informationen eng mit dem Code zu verknüpfen, in dem die Verletzung auftritt.

Die allgemeine Form der Unterdrückung schließt die Regel Kategorie und einen Regel Bezeichner ein, der eine optionale, lesbare Darstellung des Regel namens enthält. Beispiel:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Wenn für das Minimieren von in-Source-Unterdrückungs Metadaten strenge Leistungs Gründe vorliegen, kann der Regelname ausgelassen werden. Die Regel Kategorie und Ihre Regel-ID bilden zusammen einen ausreichend eindeutigen Regel Bezeichner. Beispiel:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Aus Gründen der Wartbarkeit wird das Weglassen des Regel namens nicht empfohlen.

## <a name="suppress-selective-violations-within-a-method-body"></a>Selektive Verstöße innerhalb eines Methoden Texts unterdrücken

Unterdrückungs Attribute können auf eine Methode angewendet werden, können aber nicht in einen Methoden Text eingebettet werden. Dies bedeutet, dass alle Verstöße gegen eine bestimmte Regel unterdrückt werden, wenn <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Sie das-Attribut der-Methode hinzufügen.

In einigen Fällen möchten Sie möglicherweise eine bestimmte Instanz des Verstoßes unterdrücken, sodass zukünftiger Code nicht automatisch von der Code Analyse Regel ausgenommen wird. Bestimmte Code Analyse Regeln ermöglichen dies, indem Sie die `MessageId` -Eigenschaft <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> des-Attributs verwenden. Im Allgemeinen berücksichtigen ältere Regeln für Verstöße für ein bestimmtes Symbol (eine lokale Variable oder einen Parameter) die `MessageId` Eigenschaft. [CA1500: variablenamesschuldnotmatchfieldnames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) ist ein Beispiel für eine solche Regel. Ältere Regeln für Verstöße gegen ausführbaren Code (nicht-Symbol) beachten jedoch nicht die `MessageId` -Eigenschaft. Außerdem wird die `MessageId` -Eigenschaft von .NET Compiler Platform ("Roslyn")-Analysen nicht beachtet.

Um eine bestimmte Symbol Verletzung einer Regel zu unterdrücken, geben Sie den Symbolnamen `MessageId` für die Eigenschaft <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> des Attributs an. Das folgende Beispiel zeigt Code mit zwei Verstößen gegen [CA1500: variablenamestiondnotmatchfieldnames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;eine für die `name` Variable und eine für die `age` Variable. Nur die Verletzung für das `age` Symbol wird unterdrückt.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>Generierter code

Compiler verwalteter Code und einige Tools von Drittanbietern generieren Code, um eine schnelle Code Entwicklung zu ermöglichen. Vom Compiler generierter Code, der in Quelldateien angezeigt wird, wird `GeneratedCodeAttribute` normalerweise mit dem-Attribut markiert.

Sie können auswählen, ob Warnungen und Fehler bei der Code Analyse für generierten Code unterdrückt werden sollen. Informationen dazu, wie Sie Warnungen und Fehler unterdrücken, finden [Sie unter Vorgehensweise: Warnungen für generierten Code](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)unterdrücken.

> [!NOTE]
> Die Code Analyse `GeneratedCodeAttribute` wird ignoriert, wenn Sie entweder auf eine gesamte Assembly oder einen einzelnen Parameter angewendet wird.

## <a name="global-level-suppressions"></a>Unterdrückungen auf globaler Ebene

Das Tool für die Analyse von `SuppressMessage` verwaltetem Code untersucht Attribute, die auf Assembly-, Modul-, Typ-, Element-oder Parameter Ebene angewendet werden. Außerdem werden Verstöße gegen Ressourcen und Namespaces ausgelöst. Diese Verstöße müssen auf globaler Ebene angewendet werden und sind auf einen Bereich beschränkt. Beispielsweise wird durch die folgende Meldung eine Namespace Verletzung unterdrückt:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Wenn Sie eine Warnung mit `namespace` dem Bereich unterdrücken, wird die Warnung gegen den Namespace selbst unterdrückt. Die Warnung wird nicht für Typen im-Namespace unterdrückt.

Alle Unterdrückungen können durch Angabe eines expliziten Bereichs ausgedrückt werden. Diese Unterdrückungen müssen auf globaler Ebene aktiv sein. Sie können die Unterdrückung auf Element Ebene nicht angeben, indem Sie einen Typ ergänzen.

Unterdrückungen auf globaler Ebene sind die einzige Möglichkeit, Nachrichten zu unterdrücken, die auf vom Compiler generierten Code verweisen, der der explizit bereitgestellten Benutzer Quelle nicht zugeordnet ist. Der folgende Code unterdrückt z. b. einen Verstoß gegen einen vom Compiler ausgegebenen Konstruktor:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target`enthält immer den voll qualifizierten Elementnamen.

## <a name="global-suppression-file"></a>Globale Unterdrückungs Datei

Die globale Unterdrückungs Datei verwaltet Unterdrückungen, bei denen es sich entweder um Unterdrückungen auf globaler Ebene oder um Unterdrückungen handelt, die kein Ziel angeben. Beispielsweise werden Unterdrückungen für Verstöße auf Assemblyebene in dieser Datei gespeichert. Außerdem werden einige ASP.net Unterdrückungen in dieser Datei gespeichert, da Einstellungen auf Projektebene für Code hinter einem Formular nicht verfügbar sind. Eine globale Unterdrückungs Datei wird erstellt und dem Projekt hinzugefügt, wenn Sie zum ersten Mal die Option **in Project Unterdrückungs Datei** des Befehls unter **drücken** im Fenster **Fehlerliste** auswählen.

## <a name="see-also"></a>Siehe auch

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Verwenden von Code Analysemodulen](../code-quality/use-roslyn-analyzers.md)
