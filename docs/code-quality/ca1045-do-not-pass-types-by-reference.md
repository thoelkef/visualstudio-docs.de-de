---
title: 'CA1045: Typen nicht als Verweis übergeben.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fd0da0f8b04055622b46087ecb9f12b375d9576
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922852"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Typen nicht als Verweis übergeben.

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine öffentliche oder geschützte Methode in einem öffentlichen Typ verfügt über `ref` einen Parameter, der einen primitiven Typ, einen Verweistyp oder einen Werttyp annimmt, bei dem es sich nicht um einen der integrierten Typen handelt.

## <a name="rule-description"></a>Regelbeschreibung
Die Übergabe von Typen als Verweis `out` ( `ref`mit oder) erfordert die Verwendung von Zeigern, das Verständnis der Unterschiede zwischen Werttypen und Verweis Typen sowie die Behandlung von Methoden mit mehreren Rückgabe Werten. Außerdem wird der Unterschied `out` zwischen `ref` -und-Parametern nicht häufig verstanden.

Wenn ein Verweistyp als Verweis übergeben wird, beabsichtigt die Methode, den-Parameter zu verwenden, um eine andere Instanz des Objekts zurückzugeben. (Die Übergabe eines Verweis Typs als Verweis wird auch als Verwendung eines doppelten Zeigers, Zeiger auf einen Zeiger oder doppelte Dereferenzierung bezeichnet.) Mit der Standard Aufruf Konvention, die als Wert übergeben wird, erhält ein Parameter, der einen Verweistyp annimmt, bereits einen Zeiger auf das Objekt. Der Zeiger, nicht das Objekt, auf das es verweist, wird als Wert übermittelt. Das übergeben nach Wert bedeutet, dass die Methode den Zeiger nicht ändern kann, damit Sie auf eine neue Instanz des Verweis Typs verweist, kann jedoch den Inhalt des Objekts ändern, auf das es verweist. Dies ist für die meisten Anwendungen ausreichend und liefert das gewünschte Verhalten.

Wenn eine Methode eine andere Instanz zurückgeben muss, verwenden Sie den Rückgabewert der-Methode, um dies zu erreichen. Eine Reihe <xref:System.String?displayProperty=fullName> von Methoden, die mit Zeichen folgen arbeiten und eine neue Instanz einer Zeichenfolge zurückgeben, finden Sie unter der-Klasse. Wenn dieses Modell verwendet wird, wird es dem Aufrufer überlassen, zu entscheiden, ob das ursprüngliche Objekt beibehalten wird.

Obwohl Rückgabewerte alltäglich und stark verwendet werden, sind für die korrekte `out` Anwendung `ref` von-und-Parametern zwischen Entwurfs-und Codierungs Fähigkeiten erforderlich. Bibliotheks Architekten, die für eine allgemeine Zielgruppe entwerfen, sollten nicht erwarten, dass `out` Benutzer `ref` die Arbeit mit-oder-Parametern meistern.

> [!NOTE]
> Wenn Sie mit Parametern arbeiten, die große Strukturen darstellen, können die zusätzlichen Ressourcen, die erforderlich sind, um diese Strukturen zu kopieren, beim übergeben nach Wert einen Leistungs Effekt verursachen. In diesen Fällen können Sie die Verwendung `ref` der Parameter oder `out` in Erwägung gezogen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, der durch einen Werttyp verursacht wird, lassen Sie die Methode das Objekt als Rückgabewert zurückgeben. Wenn die Methode mehrere Werte zurückgeben muss, entwerfen Sie Sie so um, dass eine einzelne Instanz eines Objekts zurückgegeben wird, das die Werte enthält.

Um einen Verstoß gegen diese Regel zu beheben, der durch einen Verweistyp verursacht wird, stellen Sie sicher, dass das gewünschte Verhalten eine neue Instanz des Verweises zurückgeben soll. Wenn dies der Fall ist, sollte die Methode ihren Rückgabewert verwenden, um dies zu tun.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Dieser Entwurf kann jedoch Probleme mit der Benutzerfreundlichkeit verursachen.

## <a name="example"></a>Beispiel
Die folgende Bibliothek zeigt zwei Implementierungen einer-Klasse, die Antworten auf das Feedback des Benutzers generiert. Die erste Implementierung (`BadRefAndOut`) zwingt den Bibliotheks Benutzer, drei Rückgabewerte zu verwalten. Die zweite Implementierung (`RedesignedRefAndOut`) vereinfacht die Benutzer Leistung durch die Rückgabe einer Instanz einer Container Klasse (`ReplyData`), die die Daten als einzelne Einheit verwaltet.

[!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>Beispiel
Die folgende Anwendung veranschaulicht die Benutzeroberflächen Darstellung. Der-Befehl für die neu gestaltete`UseTheSimplifiedClass` Bibliothek (-Methode) ist einfacher, und die von der-Methode zurückgegebenen Informationen können problemlos verwaltet werden. Die Ausgabe der beiden Methoden ist identisch.

[!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>Beispiel
Die folgende Beispiel Bibliothek veranschaulicht, `ref` wie Parameter für Verweis Typen verwendet werden, und zeigt eine bessere Möglichkeit, diese Funktionalität zu implementieren.

[!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>Beispiel
Die folgende Anwendung ruft jede Methode in der Bibliothek auf, um das Verhalten zu veranschaulichen.

[!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="related-rules"></a>Verwandte Regeln
[CA1021: Out-Parameter vermeiden](../code-quality/ca1021-avoid-out-parameters.md)