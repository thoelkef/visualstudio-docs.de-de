---
title: 'CA1707: Bezeichner sollten keine Unterstriche enthalten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe6b90ef971bd00392381f47860d85f34e10dc26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544026"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Bezeichner sollten keine Unterstriche enthalten.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1707: Bezeichner sollten keine Unterstriche enthalten](/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).

|Element|Wert|
|-|-|
|TypName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechen: Wenn Assemblys ausgelöst werden<br /><br /> Nicht unterbrechend: Wenn für Typparameter ausgelöst|

## <a name="cause"></a>Ursache
 Der Name eines Bezeichners enthält den Unterstrich (_).

## <a name="rule-description"></a>Beschreibung der Regel
 Bezeichnernamen dürfen keinen Unterstrich (_) enthalten. Die Regel überprüft Namespaces, Typen, Member und Parameter.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie alle Unterstrich Zeichen aus dem Namen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
