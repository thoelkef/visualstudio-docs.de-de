---
title: 'CA1001: Typen, die Verwerfbare Felder besitzen, müssen gelöscht werden können | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42d21eb0bf32b3abb0eb26d3723123bf085914ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646326"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend, wenn der Typ außerhalb der Assembly nicht sichtbar ist.<br /><br /> Unterbrechung: Wenn der Typ außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Eine Klasse deklariert und implementiert ein Instanzfeld, das ein <xref:System.IDisposable?displayProperty=fullName>-Typ ist, und die Klasse implementiert nicht <xref:System.IDisposable>.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Klasse implementiert die Schnittstelle "<xref:System.IDisposable>", um nicht verwaltete Ressourcen, die Sie besitzt, zu verwerfen. Ein Instanzfeld, das ein <xref:System.IDisposable>-Typ ist, gibt an, dass das Feld eine nicht verwaltete Ressource besitzt. Eine Klasse, die ein <xref:System.IDisposable>-Feld deklariert, besitzt indirekt eine nicht verwaltete Ressource und sollte die <xref:System.IDisposable>-Schnittstelle implementieren. Wenn die Klasse keine nicht verwalteten Ressourcen direkt besitzt, sollte Sie keinen Finalizer implementieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie <xref:System.IDisposable> und in der <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>-Methode die <xref:System.IDisposable.Dispose%2A>-Methode des Felds.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, die gegen die Regel verstößt, und eine Klasse, die die Regel erfüllt, indem <xref:System.IDisposable> implementiert wird. Die Klasse implementiert keinen Finalizer, da die Klasse nicht direkt Besitzer von nicht verwalteten Ressourcen ist.

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Typen, die systemeigene Ressourcen besitzen, müssen gelöscht werden können](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
