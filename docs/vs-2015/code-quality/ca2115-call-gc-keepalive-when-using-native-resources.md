---
title: 'CA2115: GC abrufen. KeepAlive bei Verwendung von nativen Ressourcen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c668172ca318000068fb4e90f4848e456c32208d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543623"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: GC.KeepAlive beim Verwenden nativer Ressourcen aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode, die in einem Typ mit einem Finalizer deklariert ist, verweist auf ein- <xref:System.IntPtr?displayProperty=fullName> Feld oder ein- <xref:System.UIntPtr?displayProperty=fullName> Feld, aber nicht <xref:System.GC.KeepAlive%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 Durch die Garbage Collection wird ein Objekt beendet, wenn in verwaltetem Code keine weiteren Verweise darauf vorhanden sind. Nicht verwaltete Verweise auf Objekte verhindern Garbage Collection. Diese Regel erkennt Fehler, die auftreten können, wenn eine nicht verwaltete Ressource freigegeben wird, während sie in nicht verwaltetem Code noch verwendet wird.

 Diese Regel setzt voraus, dass die <xref:System.IntPtr> <xref:System.UIntPtr> Felder und Zeiger auf nicht verwaltete Ressourcen speichern. Da der Zweck eines Finalizers darin besteht, nicht verwaltete Ressourcen freizugeben, geht die Regel davon aus, dass der Finalizer die nicht verwaltete Ressource freigibt, auf die von den Zeiger Feldern verwiesen wird. Diese Regel setzt auch voraus, dass die-Methode auf das Zeiger Feld verweist, um die nicht verwaltete Ressource an nicht verwalteten Code zu übergeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der-Methode einen-Rückruf hinzu <xref:System.GC.KeepAlive%2A> , und übergeben Sie dabei die aktuelle Instanz ( `this` in c# und C++) als Argument. Positionieren Sie den-Befehl nach der letzten Codezeile, in der das Objekt vor Garbage Collection geschützt werden muss. Unmittelbar nach dem-Aufrufvorgang <xref:System.GC.KeepAlive%2A> wird das Objekt erneut als bereit für Garbage Collection betrachtet, vorausgesetzt, dass keine verwalteten Verweise vorhanden sind.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Regel trifft auf einige Annahmen zu, die zu falsch positiven Ergebnissen führen können. Sie können eine Warnung aus dieser Regel sicher unterdrücken, wenn Folgendes gilt:

- Der Finalizer gibt den Inhalt des- <xref:System.IntPtr> Felds oder des- <xref:System.UIntPtr> Felds, auf das die-Methode verweist, nicht frei.

- Die-Methode übergibt das- <xref:System.IntPtr> Feld oder das- <xref:System.UIntPtr> Feld nicht an nicht verwalteten Code.

  Überprüfen Sie andere Meldungen sorgfältig, bevor Sie Sie ausschließen. Diese Regel erkennt Fehler, die schwer zu reproduzieren und zu Debuggen sind.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel enthält keinen `BadMethod` `GC.KeepAlive` -Rückruf und verstößt daher gegen die Regel. `GoodMethod`enthält den korrigierten Code.

> [!NOTE]
> Bei diesem Beispiel handelt es sich um Pseudo Code, obwohl der Code kompiliert und ausgeführt wird, wird die Warnung nicht ausgelöst, da eine nicht verwaltete Ressource nicht erstellt oder freigegeben wird.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
