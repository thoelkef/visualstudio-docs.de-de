---
title: Unterdrücken von Warnungen der Codeanalyse in Visual Studio
ms.date: 01/29/2018
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
ms.openlocfilehash: aec11e54547f05e3ac7babae29e0c95737bc725e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924417"
---
# <a name="suppress-code-analysis-warnings"></a>Unterdrücken der codeanalysewarnungen

Es ist häufig nützlich, um anzugeben, dass eine Warnung nicht anwendbar ist. Dies gibt an, für die Teammitglieder, die der Code wurde überprüft, und die Warnung kann unterdrückt werden. Datenquelle unterdrückenden (ISS) verwendet die <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut, um eine Warnung zu unterdrücken. Das Attribut kann in der Nähe der Codesegment platziert werden, die die Warnung generiert. Können Sie hinzufügen, die <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut auf die Quelldatei durch Eingabe in oder können Sie das Kontextmenü für eine Warnung in der **Fehlerliste** automatisch hinzuzufügen.

Die <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut ist ein conditional-Attribut das in der Assembly mit verwaltetem Code, die IL-Metadaten enthalten ist, nur dann, wenn zum Zeitpunkt der Kompilierung die CODE_ANALYSIS-Kompilierungssymbol definiert ist.

In C + c++ / CLI, verwenden Sie die Makros Zertifizierungsstelle\_UNTERDRÜCKEN\_Nachricht oder einer Zertifizierungsstelle\_GLOBAL\_SUPPRESS_MESSAGE in der Headerdatei, um das Attribut hinzuzufügen.

> [!NOTE]
> Sie sollten nicht Unterdrückung im Quellcode auf Releasebuilds verwenden, um zu verhindern, dass die Unterdrückung im Quellcode Metadaten versehentlich Protokollversand. Darüber hinaus kann aufgrund der Verarbeitungskosten Unterdrückung im Quellcode, die Leistung Ihrer Anwendung beeinträchtigt sein.

> [!NOTE]
> Wenn Sie ein Projekt zu Visual Studio 2017 migrieren, können Sie plötzlich eine Flut von codeanalysewarnungen Datenwachstums werden. Wenn Sie nicht bereit sind, korrigieren Sie die Warnungen und Codeanalyse vorübergehend deaktivieren möchten, öffnen Sie die Eigenschaftenseiten des Projekts (**Projekt** > ***Projekt* Eigenschaften...** ) und fahren Sie mit der **Codeanalyse** Registerkarte. Deaktivieren Sie **Codeanalyse für Build aktivieren**, und erstellen Sie das Projekt dann erneut. Alternativ können Sie einen anderen, kleineren Regelsatz, der für den Code ausführen auswählen. Denken Sie daran, aktivieren Sie die Codeanalyse auf Wenn Sie die Warnungen beheben bereit sind.

## <a name="suppressmessage-attribute"></a>SuppressMessage-Attribut

Bei Auswahl **unterdrücken** aus im Kontext oder mit der rechten Maustaste in eine codeanalysewarnung in der **Fehlerliste**ein <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut wird entweder im Code oder globale Unterdrückung des Projekts hinzugefügt. die Datei.

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

- **Regel "Kategorie"** – die Kategorie aus, in dem die Regel definiert wird. Weitere Informationen zu Codeanalyseregeln, finden Sie unter [verwalteten Code (Warnungen)](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Regel-Id** -der Bezeichner der Regel. Unterstützung umfasst sowohl einen kurz- und langfristigen Namen für die Regel-ID an. Der kurze Name ist CAXXXX; der lange Name ist CAXXXX:FriendlyTypeName.

- **Durch den Blocksatz** -der Text, der verwendet wird, um den Grund für die Unterdrückung der Meldung dokumentieren.

- **Meldungs-Id** -eindeutige Bezeichner für ein Problem für jede Nachricht.

- **Bereich** -Ziel, auf dem die Warnung unterdrückt wird. Wenn das Ziel nicht angegeben ist, wird er auf das Ziel des Attributs festgelegt. Die folgenden: Bereiche werden unterstützt

    - Modul

    - Namespace

    - Ressource

    - Typ

    - Member

- **Ziel** : ein Bezeichner, der verwendet wird, um das Ziel anzugeben, auf dem die Warnung unterdrückt wird. Sie müssen einen vollständig qualifizierten Elementnamen enthalten.

## <a name="suppressmessage-usage"></a>SuppressMessage-Verwendung

Codeanalysewarnungen werden auf der Ebene, unterdrückt die <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut angewendet wird. Das Attribut kann z. B. auf die Assembly, Modul, Typ, Member oder Parameter Ebene angewendet werden. Das Zweck dieses werden eng gekoppelt die Unterdrückungsinformationen an den Code, in dem die Verletzung auftritt.

Das allgemeine Format Unterdrückung umfasst die Regelkategorie und Regelbezeichner, der eine optionale lesbare Darstellung der Namen der Regel enthält. Zum Beispiel:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Wenn strict Leistungsgründen Minimierung Unterdrückung im Quellcode Metadaten sind, kann der Regelname ausgelassen werden. Die Regelkategorie und die zugehörige Regel-ID bilden zusammen hinreichend eindeutigen Regelbezeichner. Zum Beispiel:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Aus Gründen der Verwaltbarkeit ist das Weglassen von Namen der Regel nicht empfohlen.

## <a name="suppress-selective-violations-within-a-method-body"></a>Selektive Verstöße innerhalb eines Methodentexts unterdrücken

Unterdrückung Attribute können auf eine Methode angewendet werden, sondern können nicht innerhalb eines Methodentexts eingebettet sein. Dies bedeutet, dass alle Verstöße gegen eine bestimmte Regel unterdrückt werden, wenn Sie beim Hinzufügen der <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> -Attribut zur Methode.

In einigen Fällen empfiehlt es sich um eine bestimmte Instanz einer Verletzung, z. B. zu unterdrücken, sodass zukünftiger Code automatisch von der Regel zur Codeanalyse ausgenommen ist nicht. Bestimmte Codeanalyseregeln können Sie hierzu mit der `MessageId` Eigenschaft von der <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut. Im Allgemeinen Legacy-Regeln für Verstöße auf einem bestimmten Symbol (eine lokale Variable oder Parameter) bezüglich der `MessageId` Eigenschaft. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) ist ein Beispiel für eine solche Regel. Allerdings Legacyregeln Verstöße ausführbarem Code (nicht-Symbol) berücksichtigen nicht die `MessageId` Eigenschaft. Darüber hinaus .NET Compiler Platform ("Roslyn")-Analysen berücksichtigen nicht die `MessageId` Eigenschaft.

