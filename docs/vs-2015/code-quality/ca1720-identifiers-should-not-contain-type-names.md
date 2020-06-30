---
title: 'CA1720: Bezeichner dürfen keine Typnamen enthalten. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f6d228b0fbf5507ba135f9ddc35d6d8b161f0011
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534848"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Bezeichner dürfen keine Typnamen enthalten.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentyp Namen.

 - oder -

 Der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentyp Namen.

## <a name="rule-description"></a>Beschreibung der Regel
 Namen von Parametern und Membern werden besser verwendet, um ihre Bedeutung zu vermitteln, als den Typ zu beschreiben, der von den Entwicklungs Tools bereitgestellt werden soll. Wenn ein Datentyp Name verwendet werden muss, verwenden Sie für Namen von Membern einen sprachunabhängigen Namen anstelle eines sprachspezifischen namens. Verwenden Sie beispielsweise anstelle des c#-Typnamens "int" den sprachunabhängigen Datentyp namens Int32.

 Jedes diskrete Token im Namen des Parameters oder Members wird mit den folgenden sprachspezifischen Datentyp Namen überprüft, ohne Berücksichtigung der Groß-/Kleinschreibung:

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

  Außerdem werden die Namen eines Parameters auch mit den folgenden sprachunabhängigen Datentyp Namen überprüft, ohne Berücksichtigung der Groß-und Kleinschreibung:

- Object

- Obj

- Boolesch

- Char

- String

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
 Gelegentlich können typbasierte Parameter-und Elementnamen verwendet werden. Bei der neuen Entwicklung treten jedoch keine bekannten Szenarien auf, in denen Sie eine Warnung aus dieser Regel unterdrücken sollten. Bei Bibliotheken, die zuvor ausgeliefert wurden, müssen Sie möglicherweise eine Warnung aus dieser Regel unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
