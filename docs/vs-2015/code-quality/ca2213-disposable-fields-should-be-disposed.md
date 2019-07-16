---
title: 'CA2213: Verwerfbare Felder verwerfen werden | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cbb606729fe89eb5c2ebe3c814096ef39120836a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685254"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Verwerfbare Felder verwerfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ, der implementiert <xref:System.IDisposable?displayProperty=fullName> deklariert Felder von Typen, die ebenfalls implementieren <xref:System.IDisposable>. Die <xref:System.IDisposable.Dispose%2A> -Methode des Felds wird nicht aufgerufen, indem die <xref:System.IDisposable.Dispose%2A> -Methode des deklarierenden Typs.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Typ ist zum Freigeben von alle nicht verwalteten Ressourcen verantwortlich. Dies erfolgt durch die Implementierung <xref:System.IDisposable>. Diese Regel überprüft, ob einem verwerfbaren Typ `T` deklariert ein Feld `F` d. h. eine Instanz eines verwerfbaren Typs `FT`. Für jedes Feld `F`, der Regel wird versucht, einen Aufruf von `FT.Dispose`. Die Regel durchsucht, die vom aufgerufenen Methoden `T.Dispose`, und die Ebene darunter (die durch die vom aufgerufenen Methoden aufgerufenen Methoden `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen <xref:System.IDisposable.Dispose%2A> für Felder, die Typen, die implementieren <xref:System.IDisposable> Sie sind verantwortlich für die Zuordnung und Freigabe von nicht verwalteten Ressourcen frei, die nach dem Feld.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicherer, die mit dieser Regel eine Warnung zu unterdrücken, wenn Sie nicht zuständig sind, für die Ressource freigegeben, die nach dem Feld gespeichert wird, oder wenn der Aufruf von <xref:System.IDisposable.Dispose%2A> tritt auf, auf einer tieferen aufrufenden Ebene als die Regel überprüft.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein `TypeA` implementiert <xref:System.IDisposable> (`FT` aus dem vorherigen Beispiel).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein `TypeB` gegen diese Regel, durch das Deklarieren eines Feldes `aFieldOfADisposableType` (`F` aus dem vorherigen Beispiel) als von einem verwerfbaren Typ (`TypeA`) und nicht aufrufen <xref:System.IDisposable.Dispose%2A> für das Feld. `TypeB` entspricht `T` aus dem vorherigen Beispiel.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.IDisposable?displayProperty=fullName> [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
