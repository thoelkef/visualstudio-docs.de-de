---
title: 'CA1021: out-Parameter vermeiden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f62a88d8b3462d50b92cf2c7bcdf577ff736d19b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: out-Parameter vermeiden
|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ verfügt über eine `out` Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Die Übergabe von Typen als Verweis (mit `out` oder `ref`) erfordert Erfahrung mit Zeigern, Kenntnisse der Unterschiede zwischen Wert- und Verweistypen und Arbeiten mit Methoden mit mehreren Rückgabewerten. Außerdem ist der Unterschied zwischen `out` und `ref` Parameter wird nicht umfassend unterstützt.

 Wenn ein Verweistyp "nach Verweis" übergeben wird, will die Methode ab, den Parameter zu verwenden, um eine andere Instanz des Objekts zurückzugeben. Übergabe eines Verweistyps als Verweis wird auch als mithilfe eines Zeigers, double, Zeiger auf einen Zeiger oder eine doppelte Dereferenzierung bezeichnet. Unter Verwendung des standardmäßigen Aufrufkonvention "als Wert" übergeben wird, erhält ein Parameter, der bereits einen Verweistyp verwendet, einen Zeiger auf das Objekt. Der Zeiger nicht auf das Objekt, auf den er zeigt, wird als Wert übergeben. Übergeben Sie als Wert bedeutet, die die Methode den Zeiger, damit diese auf eine neue Instanz des Verweistyps nicht ändern kann. Allerdings können sie den Inhalt des Objekts ändern, auf den er zeigt. Für die meisten Anwendungen reicht es liefert das gewünschte Verhalten.

 Wenn eine Methode eine andere Instanz zurückgeben muss, verwenden Sie den Rückgabewert der Methode, um dies zu erreichen. Finden Sie unter der <xref:System.String?displayProperty=fullName> Klasse für eine Vielzahl von Methoden, mit denen Zeichenfolgen bearbeitet werden und eine neue Instanz einer Zeichenfolge zurückgeben. Wenn dieses Modell verwendet wird, muss der Aufrufer entscheiden, ob das ursprüngliche Objekt beibehalten wird.

 Obwohl Rückgabewerte inzwischen sind und oft verwendet, die richtige Anwendung der `out` und `ref` Parameter erfordert fortgeschrittene Entwurfs- und Fähigkeiten. Entwickler von Bibliotheken Entwurf für eine Breite Zielgruppe keine Benutzer master arbeiten mit erwarten soll `out` oder `ref` Parameter.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, die durch einen Werttyp verursacht wird, haben Sie die Methode das Objekt als Rückgabewert zurück. Wenn die Methode mehrere Werte zurückgeben muss, Umgestalten Sie, um eine einzelne Instanz eines Objekts zurückzugeben, die die Werte enthält.

 Um einen Verstoß gegen diese Regel zu beheben, die durch ein Verweistyp verursacht wird, stellen Sie sicher, dass das gewünschte Verhalten ist, um eine neue Instanz des Verweises zurückzugeben. Wenn dies der Fall, sollte die Methode den Rückgabewert verwenden, hierzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel. Dieser Entwurf konnte jedoch verwendungsproblemen verursachen.

## <a name="example"></a>Beispiel
 Die folgende Bibliothek zeigt zwei Implementierungen einer Klasse, die Antworten auf das Feedback von einem Benutzer generiert. Die erste Implementierung (`BadRefAndOut`) erzwingt, dass Benutzer der Bibliothek, drei Rückgabewerte zu verwalten. Die zweite Implementierung (`RedesignedRefAndOut`) vereinfacht die erforderlichen Erfahrungsgrad des Benutzers durch Rückgabe einer Instanz einer Container-Klasse (`ReplyData`), die die Daten als einzelne Einheit verwaltet.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung zeigt die Erfahrung des Benutzers. Der Aufruf der umgestalteten Bibliothek (`UseTheSimplifiedClass` Methode) ist einfacher, und die von der Methode zurückgegebene Informationen leicht verwaltet wird. Die Ausgabe der beiden Methoden ist identisch.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Beispiel
 Das folgende Beispielbibliothek wird veranschaulicht, wie `ref` Parameter für Verweistypen dienen und zeigt eine bessere Möglichkeit, diese Funktionalität zu implementieren.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung ruft jede Methode in der Bibliothek, um das Verhalten zeigen.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

 Folgende Ergebnisse werden zurückgegeben:

 **Changing-Zeiger - übergebener Wert:**
**12345**
**12345**
**Changing-Zeiger - Verweisübergabe:** 
 ** 12345**
**12345 ABCDE**
**übergeben als Rückgabewert:**
**12345 ABCDE**
## <a name="try-pattern-methods"></a>Wiederholen Sie den Mustermethoden

### <a name="description"></a>Beschreibung
 Methoden, implementieren die **versuchen\<etwas >** Steuerelementmuster, z. B. <xref:System.Int32.TryParse%2A?displayProperty=fullName>, keine dieser Verletzung auslösen. Das folgende Beispiel zeigt eine Struktur (Werttyp), implementiert die <xref:System.Int32.TryParse%2A?displayProperty=fullName> Methode.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1045: Typen nicht als Verweis übergeben](../code-quality/ca1045-do-not-pass-types-by-reference.md)