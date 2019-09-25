---
title: 'CA2115: GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: eb6d28e15870907034479e698ba8e7464f4f5159
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232725"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methode <xref:System.IntPtr?displayProperty=fullName> ,die<xref:System.UIntPtr?displayProperty=fullName> in einem Typ mit einem Finalizer deklariert ist, verweist auf ein-Feld oder ein-Feld, aber nicht. <xref:System.GC.KeepAlive%2A?displayProperty=fullName>

## <a name="rule-description"></a>Regelbeschreibung

Durch die Garbage Collection wird ein Objekt beendet, wenn in verwaltetem Code keine weiteren Verweise darauf vorhanden sind. Nicht verwaltete Verweise auf Objekte verhindern Garbage Collection. Diese Regel erkennt Fehler, die auftreten können, wenn eine nicht verwaltete Ressource freigegeben wird, während sie in nicht verwaltetem Code noch verwendet wird.

Diese Regel setzt voraus <xref:System.IntPtr> , <xref:System.UIntPtr> dass die Felder und Zeiger auf nicht verwaltete Ressourcen speichern. Da der Zweck eines Finalizers darin besteht, nicht verwaltete Ressourcen freizugeben, geht die Regel davon aus, dass der Finalizer die nicht verwaltete Ressource freigibt, auf die von den Zeiger Feldern verwiesen wird. Diese Regel setzt auch voraus, dass die-Methode auf das Zeiger Feld verweist, um die nicht verwaltete Ressource an nicht verwalteten Code zu übergeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der <xref:System.GC.KeepAlive%2A> -Methode einen-Rückruf hinzu, und übergeben Sie C# dabei C++die aktuelle-Instanz (`this` in und) als-Argument. Positionieren Sie den-Befehl nach der letzten Codezeile, in der das Objekt vor Garbage Collection geschützt werden muss. Unmittelbar nach dem-Aufrufvorgang <xref:System.GC.KeepAlive%2A>wird das Objekt erneut als bereit für Garbage Collection betrachtet, vorausgesetzt, dass keine verwalteten Verweise vorhanden sind.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Diese Regel trifft auf einige Annahmen zu, die zu falsch positiven Ergebnissen führen können. Sie können eine Warnung aus dieser Regel sicher unterdrücken, wenn Folgendes gilt:

- Der Finalizer gibt den Inhalt des <xref:System.IntPtr> -Felds oder <xref:System.UIntPtr> des-Felds, auf das die-Methode verweist, nicht frei.

- Die-Methode übergibt das- <xref:System.IntPtr> Feld <xref:System.UIntPtr> oder das-Feld nicht an nicht verwalteten Code.

Überprüfen Sie andere Meldungen sorgfältig, bevor Sie Sie ausschließen. Diese Regel erkennt Fehler, die schwer zu reproduzieren und zu Debuggen sind.

## <a name="example"></a>Beispiel

Im folgenden Beispiel `BadMethod` enthält keinen-Rückruf und verstößt daher gegen `GC.KeepAlive` die Regel. `GoodMethod`enthält den korrigierten Code.

> [!NOTE]
> Bei diesem Beispiel handelt es sich um Pseudo Code. Obwohl der Code kompiliert und ausgeführt wird, wird die Warnung nicht ausgelöst, weil keine nicht verwaltete Ressource erstellt oder freigegeben wird.

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)