---
title: Verwaltbarkeitswarnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a2efe3e8d2d8c00a4fb016250f06943db46120c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649274"
---
# <a name="maintainability-warnings"></a>Verwaltbarkeitswarnungen

Wart barkeits Warnungen unterstützen die Verwaltung von Bibliotheken und Anwendungen.

## <a name="in-this-section"></a>In diesem Abschnitt

| Regel | Beschreibung |
|-----------|-----------------------------------|
| [CA1500: Variablennamen sollten nicht mit Feldnamen übereinstimmen](../code-quality/ca1500.md) | Eine Instanzmethode deklariert einen Parameter oder eine lokale Variable, deren Name mit einem Instanzfeld des deklarierenden Typs übereinstimmt, was zu Fehlern führt. |
| [CA1501: Übermäßige Vererbung vermeiden](../code-quality/ca1501.md) | Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief. Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein. |
| [CA1502: Übermäßige Komplexität vermeiden](../code-quality/ca1502.md) | Diese Regel ermöglicht Aussagen über die Anzahl linear unabhängiger Pfade in einer Methode, wobei die Anzahl der Pfade durch die Anzahl und Komplexität bedingter Branches bestimmt wird. |
| [CA1504: Irreführende Feldnamen überprüfen](../code-quality/ca1504.md) | Der Name eines Instanzfelds beginnt mit "S_", oder der Name eines statischen Felds (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) beginnt mit "M_". |
| [CA1505: Nicht wartbaren Code vermeiden](../code-quality/ca1505.md) | Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert. Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder eine Methode wahrscheinlich schwer zu verwalten ist und geeignet für einen Neuentwurf wäre. |
| [CA1506: Übermäßige Klassenkopplungen vermeiden](../code-quality/ca1506.md) | Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden. |
| [CA1507: nameof anstelle der Zeichenfolge verwenden](../code-quality/ca1507.md) | Ein Zeichenfolgenliterals wird als Argument verwendet, bei dem ein `nameof` Ausdruck verwendet werden kann. |

## <a name="see-also"></a>Siehe auch

- [Messen von Komplexität und Verwaltbarkeit von verwaltetem Code](../code-quality/code-metrics-values.md)
