---
title: 'CA1810: Statische Felder von Referenztypen inline initialisieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1fca9742a4fe5e778c0b172adad7996dcad58ca4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923485"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Statische Felder von Referenztypen inline initialisieren.

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Verweistyp deklariert einen expliziten statischen Konstruktor.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT-Compiler (Just in Time) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde. Statischen Initialisierung wird ausgelöst, wenn Sie einen statischer Member zugegriffen wird, oder wenn eine Instanz des Typs erstellt wird. Statischen Initialisierung wird jedoch nicht ausgelöst, wenn Sie eine Variable des Typs deklarieren, aber nicht verwenden, die kann wichtig sein, wenn die Initialisierung globalen Zustand ändert.

 Wenn alle statische Daten Inline initialisiert und ein expliziter statischer Konstruktor ist nicht deklariert, Hinzufügen von Microsoft intermediate Language (MSIL)-Compiler die `beforefieldinit` Flag und einen impliziten statischen Konstruktor, der initialisiert die statischen Daten in den MSIL-Typ die Definition. Wenn der JIT-Compiler erkennt die `beforefieldinit` kennzeichnen, in den meisten Fällen die Überprüfung statischer Konstruktoren nicht hinzugefügt werden. Statischen Initialisierung ist garantiert, zu einem Zeitpunkt ausgeführt werden soll, bevor ein statisches Feld zugegriffen werden, aber nicht, bevor Sie ein statische Methode oder die Instanz-Konstruktor aufgerufen wird. Beachten Sie, dass die statische Initialisierung zu einem beliebigen Zeitpunkt nach dem Deklarieren einer Variablen des Typs auftreten kann.

 Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden. Ein statischer Konstruktor wird häufig verwendet, nur für die nach dem Initialisieren von statischen Feldern, in denen Fall, die Sie nur sicherstellen, dass die statische Initialisierung, müssen vor der ersten Zugriff auf ein statisches Feld auftritt. Die `beforefieldinit` Verhalten eignet sich für diese und die meisten anderen Projekttypen. Es ist nur dann ungeeignet, wenn statische Initialisierung wirkt sich auf die globalen Zustand und eine der folgenden zutrifft:

- Die Auswirkungen auf den globalen Zustand ist teuer und ist nicht erforderlich, wenn der Typ nicht verwendet wird.

- Die Auswirkungen des globalen Status können zugegriffen werden, ohne den Zugriff auf ein statisches Feld des Typs.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, wenn Leistung nicht relevant ist; oder wenn globale Zustandsänderungen, die durch statische Initialisierung verursacht werden, teuer sind oder müssen garantiert auftreten, bevor Sie eine statische Methode des Typs aufgerufen wird, oder eine Instanz des Typs erstellt.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ, `StaticConstructor`, die gegen die Regel und einen Typ, `NoStaticConstructor`, ersetzt den statischen Konstruktor mit Inline-Initialisierung, um die Regel zu erfüllen.

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

Beachten Sie das Hinzufügen der `beforefieldinit` Flag für die MSIL-Definition für die `NoStaticConstructor` Klasse.

```
.class public auto ansi StaticConstructor
extends [mscorlib]System.Object
{
} // end of class StaticConstructor

.class public auto ansi beforefieldinit NoStaticConstructor
extends [mscorlib]System.Object
{
} // end of class NoStaticConstructor
```

## <a name="related-rules"></a>Verwandte Regeln

- [CA2207: Statische Felder Werttyp Inline initialisieren](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)