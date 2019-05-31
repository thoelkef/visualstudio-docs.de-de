---
title: 'CA1045: Typen nicht als Verweis übergeben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6bbdcb2e2ac8f905a2b52cfb41ed90217d215b4b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431541"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Typen nicht als Verweis übergeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ hat einen `ref` Parameter, der ein primitiver Typ, ein Verweistyp oder ein Werttyp ist, akzeptiert ist keiner der integrierten Typen.

## <a name="rule-description"></a>Regelbeschreibung
 Übergabe von Typen als Verweis (mit `out` oder `ref`) erfordert Erfahrung mit Zeigern, Kenntnisse der Unterschiede zwischen Werttypen und Verweistypen und Umgang mit Methoden, die Rückgabe mehrerer Werte aufweisen. Außerdem ist der Unterschied zwischen `out` und `ref` Parameter kann häufig nicht interpretiert werden.

 Wenn ein Verweistyp "by Reference" übergeben wird, soll die Methode ab, den Parameter zu verwenden, um eine andere Instanz des Objekts zurückzugeben. (Übergabe eines Verweistyps als Verweis wird auch bezeichnet als mithilfe eines Zeigers, double, Zeiger auf einen Zeiger oder doppelte Dereferenzierung.) Verwenden die Standardaufrufkonvention, die "als Wert" übergeben wird, erhält ein Parameter, der einen Verweistyp bereits akzeptiert einen Zeiger auf das Objekt. Der Zeiger ist, nicht auf das Objekt aus, die auf den er verweist, wird als Wert übergeben. Übergabe nach Wert bedeutet, die die Methode den Zeiger, damit diese auf eine neue Instanz des Verweises nicht ändern kann geben, aber können ändern, den Inhalt des Objekts auf den er verweist. Für die meisten Anwendungen müssen dies ist ausreichend, und liefert das gewünschte Verhalten.

 Wenn eine Methode eine andere Instanz zurückgeben muss, verwenden Sie der Rückgabewert der Methode, um dies zu erreichen. Finden Sie unter den <xref:System.String?displayProperty=fullName> -Klasse für eine Vielzahl von Methoden, die für Zeichenfolgen verwendet werden, und geben Sie eine neue Instanz einer Zeichenfolge zurück. Mithilfe des Modells, bleibt es an den Aufrufer, um zu entscheiden, ob das ursprüngliche Objekt beibehalten wird.

 Zwar sind in aller Munde und häufig verwendet, die richtige Anwendung der Rückgabewerte `out` und `ref` Parameter erfordert, mittlere Design- und Fertigkeiten im coding. Entwurf für eine Breite Zielgruppe master arbeiten mit Benutzern nicht erwarten sollten Entwickler von Bibliotheken `out` oder `ref` Parameter.

> [!NOTE]
> Bei der Arbeit mit Parametern, die große Strukturen sind, können die zusätzlichen Ressourcen, die erforderlich sind, zum Kopieren dieser Strukturen eine Auswirkung auf die Leistung führen, wenn Sie nach Wert übergeben. In diesen Fällen verwenden Sie ggf. `ref` oder `out` Parameter.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, die von einem Werttyp verursacht wird, müssen Sie die Methode, die das Objekt als ihren Rückgabewert zurück. Wenn die Methode mehrere Werte zurückgeben muss, Umgestalten Sie, um eine einzelne Instanz eines Objekts zurück, der die Werte enthält.

 Um einen Verstoß gegen diese Regel zu beheben, die von einem Verweistyp verursacht wird, stellen Sie sicher, dass das gewünschte Verhalten ist, um eine neue Instanz des Verweises zurückzugeben. Wenn es sich handelt, sollte die Methode den Rückgabewert verwenden, hierzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher ist, unterdrücken Sie eine Warnung dieser Regel. Dieser Entwurf könnte jedoch Probleme hinsichtlich der Verwendbarkeit führen.

## <a name="example"></a>Beispiel
 Die folgende Bibliotheken zeigt zwei Implementierungen einer Klasse, die Antworten auf das Feedback des Benutzers generiert. Die erste Implementierung (`BadRefAndOut`) erzwingt, dass Benutzer der Bibliothek, die drei Rückgabewerte zu verwalten. Die zweite Implementierung (`RedesignedRefAndOut`) vereinfacht die benutzererfahrung durch Rückgabe einer Instanz einer Container-Klasse (`ReplyData`), die die Daten als einzelne Einheit verwaltet.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung zeigt die Erfahrung des Benutzers. Der Aufruf der umgestalteten Bibliothek (`UseTheSimplifiedClass` Methode) ist einfacher, und die Informationen, die von der Methode zurückgegeben wird, ist einfach verwaltet. Die Ausgabe der beiden Methoden ist identisch.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Beispielbibliothek wird veranschaulicht, wie `ref` Parameter für Verweistypen werden verwendet, und zeigt eine bessere Möglichkeit, die diese Funktionalität zu implementieren.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung ruft jede Methode in der Bibliothek, um das Verhalten zu veranschaulichen.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Changing-Zeiger - nach Wert übergeben:** 
**12345**
**12345**
**ändern – als Verweis übergebenen Zeiger:** 
**12345**
**12345 ABCDE**
**Übergabe nach Wert zurückgibt:** 
**12345 ABCDE**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1021: Out-Parameter vermeiden](../code-quality/ca1021-avoid-out-parameters.md)
