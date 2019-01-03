---
title: 'CA1001: Typen, die löschbare Felder besitzen müssen gelöscht werden können.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d935d6310e9160cec222ef71933f23f1abf379cc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908826"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typen, die löschbare Felder besitzen müssen gelöscht werden können.

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend – Wenn der Typ nicht außerhalb der Assembly sichtbar ist.<br /><br /> Wichtige – Wenn der Typ außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Eine Klasse deklariert und implementiert ein Instanzenfeld, das eine <xref:System.IDisposable?displayProperty=fullName> Typ und die Klasse implementiert keine <xref:System.IDisposable>.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Klasse implementiert die <xref:System.IDisposable> Schnittstelle, um nicht verwaltete Ressourcen freigegeben, die dieser besitzt. Ein Instanzenfeld, das eine <xref:System.IDisposable> Typ gibt an, dass das Feld eine nicht verwaltete Ressource besitzt. Eine Klasse, die deklariert eine <xref:System.IDisposable> Feld indirekt eine nicht verwaltete Ressource besitzt, und sollte implementieren die <xref:System.IDisposable> Schnittstelle. Wenn die Klasse nicht direkt über nicht verwalteten Ressourcen besitzt, sollten sie keinen Finalizer implementieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren <xref:System.IDisposable> und von der <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Methodenaufruf der <xref:System.IDisposable.Dispose%2A> -Methode des Felds.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, die gegen die Regel verstößt und eine Klasse, die durch die Implementierung der Regel entspricht <xref:System.IDisposable>. Die Klasse implementiert keinen Finalizer, da die Klasse nicht direkt über nicht verwalteten Ressourcen besitzt.

 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Dispose-Methoden müssen die Dispose der Basisklasse aufrufen.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Typen, die systemeigene Ressourcen besitzen müssen gelöscht werden können.](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)