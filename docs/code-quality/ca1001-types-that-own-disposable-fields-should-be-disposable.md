---
title: 'CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können.'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fae67f8c1ffa3b4e6d7cc2f0fbbaf670733f9ff4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923314"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können.

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend, wenn der Typ außerhalb der Assembly nicht sichtbar ist.<br /><br /> Unterbrechung: Wenn der Typ außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
Eine Klasse deklariert und implementiert ein Instanzfeld, bei <xref:System.IDisposable?displayProperty=fullName> dem es sich um einen-Typ <xref:System.IDisposable>handelt und die-Klasse nicht implementiert.

## <a name="rule-description"></a>Regelbeschreibung
Eine Klasse implementiert die <xref:System.IDisposable> -Schnittstelle, um nicht verwaltete Ressourcen, die Sie besitzt, zu verwerfen. Ein Instanzfeld, das <xref:System.IDisposable> ein-Typ ist, gibt an, dass das Feld eine nicht verwaltete Ressource besitzt. Eine Klasse, die ein <xref:System.IDisposable> Feld deklariert, besitzt indirekt eine nicht verwaltete Ressource und sollte <xref:System.IDisposable> die-Schnittstelle implementieren. Wenn die Klasse keine nicht verwalteten Ressourcen direkt besitzt, sollte Sie keinen Finalizer implementieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, <xref:System.IDisposable> implementieren Sie und <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> aus der- <xref:System.IDisposable.Dispose%2A> Methode die-Methode des-Felds.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Klasse, die gegen die Regel verstößt, und eine Klasse, die die <xref:System.IDisposable>Regel durch Implementieren von erfüllt. Die Klasse implementiert keinen Finalizer, da die Klasse nicht direkt Besitzer von nicht verwalteten Ressourcen ist.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

[CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA2215: Verwerfen-Methoden sollten Basisklassen Freigabe abrufen](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

[CA1049: Typen, die native Ressourcen besitzen, müssen gelöscht werden können](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)