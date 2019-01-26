---
title: 'CA1504: Irreführende Feldnamen überprüfen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: da99bab4235028f75146be1807162e93759d3eb9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926461"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Irreführende Feldnamen überprüfen.

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Der Name eines Instanzenfelds beginnt mit "S_" oder den Namen einer `static` (`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Feld beginnt mit "M_".

## <a name="rule-description"></a>Regelbeschreibung
 Feldnamen, die mit "S_" beginnen, sind statische Daten von vielen Benutzern zugeordnet. Auf ähnliche Weise werden die Feldnamen, die mit "M_" beginnen (Member) Instanzdaten zugeordnet. Für Code einfacher zu verwalten sollten Namen in der Regel verwendeten Konventionen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie das Feld mit dem entsprechenden Präfix. Alternativ passen Sie das Feld mit dem aktuellen Suffix durch Hinzufügen oder Entfernen der `static` Modifizierer.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.