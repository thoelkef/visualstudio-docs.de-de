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
ms.openlocfilehash: c596ddfa36beec696c275ea13b662ceebf8bde2c
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841798"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Bezeichner dürfen keine Typnamen enthalten.

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name eines Parameters in ein Element enthält einen Datentypnamen.

- oder - 

Der Name eines Members enthält einen sprachspezifischen Datentypnamen.

Diese Regel nur sucht standardmäßig an extern sichtbare Member, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Namen von Parametern und Membern werden besser zum kommunizieren ihre Bedeutung als zur Beschreibung des Typs, die von den Entwicklungstools bereitgestellt werden soll. Für Namen von Elementen, wenn Sie ein Datentypnamen verwendet werden muss, eine sprachunabhängige Name anstelle einer sprachspezifischen verwenden. Beispielsweise anstelle von der C# Typnamen `int`, verwenden Sie den sprachunabhängige Datentypnamen `Int32`.

Jedes diskrete Token im Namen des Parameters oder Members wird mit den folgenden sprachspezifischen Datentypnamen unter Beachtung der Groß-verglichen:

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

Darüber hinaus werden die Namen der Parameter auch mit den folgenden sprachunabhängige Typnamen unter Beachtung der Groß-verglichen:

- Object
- Obj
- Boolesch
- Char
- Zeichenfolge
- SByte
- Byte
- UByte
- Int16
- UInt16
- Int32
- UInt32
- Int64
- UInt64
- IntPtr
- Ptr
- Zeiger
- UInptr
- UPtr
- UPointer
- Single
- Double
- Decimal
- GUID

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

**Bei Auslösung gegen einen Parameter:**

Ersetzen Sie die Daten-Typ-ID, den Namen der Parameter mit einem Begriff, der seine Bedeutung besser beschreibt oder einen generischen Begriff, z. B. "Value".

**Wenn für ein Element ausgelöst wird:**

Ersetzen Sie den sprachspezifischen Datentypbezeichner den Namen der Member mit einem Begriff, der der Bedeutung, eine sprachunabhängige Entsprechung oder einen generischen Begriff, z. B. "Value" besser beschreibt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Gelegentliche Nutzung eines basierende Parameter- und Memberlisten-Namen kann geeignet sein. Für neue Entwicklungen keine bekannte jedoch Szenarien, in dem Sie eine Warnung dieser Regel unterdrücken soll. Bei Bibliotheken, die zuvor veröffentlicht haben, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Naming) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Verwandte Regeln

- [CA1709: Bezeichner sollten beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)