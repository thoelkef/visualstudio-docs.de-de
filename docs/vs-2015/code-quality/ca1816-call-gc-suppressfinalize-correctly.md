---
title: 'CA1816: GC abrufen. Ordnungsgemäße SuppressFinalize | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: acc86c278faa877897d294e72632762eff834a76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668382"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize korrekt aufrufen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Callgcsuppressfinalizecorrectly|
|CheckId|CA1816|
|Kategorie|Microsoft. Verwendung|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

- Eine Methode, bei der es sich um eine Implementierung von handelt, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> keine <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufruft.

- Eine Methode, bei der es sich nicht um eine Implementierung von handelt, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufruft.

- Eine Methode ruft <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> auf und übergibt etwas anderes als This (mich in Visual Basic).

## <a name="rule-description"></a>Regelbeschreibung
 Die <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>-Methode ermöglicht Benutzern das Freigeben von Ressourcen zu einem beliebigen Zeitpunkt, bevor das Objekt für Garbage Collection verfügbar wird. Wenn die <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>-Methode aufgerufen wird, gibt Sie Ressourcen des-Objekts frei. Dies macht die Finalisierung unnötig. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> sollte <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufgerufen werden, damit der Garbage Collector den Finalizer des Objekts nicht aufruft.

 So verhindern Sie, dass abgeleitete Typen mit Finalizern [System. iverwerf] erneut implementieren müssen (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) und um es aufzurufen, sollten nicht versiegelte Typen ohne Finalizer weiterhin <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufgerufen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 So beheben Sie einen Verstoß gegen diese Regel:

 Wenn die Methode eine Implementierung von <xref:System.IDisposable.Dispose%2A> ist, fügen Sie <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> einen aufzurufenden hinzu.

 Wenn es sich bei der Methode nicht um eine Implementierung von <xref:System.IDisposable.Dispose%2A> handelt, entfernen Sie entweder den aufzurufenden <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, oder verschieben Sie ihn in die <xref:System.IDisposable.Dispose%2A> Implementierung des Typs.

 Ändern Sie alle Aufrufe von <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, um dies (ich in Visual Basic) zu übergeben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie nur eine Warnung aus dieser Regel, wenn Sie die Verwendung von <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> zum Steuern der Lebensdauer anderer Objekte über. Unterdrücken Sie keine Warnung aus dieser Regel, wenn eine Implementierung von <xref:System.IDisposable.Dispose%2A> keinen <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufruft. In dieser Situation wird die Leistung durch einen Fehler beim unterdrücken der Finalisierung beeinträchtigt, und es werden keine Vorteile geboten.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> fälschlicherweise aufruft.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ordnungsgemäß aufruft.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Siehe auch
 [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
