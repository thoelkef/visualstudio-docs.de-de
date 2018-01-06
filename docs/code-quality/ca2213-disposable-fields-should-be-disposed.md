---
title: 'CA2213: Verwerfbare Felder verwerfen sollten verworfen werden. | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4da3299e839be08a5ff11792aa2c80a364349b18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Verwerfbare Felder verwerfen
|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein Typ, der implementiert <xref:System.IDisposable?displayProperty=fullName> deklariert Felder von Typen, die ebenfalls implementieren <xref:System.IDisposable>. Die <xref:System.IDisposable.Dispose%2A> -Methode des Felds wird nicht aufgerufen, indem Sie die <xref:System.IDisposable.Dispose%2A> Methode des deklarierenden Typs.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein Typ ist verantwortlich für alle nicht verwalteten Ressourcen freigibt; Dies erfolgt durch Implementierung <xref:System.IDisposable>. Diese Regel überprüft, ob ein Typ `T` deklariert ein Feld `F` d. h. eine Instanz von einem Typ `FT`. Für jedes Feld `F`, versucht die Regel, einen Aufruf von `FT.Dispose`. Die Regel durchsucht, die vom aufgerufenen Methoden `T.Dispose`, und die Ebene darunter (die durch die vom aufgerufenen Methoden aufgerufenen Methoden `FT.Dispose`).  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen <xref:System.IDisposable.Dispose%2A> auf Felder von Typen, die implementieren <xref:System.IDisposable> , wenn Sie verantwortlich für die Zuordnung sind und Freigabe der nicht verwalteten Ressourcen frei, die durch das Feld.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können zum Unterdrücken einer Warnung dieser Regel, wenn Sie nicht zuständig sind, für die Ressource freigegeben, die nach dem Feld aufrechterhalten oder ruhig der Aufruf von <xref:System.IDisposable.Dispose%2A> tritt auf, genauer gesagt aufrufenden als die Regel überprüft.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ `TypeA` implementiert <xref:System.IDisposable> (`FT` im vorherigen Beispiel).  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ `TypeB` gegen diese Regel, indem Sie ein Feld deklarieren `aFieldOfADisposableType` (`F` im vorherigen Beispiel) als einem Typ (`TypeA`) und nicht aufrufen <xref:System.IDisposable.Dispose%2A> auf das Feld. `TypeB`entspricht `T` im vorherigen Beispiel.  
  
 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)