---
title: 'CA2213: Verwerfbare Felder müssen verworfen werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662897"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Verwerfbare Felder verwerfen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ, der <xref:System.IDisposable?displayProperty=fullName> implementiert, deklariert Felder mit Typen, die ebenfalls <xref:System.IDisposable> implementieren. Die <xref:System.IDisposable.Dispose%2A>-Methode des Felds wird nicht von der <xref:System.IDisposable.Dispose%2A>-Methode des deklarierenden Typs aufgerufen.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Typ ist für das Verwerfen aller seiner nicht verwalteten Ressourcen zuständig. Dies wird erreicht, indem <xref:System.IDisposable> implementiert wird. Diese Regel überprüft, ob ein verwerfbarer Typ `T` ein Feld `F` deklariert, das eine Instanz eines verwerfbaren Typs `FT` ist. Für jedes Feld `F` versucht die Regel, einen aufzurufenden `FT.Dispose` zu suchen. Die Regel durchsucht die Methoden, die von `T.Dispose` aufgerufen werden, und eine Ebene niedriger (die Methoden, die von den Methoden aufgerufen werden, die von `FT.Dispose` aufgerufen werden)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie <xref:System.IDisposable.Dispose%2A> für Felder mit Typen an, die <xref:System.IDisposable> implementieren, wenn Sie für das zuordnen und Freigeben der nicht verwalteten Ressourcen, die im Feld gehalten werden, verantwortlich sind.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Sie nicht für die Freigabe der Ressource zuständig sind, die im Feld gehalten wird, oder wenn der Aufruf von <xref:System.IDisposable.Dispose%2A> auf einer tieferen Aufruf Ebene als die Regel Überprüfungen auftritt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Typ`TypeA`, die <xref:System.IDisposable> (`FT` in der vorherigen Diskussion) implementiert.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeB`, der gegen diese Regel verstößt, indem ein Feld `aFieldOfADisposableType` (`F` in der vorherigen Diskussion) als verwerfbarer Typ (`TypeA`) deklariert und <xref:System.IDisposable.Dispose%2A> für das Feld nicht aufgerufen wird. `TypeB` entspricht `T` in der vorherigen Erörterung.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.IDisposable?displayProperty=fullName> Lösch [Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