Um einen bestimmten Symbols Verstoß gegen eine Regel zu unterdrücken, geben Sie den Symbolnamen für die `MessageId` Eigenschaft von der <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Attribut. Das folgende Beispiel zeigt den Code mit zwei Verstöße gegen [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;eine für die `name` Variable und einen für die `age` Variable. Nur der Verstoß für die `age` Symbol unterdrückt wird.

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

Compiler für verwalteten Code und einige Drittanbieter-Tools generieren Code aus, um eine schnelle Codeentwicklung zu ermöglichen. Vom Compiler generierte Code, der in Quelldateien ist in der Regel mit markiert die `GeneratedCodeAttribute` Attribut.

Sie können auswählen, ob das Unterdrücken von codeanalysewarnungen und Fehler für generierten Code. Weitere Informationen dazu, wie solche Warnungen und Fehler unterdrücken, finden Sie unter [wie: Unterdrücken von Warnungen für generierten Code](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Codeanalyse ignoriert `GeneratedCodeAttribute` Wenn sie eine gesamte Assembly oder einen einzelnen Parameter angewendet wird.

## <a name="global-level-suppressions"></a>Auf globaler Ebene Unterdrückungen

Die verwaltete Codeanalysetool überprüft `SuppressMessage` Attribute, die auf die Assembly, Modul, Typ, Member oder ein Parameterwert Ebene angewendet werden. Es wird auch ausgelöst, Verstöße gegen die Ressourcen und Namespaces. Diese Verstöße wurden auf globaler Ebene angewendet werden muss und im Bereich einer und angewendet. Die folgende Meldung unterdrückt z. B. einen Namespace Verstoß:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Wenn Sie eine Warnung mit Namespacebereich unterdrücken, wird die Warnung für den Namespace selbst unterdrückt. Sie unterdrückt die Warnung für Typen im Namespace nicht.

Jede Unterdrückung kann durch Angabe eines expliziten Bereichs ausgedrückt werden. Diese Unterdrückungen müssen auf globaler Ebene befinden. Sie können nicht auf Memberebene Unterdrückung werden, indem einen Typ angeben.

Auf globaler Ebene Unterdrückungen sind die einzige Möglichkeit, Nachrichten zu unterdrücken, die vom Compiler generierte Code verweisen, die explizit angegebene Benutzerquelle zugeordnet ist. Der folgende Code unterdrückt z. B. einen Verstoß gegen einen Konstruktor Compiler ausgegeben:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` enthält immer den vollqualifizierten Elementnamen ein.

## <a name="global-suppression-file"></a>Globale Unterdrückungsdatei

Die Unterdrückungsdatei für die globale verwaltet Unterdrückungen, die auf globaler Ebene Unterdrückungen oder Unterdrückungen, die kein Ziel angeben. Beispielsweise werden Unterdrückungen auf Assemblyebene Verstöße in dieser Datei gespeichert. Darüber hinaus sind einige Unterdrückungen ASP.NET in dieser Datei gespeichert werden, da Einstellungen auf Projektebene nicht verfügbar für Code für ein Formular sind. Eine globale Unterdrückungsdatei erstellt und hinzugefügt zu Ihrem Projekt zum ersten Mal, die Sie auswählen der **im Projektunterdrückungsdatei** -Option von der **unterdrücken** -Befehl in der **Fehlerliste**Fenster.

## <a name="see-also"></a>Siehe auch

- <xref:System.Diagnostics.CodeAnalysis>
- [Verwenden Sie Roslyn-Analyzern](../code-quality/use-roslyn-analyzers.md)