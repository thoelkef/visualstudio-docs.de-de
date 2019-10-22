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
ms.openlocfilehash: 89f3705169fb9d28a1ec773671d460f00b98d892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662850"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ, der <xref:System.IDisposable?displayProperty=fullName> implementiert, erbt von einem Typ, der auch <xref:System.IDisposable> implementiert. Die <xref:System.IDisposable.Dispose%2A>-Methode des erbenden Typs ruft nicht die <xref:System.IDisposable.Dispose%2A>-Methode des übergeordneten Typs auf.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn ein Typ von einem verwerfbaren Typ erbt, muss er die <xref:System.IDisposable.Dispose%2A>-Methode des Basistyps innerhalb seiner eigenen <xref:System.IDisposable.Dispose%2A> Methode abrufen. Durch das Aufrufen der Methode für den Basistyp wird sichergestellt, dass alle vom Basistyp erstellten Ressourcen freigegeben werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie `base` an. <xref:System.IDisposable.Dispose%2A> in ihrer <xref:System.IDisposable.Dispose%2A>-Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der `base` aufgerufen wird. <xref:System.IDisposable.Dispose%2A> Tritt auf einer tieferen Aufruf Ebene auf als die Regel Überprüfungen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeA`, der <xref:System.IDisposable> implementiert.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `TypeB`, der vom Typ `TypeA` erbt und seine <xref:System.IDisposable.Dispose%2A>-Methode ordnungsgemäß aufruft.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.IDisposable?displayProperty=fullName> Lösch [Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
