---
title: Unterdrücken von codeanalysewarnungen
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 1e90de7acf13ca28a20a35aa3ad3e70f58780279
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513045"
---
# <a name="suppress-code-analysis-warnings"></a>Unterdrücken von codeanalysewarnungen

Es ist häufig nützlich, um anzugeben, dass eine Warnung nicht anwendbar ist. Dies gibt an, für Teammitglieder, die der Code überprüft wurde, und kann die Warnung unterdrückt werden. Im Quellcode Unterdrückung (ISS) verwendet die <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut, um eine Warnung zu unterdrücken. Das Attribut kann in der Nähe der Codesegment platziert werden, die die Warnung generiert hat. Hinzufügbaren den <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut zur Quelldatei, indem Sie eingeben, oder Sie können das Kontextmenü für eine Warnung in der **Fehlerliste** es automatisch hinzuzufügen.

Die <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut ist ein conditional-Attribut, das in der Assembly mit verwaltetem Code, den IL-Metadaten enthalten ist, nur dann, wenn das Symbol für die CODE_ANALYSIS-Kompilierung zum Zeitpunkt der Kompilierung definiert wird.

In C++ / CLI, verwenden Sie die Makros Zertifizierungsstelle\_UNTERDRÜCKEN\_Nachricht oder einer Zertifizierungsstelle\_GLOBAL\_SUPPRESS_MESSAGE in der Headerdatei, um das Attribut hinzuzufügen.

> [!NOTE]
> Sie sollten nicht im Quellcode-Unterdrückungen für Releasebuilds verwenden, um zu verhindern, dass die Metadaten für die Unterdrückung im Quellcode versehentlich Protokollversand. Darüber hinaus kann aufgrund der Verarbeitungskosten Unterdrückung im Quellcode, die Leistung Ihrer Anwendung beeinträchtigt werden.

