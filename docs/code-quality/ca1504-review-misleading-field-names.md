---
title: 'CA1504: Irreführende Feldnamen überprüfen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df6ab704c2dfdbf8ebdf8eb42f56d8d64600736f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921831"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Irreführende Feldnamen überprüfen.

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Der Name eines Instanzfelds beginnt mit "S_", oder der Name `static` eines-Felds (`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) beginnt mit "M_".

## <a name="rule-description"></a>Regelbeschreibung
Feldnamen, die mit "S_" beginnen, werden von vielen Benutzern statischen Daten zugeordnet. Ebenso sind Feldnamen, die mit "M_" beginnen, mit Instanzdaten(Member) verknüpft. Um leichter verwalteten Code zu erhalten, sollten Namen allgemeinen verwendeten Konventionen entsprechen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, benennen Sie das Feld um, indem Sie das entsprechende Präfix verwenden. Alternativ dazu können Sie das Feld mit dem aktuellen Suffix einverstanden machen, indem Sie `static` den-Modifizierer hinzufügen oder entfernen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.