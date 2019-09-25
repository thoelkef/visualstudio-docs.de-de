---
title: 'CA1720: Bezeichner dürfen keine Typnamen enthalten.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2677c2ef5342b795bb684f3ab06bc7cf5195cf7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233894"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Bezeichner dürfen keine Typnamen enthalten.

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name eines Parameters in einem Member enthält einen Datentyp Namen.

- oder -

Der Name eines Members enthält einen sprachspezifischen Datentyp Namen.

Standardmäßig betrachtet diese Regel nur extern sichtbare Member, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Namen von Parametern und Membern werden besser verwendet, um ihre Bedeutung zu vermitteln, als den Typ zu beschreiben, der von den Entwicklungs Tools bereitgestellt werden soll. Wenn ein Datentyp Name verwendet werden muss, verwenden Sie für Namen von Membern einen sprachunabhängigen Namen anstelle eines sprachspezifischen namens. Verwenden Sie beispielsweise anstelle des C# Typnamens `int`den Namen des sprachunabhängigen `Int32`Datentyps.

Jedes diskrete Token im Namen des Parameters oder Members wird in der Groß-und Kleinschreibung mit den folgenden sprachspezifischen Datentyp Namen verglichen:

- Bool
- WChar
- Int8
- UInt8
- Short
- UShort
- Int
- UInt
- Ganze Zahl
- UInteger
- Long
- ULong
- Ohne Vorzeichen
- Signiert
- Float
- Float32
- Float64

Außerdem werden die Namen eines Parameters unter Berücksichtigung der Groß-/Kleinschreibung auch anhand der folgenden sprachunabhängigen Datentyp Namen überprüft:

- Object
- Obj
- Boolesch
- Char
- Zeichenfolge
- SByte
- Byte
- Ubyte
- Int16
- UInt16
- Int32
- UInt32
- Int64
- UInt64
- IntPtr
- PTR
- Zeiger
- Uinptr
- Uptr
- Upointer
- Single
- Double
- Decimal
- GUID

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

**Wenn für einen Parameter ausgelöst:**

Ersetzen Sie den Datentyp Bezeichner im Namen des Parameters durch einen Begriff, der seine Bedeutung oder einen allgemeineren Begriff (z. b. "Value") besser beschreibt.

**Wenn für einen Member ausgelöst:**

Ersetzen Sie den sprachspezifischen Datentyp Bezeichner im Namen des Members durch einen Begriff, der seine Bedeutung, eine sprachunabhängige Entsprechung oder einen allgemeineren Begriff (z. b. "Value") besser beschreibt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Gelegentlich können typbasierte Parameter-und Elementnamen verwendet werden. Bei der neuen Entwicklung treten jedoch keine bekannten Szenarien auf, in denen Sie eine Warnung aus dieser Regel unterdrücken sollten. Bei Bibliotheken, die bereits ausgeliefert wurden, müssen Sie möglicherweise eine Warnung aus dieser Regel unterdrücken.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Naming) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Verwandte Regeln

- [CA1709: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Bezeichner sollten sich um mehr als einen Fall unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: Parameter Namen sollten nicht mit Elementnamen identisch sein.](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)