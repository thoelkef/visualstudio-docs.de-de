---
title: 'CA1720: Bezeichner dürfen keine Typnamen enthalten | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 504c985bd276a891b76e8c9b2a7c0ef51c3a490a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576727"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Bezeichner dürfen keine Typnamen enthalten.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentypnamen.

 - oder - 

 Der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentypnamen.

## <a name="rule-description"></a>Regelbeschreibung
 Namen von Parametern und Membern werden besser zum kommunizieren ihre Bedeutung als zur Beschreibung des Typs, die von den Entwicklungstools bereitgestellt werden soll. Für Namen von Elementen, wenn Sie ein Datentypnamen verwendet werden muss, eine sprachunabhängige Name anstelle einer sprachspezifischen verwenden. Verwenden Sie z. B. statt der C#-Typ 'Int' den sprachunabhängige Datentypnamen, Int32.

 Jedes diskrete Token im Namen des Parameters oder Members wird mit die folgenden sprachspezifischen Datentypnamen, Groß-und Kleinschreibung verglichen:

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

  Darüber hinaus werden die Namen der Parameter auch mit den folgenden sprachunabhängige Typnamen, unter Beachtung der Groß-verglichen:

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Gelegentliche Nutzung eines basierende Parameter- und Memberlisten-Namen kann geeignet sein. Für neue Entwicklungen keine bekannte jedoch Szenarien, in dem Sie eine Warnung dieser Regel unterdrücken soll. Für Bibliotheken, die zuvor versandt wurden, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1709: Bezeichner sollten beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
