---
title: 'CA2115: GC.KeepAlive beim Verwenden systemeigener Ressourcen aufrufen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 66621bec3316dfcee92a1e5b1d1d1a8d97ae5c54
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914652"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: GC.KeepAlive beim Verwenden systemeigener Ressourcen aufrufen
|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode deklariert wird, in einem Typ mit einem Finalizer verweist auf eine <xref:System.IntPtr?displayProperty=fullName> oder <xref:System.UIntPtr?displayProperty=fullName> Feld jedoch nicht aufgerufen, <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 Garbagecollection schließt ein Objekt ab, wenn es keine weiteren Verweise darauf in verwaltetem Code sind. Nicht verwaltete Verweise auf Objekte sind keine Garbagecollection verhindern. Diese Regel erkennt Fehler, die auftreten können, wenn eine nicht verwaltete Ressource freigegeben wird, während sie in nicht verwaltetem Code noch verwendet wird.

 Diese Regel setzt voraus, dass <xref:System.IntPtr> und <xref:System.UIntPtr> Felder Speichern von Zeigern auf nicht verwalteten Ressourcen. Da der Zweck eines Finalizers nicht verwaltete Ressourcen freizugeben ist, wird die Regel davon ausgegangen, dass der Finalizer, die nicht verwaltete Ressource verweist, die Zeiger Felder frei wird zu. Mit dieser Regel wird davon ausgegangen, dass die Methode die Zeigerfeld verweist um nicht verwaltete Ressource an nicht verwalteten Code übergeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen Aufruf von <xref:System.GC.KeepAlive%2A> übergeben Sie an die Methode die aktuelle Instanz (`this` in c# und C++) als Argument. Positionieren Sie den Aufruf nach der letzten Zeile des Codes, in dem das Objekt von der Garbagecollection geschützt werden muss. Unmittelbar nach dem Aufruf von <xref:System.GC.KeepAlive%2A>, das Objekt wird erneut als bereit für die Garbagecollection betrachtet, vorausgesetzt, dass keine verwalteten Verweise darauf vorhanden sind.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Regel stellt einige Annahmen, die zu falsch positiven Ergebnisse führen können. Sie können eine Warnung dieser Regel gefahrlos unterdrücken, wenn:

-   Der Finalizer ist nicht frei, den Inhalt der <xref:System.IntPtr> oder <xref:System.UIntPtr> Feld verwiesen wird, von der Methode.

-   Die Methode übergibt keine der <xref:System.IntPtr> oder <xref:System.UIntPtr> Feld zu nicht verwaltetem Code.

 Überprüfen Sie sorgfältig andere Nachrichten, bevor diese ausgeschlossen werden. Diese Regel erkennt Fehler, die schwer zu reproduzieren und zu debuggen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel `BadMethod` enthält keinen Aufruf von `GC.KeepAlive` und verletzt daher die Regel. `GoodMethod` enthält den korrigierten Code.

> [!NOTE]
>  In diesem Beispiel ist Pseudocode, obwohl der Code kompiliert und ausgeführt wird, die die Warnung wird nicht ausgelöst, da eine nicht verwaltete Ressource nicht erstellt oder freigegeben wird.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Siehe auch
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName> <xref:System.Object.Finalize%2A?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName> [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)