> [!NOTE]
> Wenn Sie ein Projekt in Visual Studio 2017 migrieren, können Sie plötzlich eine große Anzahl von Warnungen der Codeanalyse ausgesetzt sind. Diese Warnungen stammen [Roslyn-Analysetools](roslyn-analyzers-overview.md). Wenn Sie nicht bereit, die Warnungen zu beheben sind, können Sie alle unterdrücken, indem auswählen **analysieren** > **Codeanalyse ausführen und aktive Probleme unterdrücken**.
>
> ![Ausführen der Codeanalyse und Unterdrücken von Problemen in Visual Studio](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage-Attribut

Bei der Auswahl **unterdrücken** aus dem Kontextmenü per Rechtsklick öffnen, der eine codeanalysewarnung in die **Fehlerliste**, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut wird entweder in Ihrem Code oder globale Unterdrückung des Projekts hinzugefügt. die Datei.

Die <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut weist das folgende Format:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Die Eigenschaften des Attributs gehören:

- **Kategorie** -die Kategorie, in dem die Regel definiert wird. Weitere Informationen zu Codeanalyseregeln, finden Sie unter [Managed Code (Warnungen)](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** – der Bezeichner der Regel. Die Unterstützung umfasst sowohl eine kurze und lange Namen für die Regel-ID an. Der kurze Name ist CAXXXX; der lange Name ist CAXXXX:FriendlyTypeName.

- **Begründung** -der Text, der verwendet wird, um den Grund für das Unterdrücken der Meldung dokumentieren.

- **MessageId** – Eindeutiger Bezeichner für ein Problem für jede Nachricht.

- **Bereich** -Ziel auf dem die Warnung unterdrückt wird. Wenn das Ziel nicht angegeben ist, wird es an das Ziel des Attributs festgelegt. Die folgenden: Bereiche werden unterstützt

    - Modul

    - Namespace

    - Ressource

    - Typ

    - Member

- **Ziel** – ein Bezeichner, der verwendet wird, an das Ziel, auf dem die Warnung unterdrückt wird. Es muss eine vollständig qualifizierte Elementnamen enthalten.

## <a name="suppressmessage-usage"></a>SuppressMessage-Nutzung

Warnungen der Codeanalyse unterdrückt werden, auf der Ebene, der die <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut angewendet wird. Beispielsweise kann das Attribut auf die Assembly, Modul, Typ, Member oder Parameter-Ebene angewendet werden. Das Zweck dieses werden eng gekoppelt die Unterdrückungsinformationen aus, um den Code, in dem die Verletzung auftritt.

Die allgemeine Form der Unterdrückung umfasst die Regelkategorie und eine Regel-ID, die eine optionale lesbare Darstellung der Regelname enthält. Zum Beispiel:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Wenn strenge Leistungsgründen minimieren die Unterdrückung im Quellcode-Metadaten sind, kann der Name der ausgelassen werden. Die Regelkategorie und die Regel-ID bilden zusammen einen ausreichend eindeutigen Regelbezeichner. Zum Beispiel:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Aus Gründen der Verwaltbarkeit wird das Auslassen der Name der Regel nicht empfohlen.

## <a name="suppress-selective-violations-within-a-method-body"></a>Selektive Verstöße innerhalb eines Methodentexts unterdrücken

Unterdrückung-Attribut können auf eine Methode angewendet werden, aber es können nicht innerhalb eines Methodentexts eingebettet werden. Dies bedeutet, dass alle Verstöße gegen eine bestimmte Regel unterdrückt werden, wenn Sie beim Hinzufügen der <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut auf die Methode.

In einigen Fällen empfiehlt es sich möglicherweise auf eine bestimmte Instanz des Verstoßes, z. B. zu unterdrücken, sodass zukünftiger Code nicht automatisch die Codeanalyse-Regelsätze ausgeschlossen ist. Bestimmte Regeln für die Codeanalyse können Sie dies tun, indem Sie mit der `MessageId` Eigenschaft der <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut. Im Allgemeinen Legacy-Regeln für Verstöße für ein bestimmtes Symbol (eine lokale Variable oder Parameter) Bezug der `MessageId` Eigenschaft. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) ist ein Beispiel für eine solche Regel. Jedoch ältere Regeln für Verstöße in ausführbaren Code (nicht-Symbol) berücksichtigen nicht die `MessageId` Eigenschaft. Darüber hinaus .NET Compiler Platform ("Roslyn")-Analysen berücksichtigen nicht die `MessageId` Eigenschaft.

Um einen bestimmten Symbols Verstoß gegen eine Regel zu unterdrücken, geben Sie den Symbolnamen für die `MessageId` Eigenschaft der <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut. Das folgende Beispiel zeigt den Code mit zwei Verstöße gegen [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;eine für die `name` Variable und eine für die `age` Variable. Nur der Verstoß für die `age` Symbol wird unterdrückt.

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

Compiler für verwalteten Code und einige Tools von Drittanbietern generieren Code aus, um die schnelle Codeentwicklung zu ermöglichen. Vom Compiler generierter Code, der in Quelldateien angezeigt wird, ist in der Regel mit markiert die `GeneratedCodeAttribute` Attribut.

Sie können auswählen, ob codeanalysewarnungen und-Fehler für generierten Code zu unterdrücken. Informationen dazu, wie Sie solche Warnungen und Fehler unterdrücken, finden Sie unter [wie: Unterdrücken von Warnungen für generierten Code](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Codeanalyse ignoriert `GeneratedCodeAttribute` Wenn es auf eine gesamte Assembly oder einen einzelnen Parameter angewendet wird.

## <a name="global-level-suppressions"></a>Unterdrückungen auf Projektebene Global

Das Analysetool für verwalteten Code untersucht `SuppressMessage` Attribute, die Ebene der Assembly, Modul, Typ, Member oder Parameter angewendet werden. Es wird auch ausgelöst, Verstöße gegen Ressourcen und Namespaces. Diese Verletzungen sind auf globaler Ebene angewendet werden muss und begrenzt und ausgerichtet. Die folgende Meldung wird z. B. eine Namespaceverletzung unterdrückt:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Wenn Sie eine Warnung mit dem Namespace-Gültigkeitsbereich unterdrücken, unterdrückt sie die Warnung für den Namespace selbst. Unterdrückt nicht die Warnung für Typen im Namespace.

Durch einen expliziten Bereich angeben, kann jede Unterdrückung ausgedrückt werden. Diese Unterdrückungen müssen auf globaler Ebene befinden. Sie können nicht auf Memberebene Unterdrückung angeben, durch das ergänzen eines Typs.

Unterdrückungen auf Projektebene Global sind die einzige Möglichkeit, Nachrichten zu unterdrücken, die auf die vom Compiler generierter Code verweisen, die nicht explizit angegebenen Benutzerquelle zugeordnet ist. Der folgende Code unterdrückt z. B. einen Verstoß gegen einen Compiler ausgegebenen Konstruktor:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` enthält immer den vollqualifizierten Namen ein.

## <a name="global-suppression-file"></a>Globale Unterdrückungsdatei

Der globale Unterdrückungsdatei verwaltet Unterdrückungen, die entweder auf globaler Ebene Unterdrückungen oder Unterdrückungen, die kein Ziel angeben. Unterdrückungen auf Assemblyebene Verletzungen werden z. B. in dieser Datei gespeichert. Darüber hinaus werden einige ASP.NET Unterdrückungen in dieser Datei gespeichert, da auf Projektebene Einstellungen nicht für Code für ein Formular verfügbar sind. Eine globale Unterdrückungsdatei erstellt und hinzugefügt zu Ihrem Projekt zum ersten Mal, die Sie auswählen der **In Projektunterdrückungsdatei** Möglichkeit, die **unterdrücken** -Befehl in der **Fehlerliste**Fenster.

## <a name="see-also"></a>Siehe auch

- <xref:System.Diagnostics.CodeAnalysis>
- [Verwenden von Roslyn-Analysetools](../code-quality/use-roslyn-analyzers.md)