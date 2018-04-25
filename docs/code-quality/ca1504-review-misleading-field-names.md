---
title: 'CA1504: Irreführende Feldnamen überprüfen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0caf5e8c158f2c434bd20e4b033ed1e2f7f37e5f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Irreführende Feldnamen überprüfen
|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Der Name eines Instanzenfelds beginnt mit "S_" oder der Name einer `static` (`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Feld beginnt mit "M_".

## <a name="rule-description"></a>Regelbeschreibung
 Feldnamen, die mit "S_" beginnen, sind statische Daten von vielen Benutzern zugeordnet. Auf ähnliche Weise werden die Feldnamen, die mit "M_" beginnen Instanzdaten (Element) zugeordnet. Für Code einfacher zu verwalten sollten die Namen in der Regel verwendete Konventionen entsprechen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie das Feld mit dem entsprechenden Präfix. Alternativ passen Sie das Feld mit dem aktuellen Suffix durch Hinzufügen oder Entfernen der `static` Modifizierer.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.