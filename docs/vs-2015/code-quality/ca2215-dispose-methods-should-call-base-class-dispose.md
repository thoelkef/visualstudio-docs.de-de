---
title: 'CA2215: die verwerfen-Methoden sollten die Basisklassen Freigabe abrufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4197c2faaf4aa23db930a9019538592326a84116
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534380"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ, der implementiert, <xref:System.IDisposable?displayProperty=fullName> erbt von einem Typ, der ebenfalls implementiert <xref:System.IDisposable> . Die- <xref:System.IDisposable.Dispose%2A> Methode des erbenden Typs ruft nicht die- <xref:System.IDisposable.Dispose%2A> Methode des übergeordneten Typs auf.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn ein Typ von einem verwerfbaren Typ erbt, muss er die- <xref:System.IDisposable.Dispose%2A> Methode des Basistyps in seiner eigenen- <xref:System.IDisposable.Dispose%2A> Methode abrufen. Durch das Aufrufen der Methode für den Basistyp wird sichergestellt, dass alle vom Basistyp erstellten Ressourcen freigegeben werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie an `base` .<xref:System.IDisposable.Dispose%2A> in der- <xref:System.IDisposable.Dispose%2A> Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn aufgerufen wird `base` .<xref:System.IDisposable.Dispose%2A> Tritt auf einer tieferen Aufruf Ebene auf als die Regel Überprüfungen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeA` , der implementiert <xref:System.IDisposable> .

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeB` , der vom-Typ erbt `TypeA` und seine-Methode ordnungsgemäß aufruft <xref:System.IDisposable.Dispose%2A> .

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Weitere Informationen
 <xref:System.IDisposable?displayProperty=fullName> [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
