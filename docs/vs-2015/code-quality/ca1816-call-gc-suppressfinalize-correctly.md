---
title: 'CA1816: Rufen Sie GC. SuppressFinalize ordnungsgemäß | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 031003e4989e6018a250045f5fa8550a7ec2033a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683020"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize korrekt aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategorie|Microsoft. Verwendung|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

- Eine Methode, die eine Implementierung von <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ruft nicht <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Eine Methode, die keine Implementierung des ist <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Aufrufe <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Ruft eine Methode <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> und übergibt ein anderes Element als dieses (Me in Visual Basic).

## <a name="rule-description"></a>Regelbeschreibung
 Die <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Methode ermöglicht Benutzern das Freigeben von Ressourcen zu einem beliebigen Zeitpunkt vor dem Objekt, das die aufgabenausführung verfügbar sind, für die Garbagecollection. Wenn die <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> -Methode aufgerufen wird, gibt das Objekt die Ressourcen frei. Dadurch wird die Beendigung nicht erforderlich. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> sollten Aufrufen <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> , damit der Garbage Collector den Finalizer des Objekts nicht aufgerufen wird.

 Um zu verhindern, dass abgeleitet, dass Typen mit Finalizern müssen erneut implementieren [System.IDisposable])<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) und für den Aufruf, unversiegelte Typen ohne Finalizer sollten dennoch aufrufen <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben:

 Wenn die Methode eine Implementierung von <xref:System.IDisposable.Dispose%2A>, fügen Sie einen Aufruf von <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Wenn die Methode keine Implementierung von <xref:System.IDisposable.Dispose%2A>, entfernen Sie den Aufruf von <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> oder verschieben Sie ihn in des Typs des <xref:System.IDisposable.Dispose%2A> Implementierung.

 Ändern Sie alle Aufrufe von <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> dieses (Me in Visual Basic) übergeben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie nur eine Warnung dieser Regel auf, wenn Sie verwenden möchten <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> zur Steuerung der Lebensdauer von anderen Objekten. Unterdrücken Sie eine Warnung dieser Regel nicht, wenn eine Implementierung von <xref:System.IDisposable.Dispose%2A> ruft nicht <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. In diesem Fall wird die Leistung beeinträchtigt und keine Vorteile ergeben Abschluss nicht unterdrückt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die falsch Aufrufe <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die ordnungsgemäß Aufrufe <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2215: Dispose-Methoden müssen die Dispose der Basisklasse aufrufen.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Siehe auch
 [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
