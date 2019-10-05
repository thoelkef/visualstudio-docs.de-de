---
title: 'CA2207: Statische Felder für Werttyp inline initialisieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46f579b6776ffab6d0ed3b2e216e29d36d2065ee
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231695"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Statische Felder für Werttyp inline initialisieren.

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein Werttyp deklariert einen expliziten statischen Konstruktor.

## <a name="rule-description"></a>Regelbeschreibung
Wenn ein Werttyp deklariert wird, wird eine Standard Initialisierung durchgeführt, bei der alle Werttyp Felder auf 0 (null) und alle Verweistyp Felder `null` auf`Nothing` (in Visual Basic) festgelegt sind. Es ist nur garantiert, dass ein expliziter statischer Konstruktor ausgeführt wird, bevor ein Instanzkonstruktor oder ein statischer Member des Typs aufgerufen wird. Wenn der Typ ohne Aufruf eines Instanzkonstruktors erstellt wird, wird der statische Konstruktor daher nicht garantiert ausgeführt.

Wenn alle statischen Daten inline initialisiert werden und kein expliziter statischer Konstruktor deklariert C# wird, fügen der-und `beforefieldinit` der-Visual Basic Compiler das-Flag zur MSIL-Klassendefinition hinzu. Die Compiler fügen außerdem einen privaten statischen Konstruktor hinzu, der den statischen Initialisierungs Code enthält. Dieser private statische Konstruktor wird garantiert ausgeführt, bevor auf statische Felder des Typs zugegriffen wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten, wenn Sie deklariert werden, und entfernen Sie den statischen Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
[CA1810: Statische Felder von Verweis Typen Inline initialisieren](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)