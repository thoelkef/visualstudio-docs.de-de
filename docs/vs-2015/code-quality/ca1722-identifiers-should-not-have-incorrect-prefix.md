---
title: 'CA1722: Bezeichner sollten kein falsches Präfix aufweisen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0c9aa6600578da0d9868df2ecff9992bff9e818c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191244"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Bezeichner sollten kein falsches Präfix aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Bezeichner weist ein falsches Präfix.

## <a name="rule-description"></a>Regelbeschreibung
 Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen.

 Typnamen müssen sich nicht auf ein bestimmtes Präfix und nicht das Präfix ein "C". Diese Regel meldet Verstöße Typnamen wie "CMyClass und meldet keine Verstöße für Typnamen wie"Cache".

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie das Präfix aus einem Bezeichner.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1715: Bezeichner sollten ein korrektes Präfix aufweisen](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
