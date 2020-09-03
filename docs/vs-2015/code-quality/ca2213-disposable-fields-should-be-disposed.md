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
ms.openlocfilehash: 887600bad0c3d05ff78050aa4449cf49dc882027
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534575"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Verwerfbare Felder verwerfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ, der implementiert, <xref:System.IDisposable?displayProperty=fullName> deklariert Felder mit Typen, die ebenfalls implementieren <xref:System.IDisposable> . Die- <xref:System.IDisposable.Dispose%2A> Methode des-Felds wird nicht von der- <xref:System.IDisposable.Dispose%2A> Methode des deklarierenden Typs aufgerufen.

## <a name="rule-description"></a>Beschreibung der Regel
 Ein Typ ist für das Verwerfen aller seiner nicht verwalteten Ressourcen zuständig. Dies wird durch Implementieren von erreicht <xref:System.IDisposable> . Mit dieser Regel wird überprüft, ob ein verwerfbarer Typ `T` ein Feld deklariert `F` , das eine Instanz eines verwerfbaren Typs ist `FT` . Für jedes Feld `F` versucht die Regel, einen-Rückruf zu suchen `FT.Dispose` . Die Regel durchsucht die Methoden, die von aufgerufen `T.Dispose` werden, und eine Ebene unten (die Methoden, die von den Methoden aufgerufen werden, die von aufgerufen werden `FT.Dispose` )

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie für Felder mit Typen abrufen, die <xref:System.IDisposable.Dispose%2A> implementieren, <xref:System.IDisposable> Wenn Sie für das zuordnen und Freigeben der nicht verwalteten Ressourcen, die im Feld gehalten werden, verantwortlich sind.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Sie nicht für die Freigabe der Ressource zuständig sind, die im Feld enthalten ist, oder wenn der Aufruf von <xref:System.IDisposable.Dispose%2A> mit einer tieferen Aufruf Ebene erfolgt als die Regel Überprüfungen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeA` , der implementiert <xref:System.IDisposable> ( `FT` in der vorherigen Diskussion).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeB` , der gegen diese Regel verstößt, indem ein Feld `aFieldOfADisposableType` ( `F` in der vorherigen Erörterung) als verwerfbarer Typ ( `TypeA` ) deklariert und <xref:System.IDisposable.Dispose%2A> für das Feld nicht aufgerufen wird. `TypeB` entspricht `T` in der vorherigen Erörterung.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 <xref:System.IDisposable?displayProperty=fullName> [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
