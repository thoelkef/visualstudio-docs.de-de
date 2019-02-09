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
ms.openlocfilehash: 9a74f6313f90a31d43cf39443b1c44d78f0628f8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930986"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Methode deklariert werden, in einem Typ mit einem Finalizer verweist auf eine <xref:System.IntPtr?displayProperty=fullName> oder <xref:System.UIntPtr?displayProperty=fullName> Feld, jedoch nicht auf <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung

Die automatische speicherbereinigung schließt ein Objekt ab, wenn es keine weiteren Verweise auf die sie in verwaltetem Code gibt. Nicht verwaltete Verweise auf Objekte sind keine Garbagecollection verhindern. Diese Regel erkennt Fehler, die auftreten können, wenn eine nicht verwaltete Ressource freigegeben wird, während sie in nicht verwaltetem Code noch verwendet wird.

Mit dieser Regel wird vorausgesetzt, dass <xref:System.IntPtr> und <xref:System.UIntPtr> Felder Speichern von Zeigern in nicht verwalteten Ressourcen. Da der Zweck eines Finalizers dient, die nicht verwaltete Ressourcen freizugeben, wird die Regel davon ausgegangen, dass der Finalizer die nicht verwaltete Ressource zeigt die Felder der Zeiger freigegeben wird. Mit dieser Regel wird davon ausgegangen, dass die Methode das Zeigerfeld verweist, um die nicht verwaltete Ressource zu nicht verwaltetem Code übergeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen Aufruf von <xref:System.GC.KeepAlive%2A> an die Methode übergeben Sie die aktuelle Instanz (`this` in c# und C++) als Argument. Positionieren Sie den Aufruf nach der letzten Zeile des Codes, in dem das Objekt muss vor der Garbagecollection geschützt werden. Unmittelbar nach dem Aufruf von <xref:System.GC.KeepAlive%2A>, das Objekt wird wieder als bereit für die Garbagecollection betrachtet, vorausgesetzt, es keine verwalteten Verweise darauf gibt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Diese Regel stellt einige Annahmen, die um falsch positive Ergebnisse führen können. Sie können problemlos eine Warnung dieser Regel unterdrücken, wenn:

- Der Finalizer ist nicht frei, den Inhalt der <xref:System.IntPtr> oder <xref:System.UIntPtr> Feld, das durch die Methode.

- Die-Methode übergibt die nicht die <xref:System.IntPtr> oder <xref:System.UIntPtr> Feld zu nicht verwaltetem Code.

Überprüfen Sie sorgfältig die anderen Nachrichten vor dem schließt sie. Diese Regel erkennt Fehler, die schwer zu reproduzieren und zu debuggen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel `BadMethod` enthält keinen Aufruf von `GC.KeepAlive` und verletzt daher die Regel. `GoodMethod` enthält den korrigierten Code.

> [!NOTE]
> In diesem Beispiel ist Pseudocode. Obwohl der Code kompiliert und ausgeführt wird, wird die Warnung nicht ausgelöst, da eine nicht verwaltete Ressource nicht erstellt oder freigegeben wird.

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)