---
title: 'CA1715: Bezeichner sollten ein korrektes Präfix aufweisen.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b794eb7c7a258a843763b2c68902000031c17eb3
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873603"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Bezeichner sollten ein korrektes Präfix aufweisen.

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Wichtige – Wenn auf Schnittstellen ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für den generischen Parameter des Typs ausgelöst.|

## <a name="cause"></a>Ursache

Der Name einer Schnittstelle beginnt nicht mit einem Großbuchstaben "I".

- oder - 

Der Name des eine [generischen Typparameter](/dotnet/csharp/programming-guide/generics/generic-type-parameters) von einem Typ oder die Methode beginnt nicht mit einem Großbuchstaben ' t '.

Diese Regel nur sucht standardmäßig an extern sichtbaren Schnittstellen, Typen und Methoden, dies ist jedoch [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Starten die Namen der bestimmte Programmierelemente gemäß der Konvention mit einem bestimmten Präfix.

Schnittstellennamen sollte mit einem großen gestartet werden die 'I' einen anderen Großbuchstabe folgen. Diese Regel wird berichtet, Verstöße für Schnittstellennamen, z. B. "MyInterface" und "IsolatedInterface".

Namen generischer Typparameter sollte mit einem Großbuchstaben beginnen ' t ' und kann optional von einem anderen Großbuchstaben gefolgt werden. Diese Regel wird berichtet, Verstöße für den Namen des generischen Typs Parameter wie z. B. 'V' und 'Typ'.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysetools](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihres Codes diese Regel analysiert. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Typparameter für einzelne Zeichen

Sie können, ob Parameter vom Typ der einzelnen Zeichen dieser Regel auszuschließen oder nicht konfigurieren. Um beispielsweise anzugeben, dass diese Regel *sollte nicht* Parameter vom Typ der einzelnen Zeichen zu analysieren, fügen Sie einen der folgenden Schlüssel-Wert-Paare in einer editorconfig-Datei in Ihrem Projekt hinzu:

```
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Diese Regel löst nie für einen Typparameter, der mit dem Namen `T`, z. B. `Collection<T>`.

### <a name="api-surface"></a>API-Oberfläche

Sie können konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1715.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Naming) konfigurieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Benennen Sie den Bezeichner, damit es ordnungsgemäß vorangestellt ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="interface-naming-example"></a>Benennungskonventionen Beispiel für Schnittstelle

Der folgende Codeausschnitt zeigt eine falsch benannte Schnittstelle:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

Der folgende Codeausschnitt korrigiert der vorherige Verstoß, indem Sie die Schnittstelle 'I' voranstellen:

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Type-Parameter-Benennungskonventionen – Beispiel

Der folgende Codeausschnitt zeigt einen falsch benannter generischer Typparameter:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

Im folgenden Codeausschnitt wird der vorherige Verstoß korrigiert, werden des generische Typparameters t ":

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1722: Bezeichner sollten kein falsches Präfix aufweisen.](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)